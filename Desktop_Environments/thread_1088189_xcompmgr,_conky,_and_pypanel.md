---
title: "xcompmgr, conky, and pypanel"
date: 2009-03-05
forum: Desktop Environments
---

### Post by ivaarsen on 2009-03-05
Heya, guys.

I'm playing around with a new (to me) desktop environment, a simple OpenBox with Conky / Pypanel / Xcompmgr setup.  I had conky and pypanel set up pretty much how I wanted, but decided to add xcompmgr a little later.

Now, I have everything pretty well figured out as far as configuring either by themselves, but my two-fold question is in how these programs relate to or effect each other.

Part 1 - When I start xcompmgr, my pypanel (which is set up slightly opaque) goes solid back ground color - but still opaque.  The buttons still work, but I can't see them.  What's my misconfiguration?

Part 2 - I don't want my conky 'window' to drop a shadow.  How do I prevent this?

Thanks for your time, guys!

---

### Post by m_duck on 2009-03-05
To get you pypanel as you want it, you may need to edit ~/.pypanelrc again. Namely the background colours, font colours and the "alpha" line. If that doesn't help, can you post a copy of your ~/.pypanelrc and a screenshot so I may be able to be more useful.

For conky's shadow, that will appear because xcompmgr is launched with an option for shadows. You should be able to fix it by changing the settings in the top of your ~/.conkyrc, the setting that is important I think will be "own_window" should be set to "no"```
own_window no
```So conky will not be treated as a separate window and thus shouldn't be given a shadow.

If *that* doesn't work, post your ~/.conkyrc and I'll have a look through that as well :D

---

### Post by ivaarsen on 2009-03-06
These are on loan (or stolen?) from another forum-goer.  Screen shots attached.

conky

```
use_xft yes
xftfont cure:pixelsize=11
xftalpha 1.0
update_interval 2

own_window yes
own_window_colour 222222
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type override

double_buffer yes
draw_shades no
draw_outline no
draw_borders no

default_color cccccc
color0 ffffff

gap_x 5
gap_y 5
alignment top_left
no_buffers yes
uppercase no

TEXT
   ${color}host ${color0}$nodename // ${color}kernel ${color0}$kernel // ${color}uptime ${color0}$uptime // ${color}cpu ${color0}${cpu cpu0}% // ${color}ram ${color0}$mem // ${color}root ${color0}${fs_free /} //  ${color}home ${color0}${fs_free /home} // ${color}eth0 ul ${color0}${upspeed eth0}KB/s ${totalup eth0} // ${color}eth0 dl ${color0}${downspeed eth0}KB/s ${totaldown eth0} // ${color}eth1 ul ${color0}${upspeed eth1}KB/s ${totalup eth1} // ${color}eth1 dl ${color0}${downspeed eth1}KB/s ${totaldown eth1}
```

pypanel
```

#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x000000"    # Panel background and tinting color
TASK_COLOR      = "0x555555"    # Normal task name color 
FOCUSED_COLOR   = "0xcccccc"    # Focused task name color
SHADED_COLOR    = "0x555555"    # Shaded task name color 
MINIMIZED_COLOR = "0x555555"    # Minimized task name color 
DESKTOP_COLOR   = "0xcccccc"    # Desktop name color
CLOCK_COLOR     = "0xcccccc"    # Clock text color
LINE_COLOR      = "0xcccccc"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 0             # Panel width: 0 = Use full screen width
P_START         = 0             # Starting X coordinate of the panel
P_SPACER        = 4             # Spacing between panel objects
P_HEIGHT        = 14            # Panel height

#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 12            # Panel application icon height
I_WIDTH         = 12            # Panel application icon Width 
APPL_I_HEIGHT   = 18            # Application launcher icon height
APPL_I_WIDTH    = 18            # Application launcher icon width
TRAY_I_HEIGHT   = 16            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 16            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = "%Y-%m-%d %H:%M"    # Ex: 2004-09-25 17:45 

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 20

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = []            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "cure-8" 
#------------------------------------------------------------------------------
FONT            = "cure-8"

#------------------------------------------------------------------------------
# Show All Applications: Show apps from all desktops or just the current
# 0: Disabled - Only applications on the current desktop will be displayed
# 1: Enabled  - Selected apps are moved to the current desktop
# 2: Enabled  - Current desktop is changed to the selected apps desktop
#------------------------------------------------------------------------------
SHOWALL         = 0             # 0, 1 or 2 - see descriptions above

#------------------------------------------------------------------------------
# Show Minimized/Iconified Applications: Show only minimized apps or all apps
# 0: Disabled - Show all applications on the panel
# 1: Enabled  - Show only minimized apps on the panel
#------------------------------------------------------------------------------
SHOWMINIMIZED   = 0

#------------------------------------------------------------------------------
# Application Icon List: List of custom icons for specific applications
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
#
# The "default" entry is used for applications with no icon.  If left "",
# PyPanel will use the default icon distributed with the source.
#
# Add entries using the following format -
#     "<application name>" : "<full path to icon>",
#------------------------------------------------------------------------------
ICON_LIST       = {
                   "default" : "",
                   "example" : "/usr/share/imlib2/data/images/audio.png",
                  }
                  
#------------------------------------------------------------------------------
# Application Launch List: Ordered list of icons and applications for the
#                          application launcher.
# 
# Add entries using the following format -
#     ("<executable>", "<full path to icon>")
#------------------------------------------------------------------------------
LAUNCH_LIST     = []

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 150

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 0             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = []

#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 1             # Desktop name section
TASKS           = 2             # Task names section 
TRAY            = 3             # System tray section
CLOCK           = 4             # Clock section
LAUNCHER        = 0             # Application launcher section

#------------------------------------------------------------------------------
#                       Button Event Function Definitions
#------------------------------------------------------------------------------
# Left click   - button 1 
# Middle click - button 2
# Right click  - button 3
# Wheel up     - button 4
# Wheel down   - button 5 
#
# changeDesktop(x)
# - Change Desktop: Increase or decrease the current desktop by 'x' amount
# 
# toggleShade(task)
# - Shade or Unshade an application
#
# toggleHidden()
# - Minimize the panel to the top or bottom depending on its start location
#
# toggleMinimize(task, traise=1)
# - Minimize or Unminimize an application and optionally raise it
#
# taskRaise(task, focus=1)
# - Raise an application to the top of the window list and optionally focus it 
#
# taskLower(task, focus=0)
# - Lower an app to the bottom of the window list and optionally focus it
#
# taskFocus(task)
# - Give focus to the selected application, if it has focus then minimize it
#
# showDesktop()
# - Toggle between hiding and unhiding ALL applications
#------------------------------------------------------------------------------

#----------------------------------
def desktopButtonEvent(pp, button):
#----------------------------------
    """ Button event handler for the panel's desktop object """
        
    if button == 1:
        pp.changeDesktop(-1)
    elif button == 2:
        pp.changeDesktop(2)
    elif button == 3:
        pp.changeDesktop(1)
    elif button == 4:
        pp.changeDesktop(1)
    elif button == 5:
        pp.changeDesktop(-1)
        
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("xclock &")
    elif button == 2:
        pass
    elif button == 3:
        pp.toggleHidden()  
    elif button == 4:
        pp.showDesktop()
    elif button == 5:
        pp.showDesktop()
        
#--------------------------------
def panelButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel with no active tasks """
    
    if button == 1:
        pass
    elif button == 2:
        pass
    elif button == 3:
        pass
    elif button == 4:
        pass
    elif button == 5:
        pass
        
#-------------------------------------
def taskButtonEvent(pp, button, task):
#-------------------------------------
    """ Button event handler for the panel's tasks """
    
    if button == 1:
        pp.taskFocus(task)
    elif button == 2:
        # Destroy the application
        task.obj.destroy()
    elif button == 3:
        # Ex. - XMMS doesn't shade, so we want to minimize it instead and
        #       still use button 3 to shade other applications
        #       task.tclass is the tasks class name (WM_CLASS)
        if "xmms" in task.tclass:
            pp.toggleMinimize(task)
        else:
            pp.toggleShade(task)
    elif button == 4:
        pp.taskRaise(task, focus=1)
    elif button == 5:
        pp.taskLower(task, focus=0)
        
```

---

### Post by m_duck on 2009-03-06
OK, I think if you set "own_window yes" to "own_window no" in your ~/.conkyrc that should solve the conky problem.

As for pypanel, it's weird, I've not seen that before! My first guess is try setting the "SHADE" option (I said alpha earlier, meant shade) to 255 and see what happens. Other than that, what if you just launch "xcompmgr" but without any options passed to it? If that fixes it, just try one option at a time so we can see which is causing the problem. If not, more thinking is called for...

---

### Post by ivaarsen on 2009-03-06
I had tried your fix already for conky, by setting own_window to 'no', but it seemed to draw over the whole desktop instead of just the bar it's supposed to be - after I start xcompmgr.

Are all these symptoms more because of own_window_type is set to 'override'?  You'll have to forgive my noob-ishness, I'm comparing this to other conky's I have running on other machines, and those are set to 'normal'.  A little quick research tells me that 'override' ignores window_hints, which I obviously don't want.

I'll give these a try, thanks for your help.

---

### Post by m_duck on 2009-03-06
It could be. I don't always get exactly what the options in conky do, just keep fiddling until it works! Try desktop or normal for own_window_type instead of override and see what happens. I'll test it soon when I can get access to linux.

---

### Post by Kabatwa on 2009-05-07
There's a few options in conky that you have to set up so that it get's along with xcompmgr. I've found that - 
```

own_window yes
own_window_transparent yes
own_window_type desktop

```Seems to work. Let me know how you get on. No idea about the pypanel thing. Good luck!

Tim

---

