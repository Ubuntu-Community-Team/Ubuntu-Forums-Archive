---
title: "Mark minimized windows in &quot;Show applications&quot; grid"
date: 2024-05-01
forum: Desktop Environments
---

### Post by -Woodrow- on 2024-05-01
When I open the "Show applications" or "Activities" grid it shows me all currently opened windows.

However, which ones are **minimized** cannot be distinguished from the others. If they were marked with an icon, or grouped (minimized vs. unminimized), or sized smaller, that would be a great help to focus on any given current task. Having to search for a window is the worst.

Is there a way to achieve that? Maybe via an extension? — If not, then consider this a suggestion.

**About:**
OS: Ubuntu 22.04.4 LTS
GNOME version: 42.9
Windowing System: Wayland

---

### Post by vanadium on 2024-05-02
That is a very valid remark. In Gnome Shell, minimizing is not a first class citizen. Actually, windows are not minimized - there is nothing where they minimize to. They are "hidden"  from the desktop. To keep track of less windows on the current desktop, you are rather supposed to move windows you do not want to deal with to a different desktop.

I very much agree with you that this entails mental overhead:

- Either you use the shortcut key Super+Shift+PgDn to move that window to another workspace, but that takes you along with the window to the other desktop instead of getting rid of the window. You first need to return back. In addition, something else may be going on on that other desktop, so "hiding"  windows there disrupts that desktop.

- Alternatively, you are supposed to go to the overview, then drag the window to another workspace. Also here, instead of quickly getting rid of the window, you are taken out of your context to the overview, with the mental overhead to scan for the window you want to move (it is not automatically selected), then move it using the mouse.

- The quick way, hitting Super+H to hide it, has the drawback you mention if you use the overview to navigate to different windows. It would be good if hidden windows would also be hidden in the overview: they are present on the dock (Dash in stock gnome) after all.

I agree that this is poorly designed. Personally, it does not bother me much: I run applications mostly maximized, use the traditional Alt+Tab for window switching and a launcher (the excellent Gnome Shell extension "Switcher") to launch applications: workflows that do not take you entirely out of the context.

That said, a quick search to me revealed the extension [Hide Minimized](https://extensions.gnome.org/extension/2639/hide-minimized/)

---

### Post by tea for one on 2024-05-02
> **-Woodrow- said:**
> Maybe via an extension?
This extension [https://github.com/home-sweet-gnome/dash-to-panel](https://github.com/home-sweet-gnome/dash-to-panel) shows minimised and open applications (via running indicators)
The open applications will appear in "Show Applications" and the minimised apps will display an indicator.
May be worth a look?

---

