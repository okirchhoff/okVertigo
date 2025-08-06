# Advanced Dolly-Zoom (Vertigo Effect) Tool for Maya

A professional-grade MEL script for Autodesk Maya that creates a hotkey-driven tool for performing a smooth, mathematically precise dolly-zoom or "Vertigo" effect, inspired by the famous shot from Alfred Hitchcock's film.

This tool allows an artist to temporarily enter a mode where dragging the mouse dollys the camera while simultaneously adjusting its focal length. This is calculated perfectly to ensure a subject in the frame remains the same size, while the background perspective appears to expand or compress dramatically.

![Vertigo Effect Demo](https://imgur.com/a/kwa124o)

## Key Features

This script has been engineered to be more than a simple proof-of-concept. It includes several advanced features that make it a robust and production-ready tool:

*   **Perfect Screen-Space Lock:** Utilizes a precise trigonometric calculation based on the camera's `focalLength` and `horizontalFilmAperture`. This ensures the subject remains perfectly locked in its screen position with **zero sliding**, even at extreme wide-angle focal lengths.

*   **Intelligent Targeting System:** The tool automatically determines the focal point based on your selection:
    *   **Multiple Objects:** Focuses on the center of the combined bounding box.
    *   **Single Object:** Focuses on the object's pivot point.
    *   **No Selection:** Focuses on the camera's current world-space point of interest.

*   **Smooth & Responsive Control:** Uses an absolute drag calculation to create a direct, 1:1 connection between your mouse movement and the dolly-zoom effect. This eliminates the lag or "catch-up" feeling found in simpler relative-based scripts.

*   **Seamless Hotkey Workflow:** Activate the tool by simply pressing and holding a hotkey. Releasing the key automatically deactivates the tool and returns you to your previous context (e.g., Move Tool, Select Tool, etc.), ensuring a fluid workflow.

## Installation

Setting up the tool takes just a few minutes.

1.  **Download the Script:**
    Download the `okVertigo.mel` script file from this repository.

2.  **Place the Script in your Maya Directory:**
    Place the `.mel` file into your Maya scripts directory. The default location is:
    *   **Windows:** `C:\Users\YourUserName\Documents\maya\scripts`
    *   **macOS:** `/Users/YourUserName/Library/Preferences/Autodesk/maya/scripts`
    *   **Linux:** `~/maya/scripts`

3.  **Set Up the Hotkeys in Maya:**
    *   Launch or restart Maya. The script's procedures will now be available.
    *   Open the Hotkey Editor by going to `Windows > Settings/Preferences > Hotkey Editor`.
    *   In the editor, it is best to use the **Custom Scripts** section to create your hotkey commands.
    *   **Press Action:**
        *   Find an empty hotkey and assign a **Press** command.
        *   In the `Command` text area, enter:
          ```mel
          vertigoToolActivate();
          ```
    *   **Release Action:**
        *   Assign the **exact same hotkey** to a **Release** command.
        *   In the `Command` text area, enter:
          ```mel
          vertigoToolDeactivate();
          ```
    *   Save your hotkeys.

![Hotkey Editor Setup](https://imgur.com/a/Oqbk7TH)

## How to Use

The tool is designed to be simple and intuitive.

1.  In a viewport, frame your shot.
2.  **Select an object** to be the focal point. Alternatively, select multiple objects or nothing at all to use the intelligent targeting.
3.  **Press and hold** your assigned hotkey.
4.  **Right-click and drag horizontally** in the viewport.
    *   Dragging right will typically dolly in and zoom out.
    *   Dragging left will dolly out and zoom in.
5.  Release the hotkey to return to your previous tool.

## Customization

You can easily adjust the tool's sensitivity.

Inside the `vertigoDrag()` procedure within the `.mel` script file, you will find the `$sensitivity` variable:

```mel
// SENSITIVITY CONTROL
float $sensitivity = 0.04;
