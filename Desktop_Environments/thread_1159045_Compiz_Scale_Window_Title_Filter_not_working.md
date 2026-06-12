---
title: "Compiz Scale Window Title Filter not working"
date: 2009-05-14
forum: Desktop Environments
---

### Post by forejtv on 2009-05-14
I use Compiz Scale plugin on my laptop together with Scale Window Title Filter. However, in 9.04 I'm unable to get the title filter to work (it worked on 8.04). When I activate the Scale plugin and press a key, in 9 of 10 cases nothing happens. Sometimes, one key press is recognized and plugin shows the windows with the titles containing the one character, but then it stops recognizing other key inputs (except the one that turns off the Scale mode :-)).

Everything else works fine, I can use the Scale filter without problems, it neither crashes nor works slowly. It seems that just the Scale Window Title Filter plugin is corrupted. I have tried to load a Compiz configuration file from a computer on which the plugin works smoothly, but it didn't solve the problem.

Thanks for any help.

---

### Post by cefn on 2009-09-03
I confirm the same non-functional plugin on my Jaunty based Mint desktop. Holding down my keyboard combo for scale triggers scale fine, but there's no keyboard input I can find which triggers filtering.

---

### Post by ashcroft3000 on 2009-09-05
Problems over here, too! Actually, the Window Title Filter has disappeared from CCSM. I could swear that I've still seen it there just the other day and that I've been using it w/o problems before (running Jaunty since April). I don't remembering uninstalling it, wouldn't even know how...

---

### Post by eclecticos on 2009-12-16
Confirming the problem on my Mint 8 desktop (based on Ubuntu 9.10 Karmic), which otherwise runs compiz perfectly.

Note: I was able to use Scale Window Title Filter successfully a year ago with Mint 6 (based on Ubuntu 9.8 Intrepid).  Actually, I don't think it worked if I activated Scale with the keyboard, because then I was already holding down Ctrl-Alt-up, which presumably interfered with anything else I tried to type.  But the title filter did work great in Mint 6 if I first activated Scale by moving the mouse to a certain corner of the screen (having configured that to activate Scale).The title filter no longer works at all in Mint 8.

Side remark: It's a pity that Gnome Do doesn't let you call up your windows by title, for an all-keyboard solution to jumping to your desired window.  But perhaps it's challenging to get Gnome Do to talk to the window manager.   

Side remark: And it's a true pity that compiz has no plugin that allows you to define single dedicated keystrokes for "Find and focus my (next) emacs window," "Find and focus my (next) firefox window," etc.  Where a "firefox window" would be defined as one with "firefox" in the title, or possibly in the process name.  Seems relatively simple to add.

Question: By the way, is there any way to get Scale or other compiz window-choosers to offer you minimized windows, too?  Sometimes the window I'm looking for turns out to be minimized.

---

### Post by stinkeye on 2009-12-16
> **eclecticos said:**
> 

Question: By the way, is there any way to get Scale or other compiz window-choosers to offer you minimized windows, too?  Sometimes the window I'm looking for turns out to be minimized.
I picked up this python script by Greg Till from another post... can't find it at the moment to link to
but here's the script
```
#!/usr/bin/env python

# Written by Greg Till
# November 2008
# Public domain software

from __future__ import division
import gtk
import os
import wnck
import time

"""scale.py: Unminimizes and re-minimizes windows for Compiz's Scale plugin

More specifically:

- Unminimize all minimized viewport windows 
- Launch the Scale plugin of the Compiz window manager
- Re-minimize previously minimized windows (other than any newly activated
    window and windows closed through Scale)

In this script, you may customize the 'pluginDelay' variable. This variable
    refers to the duration between when Scale activates and when you may
    select a window using Scale. In rare instances, windows may spontaneously
    become active after they have been unminimized and after Scale has started,
    but before you have selected a window in Scale. A change in window status
    will trigger the reminimization process. By setting a short delay after
    Scale begins, these rare active window changes will be caught and ignored.
    Each such active window change will reset the time. Typically, it can be a
    small number (a fraction of a second) and is needed, if at all, only when
    the system is working under heavy load.
    
Scale can show the windows in the current viewport or all viewports. To have
    Scale show windows from the current viewport (the default), the command
    near the end of this script that begins 'org/freedesktop/compiz...',
    should read as follows:
    
        '/org/freedesktop/compiz/scale/allscreens/initiate_key'
        
To have Scale show windows from all viewports, change the command as follows:
    
        '/org/freedesktop/compiz/scale/allscreens/initiate_all_key'
        
Regardless of which approach you use, only the windows in the current viewport
    are (un)minimized. To (un)minimize windows from all viewports would be a
    dizzying experience due to the rapid viewport changing it would
    require."""
    
previousTime = 0

def get_screen():
    """Get the screen object and refresh the screen"""
    screen = wnck.screen_get_default()
    screen.force_update()
    return screen

def get_windows():
    """Get the list of all windows"""
    screen = get_screen()
    allWindows = screen.get_windows_stacked()
    return allWindows
            
def get_tasklist_windows():
    """Get the list of windows in the tasklist"""
    # The tasklist can be configured to include windows from other viewports
    allWindows = get_windows()
    tasklistWindows = []
    for window in allWindows:
        if window.is_skip_tasklist():
            continue
        elif window.is_skip_pager():
            continue
        elif window.is_sticky():
            continue
        else:
            tasklistWindows.append(window)
    return tasklistWindows

def get_viewport_windows(): 
    """Get the list of windows that are in the viewport"""
    allWindows = get_windows()
    screen = get_screen()
    workspace = screen.get_active_workspace()
    viewportWindows = []
    for window in allWindows:
        if window.is_in_viewport(workspace):
            viewportWindows.append(window)
    return viewportWindows

def get_eligible_windows():
    """Get the list of windows that are in the viewport and the tasklist"""
    # Only these windows are subject to being unminimized
    eligibleWindows = []
    allWindows = get_windows()
    tasklistWindows = get_tasklist_windows()
    viewportWindows = get_viewport_windows()
    for window in allWindows:
        if window in tasklistWindows and window in viewportWindows:
            eligibleWindows.append(window)
    return eligibleWindows
            
def get_ineligible_windows():
    """Get the list of windows that are in the viewport & not the tasklist"""
    # One of these windows will be activated later in the script 
    ineligibleWindows = []
    allWindows = get_windows()
    viewportWindows = get_viewport_windows()
    eligibleWindows = get_eligible_windows()
    activeWindow = get_active_window()
    for window in allWindows:
        if window in eligibleWindows:
            continue
        # Don't let the Desktop be included in the list of ineligibleWindows if
        #    it is currently active; otherwise, activating an ineligibleWindow
        #    later in the script will not trigger the initial active window
        #    change signal
        # Cannot refer to the Desktop by name because not every WM will list it
        elif window in viewportWindows and window != activeWindow:
            ineligibleWindows.append(window)
    return ineligibleWindows   

def get_active_window():
    """Get the active window"""
    screen = get_screen()
    activeWindow = screen.get_active_window()
    return activeWindow

def determine_minimized(windows):
    """Determine which windows in a given list are minimized"""
    minimizedWindows = []
    for window in windows:
        if window.is_minimized():
            minimizedWindows.append(window)
    return minimizedWindows

def window_command(window, command):
    """Handle various window actions"""
    # Use wmctrl instead of equivilant commands in xwit and wnck (the latter
    #    two can cause the tasklist to blink and wnck requires X server
    #    timestamps for some actions)
    # Use xwit for minimizing because wmctrl does not have a
    #    working minimize function
    if command == 'close':
        os.popen('wmctrl -ic ' + str(window.get_xid()))
    if command == 'maximize_toggle':
        os.popen('wmctrl -ir ' + str(window.get_xid()) +
            ' -b toggle,maximized_vert,maximized_horz')
    if command == 'minimize':
        os.popen('xwit -iconify -id ' + str(window.get_xid()))
    if command == 'unminimize' or command == 'activate':
        os.popen('wmctrl -ia ' + str(window.get_xid()))
    return

def reminimize(minimizedWindows):
    # Need a new list of eligible windows because one or more windows may
    #    have been closed by Scale
        activeWindow = get_active_window()
        newEligibleWindows = get_eligible_windows()
        for window in newEligibleWindows:
            if window == activeWindow:
                continue
            elif window in minimizedWindows:
                window_command(window, 'minimize')
        gtk.main_quit()

def handler_reminimize(screen, window, firstIneligibleWin,
    minimizedWindows):
    """Re-minimize previously minimized windows after Scale finishes"""
    # 'active_window_changed' WnckScreen signal
    # 'window' argument reflects previously active window, not the current one
    # Window selection, window close, and show desktop actions in Scale all
    #    trigger this signal
    # Hitting escape in Scale yields no signal; nothing can be done by this
    #    script in this instance. This script won't close and windows will
    #    not reminimize until after the user activated another window
    # No actions from Scale are received until Scale after has finished; also,
    #    after it finishes, only the signal from its final action is received
    #    (thus, multiple window closures can occur but not result in multiple
    #    received signals)
    # This script also triggers the signal (before invoking Scale), when it
    #    activates an ineligible window
    # Thus, need to check if the active window is the same as the ineligible
    #    window activated by this script
    # If it is, then the script will wait until a window state change is
    #    caused by Scale, rather than this script (so hurry up and wait)
    # If it is not, then the script will reminimize windows, unless the user
    #    selects the desktop in Scale, which is addressed by a different
    #    handler
    # ------------------------------------------------------------------------
    # Duration in seconds between when Scale activates and when you may select
    #    a window using Scale. Used to catch late-breaking, spontaneous active
    #    window change events. Resets with each such event
    # Adjust this variable as necessary 
    pluginDelay = 0.3
    # ------------------------------------------------------------------------
    activeWindow = get_active_window()
    global previousTime
    currentTime = time.time()
    if activeWindow == firstIneligibleWin:
        # This is most likely triggered by the script itself
        # Pass and await selection of a window by the user
        previousTime = currentTime    
    elif activeWindow in minimizedWindows:
        elapsedTime = 0
        if previousTime:
            elapsedTime = currentTime - previousTime
        if elapsedTime < pluginDelay:
            # Too little time has elapsed, meaning that the window was most
            #    likely made active by late mapping; reset the active window
            previousTime = currentTime
            window_command(firstIneligibleWin, 'activate')
        else:
            # Elapsed time is long enough, so presume the window was selected
            #    by the user; reminimize
            reminimize(minimizedWindows)
    else:
        # Active window is an originally unminimized window; no mapping issue
        if minimizedWindows:
            reminimize(minimizedWindows)
        else:
            gtk.main_quit()
    return
     
def handler_show_desktop(screen):
    # 'showing_desktop_changed' WnckScreen signal
    """Quit the script if the user selects the desktop in Scale"""
    screen = get_screen()
    toggledDesktop = screen.get_showing_desktop()
    if toggledDesktop:
        gtk.main_quit()
    return
    
def main():
    # ************************************************************************
    # Unminimize all minimized viewport windows
    # ************************************************************************
    eligibleWindows = get_eligible_windows()
    ineligibleWindows = get_ineligible_windows() 
    if eligibleWindows:
        minimizedWindows = determine_minimized(eligibleWindows)
    else:
        os._exit(0)
    if minimizedWindows:
        for window in minimizedWindows:
            window_command(window, 'unminimize')
    # ************************************************************************
    # Launch the Scale plugin of the Compiz window manager
    # ************************************************************************
    # Aside from ESCaping out, Scale will exit upon one of three actions:
    #    Selecting a tasklist window, closing the last tasklist window, or
    #    showing the desktop
    # Activating a non-tasklist window in this script ensures that Scale will
    #    always generate an 'active_window_changed' event when it exits
    # Launch Scale
    scale=os.popen('dbus-send --type=method_call ' +
    '--dest=org.freedesktop.compiz ' +
    # ------------------------------------------------------------------------
    # Update this line as desired according to instructions at the top of this
    #    script
    '/org/freedesktop/compiz/scale/allscreens/initiate_key ' 
    # ------------------------------------------------------------------------
    + ' org.freedesktop.compiz.activate string:\'root\' ' +
    'int32:`xwininfo -root | grep id: | awk \'{ print $4 }\'`')
    # ************************************************************************
    # Re-minimize previously minimized windows (other than any newly activated
    #    window and windows closed through Scale)
    # ************************************************************************           
    firstIneligibleWin = ineligibleWindows[0]
    window_command(firstIneligibleWin, 'activate')
    screen = get_screen()
    screen.connect('active_window_changed', handler_reminimize,
        firstIneligibleWin, minimizedWindows)
    screen.connect('showing_desktop_changed', handler_show_desktop)
    gtk.main()

if __name__ == '__main__':
    main()
```
Works the same as scale but shows minimized windows as well.
Just add it to CCSM > commands and choose an edge binding or key.

---

### Post by fisa on 2010-08-31
Try installing compiz-fusion-plugins-extra, restart the compiz config settings manager, and then enable the "Scale Window Title Filter".

---

### Post by &gt;6J8Fh,u&quot;4X(fEa9Y2x'k+Tx? on 2011-12-11
Check out [http://ubuntuforums.org/showthread.php?t=1242738](http://ubuntuforums.org/showthread.php?t=1242738), it worked for me.

---

