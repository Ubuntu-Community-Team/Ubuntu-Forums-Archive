---
title: "Openbox, pypanel, and cpu monitor applet(s)"
date: 2009-01-25
forum: Desktop Environments
---

### Post by spipe on 2009-01-25
Is there a way to get cpu usage displayed in a docked applet, if using openbox and pypanel (or fbpanel)?

wmcpuload and shermans_applet are a couple that I have tried, but both of them show up on the desktop. This is not what I'm after.  Rather I want something that takes up residence neatly in the panel, say next to the clock.  Like the way nm-applet behaves.

I ask this because I've recently switched to openbox from my old standby WM, icewm, which provides handy little scrolling cpu/network activity graphs.  The reason for the switch is that I much prefer openbox's way of placing new windows, at least in a two-monitor system.

(Actually if I could get icewm to use both monitors according to free space, rather than always dropping new windows onto the same screen that has the focused window, I'd probably go back to icewm.  But that's another topic for another time, maybe.)

---

### Post by Stefanie on 2009-01-26
why don't you use conky?

---

### Post by spipe on 2009-01-26
Conky is nothing like I described above, unless I'm missing a command line option or something.

I'm looking for a simple graph or numeric readout that will fit in a tiny 16 pixel square (or 24 pixels or however tall the taskbar is).  It should always be there and not occupy any screen real estate outside the taskbar.

---

### Post by urukrama on 2009-01-26
Doesn't fbpanel have a cpu meter? According to the [website]("http://fbpanel.sourceforge.net/") it does.

wmcpuload (and other WindowMaker dockapps) should load in Openbox's dock, which can be set to autohide (see the rc.xml or obconf). You could also use Gkrellm, which can also be loaded in the dock.

I'm not sure of an application that would load in the system tray/notification area, but there are several other panels available that have a cpu meter (xfce4-panel and lxpanel). If you like fbpanel, you might like lxpanel (I believe the latter was based on the former).

---

### Post by spipe on 2009-01-30
> **urukrama said:**
> Doesn't fbpanel have a cpu meter? According to the [website]("http://fbpanel.sourceforge.net/") it does.

wmcpuload (and other WindowMaker dockapps) should load in Openbox's dock, which can be set to autohide (see the rc.xml or obconf). You could also use Gkrellm, which can also be loaded in the dock.

I'm not sure of an application that would load in the system tray/notification area, but there are several other panels available that have a cpu meter (xfce4-panel and lxpanel). If you like fbpanel, you might like lxpanel (I believe the latter was based on the former).

fbpanel's website does claim there is a cpu monitor, bug there's no mention of it anywhere else in the documentation or the sample configurations, no indication of how to turn it on.

I had tried wmcpuload, and just now tried gkrellm too.  I hate to sound stupid, but how do you make either of these display in the dock?  After reading both manpages and trying the various command line switches, I still can't make either of them appear anywhere but on the main desktop.

I'm missing something obvious here, I'm sure.

---

### Post by spipe on 2009-01-30
... lxpanel looks like it might be a winner though.  Thanks for that suggestion.

---

### Post by oswaldkelso on 2011-04-09
For cpu in fbpanel add the following to your config:

code:
 
Plugin {
    type = cpu
    config {
    tooltip = run-top
     Action = xterm -e top 
     }
}

---

