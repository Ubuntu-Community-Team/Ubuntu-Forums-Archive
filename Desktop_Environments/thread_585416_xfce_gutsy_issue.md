---
title: "xfce gutsy issue"
date: 2007-10-21
forum: Desktop Environments
---

### Post by g4m3b0y on 2007-10-21
Fresh install of xubuntu (7.10) on my laptop and have noticed that the battery monitor disappears from my panel. Tried to go through manually editing :

~/.config/xfce4/panel/panels.xml

and inserting:

<item name="battmon" id="11928562010"/>

as a child of the "<items>" node.

(11928562010) is the appended number of the battery monitor .rc file (battmon-11928562010.rc) in the same directory as panels.xml, which stores my preferences for the panel applet.  The .rc file is there but no line to reference it in the panels.xml file exists.

after the file is saved with the changes, i log out with saving the session (even tried without saving the session). log back in and no luck...my battery monitor applet disappears.... once i reopen the file, the line that i just added isn't there. whenever i try to add the applet to the panel, it doesn't even show up and the attempted addition to the panel isn't reflected in the panels.xml file. anyone have any ideas?

---

### Post by swnesbitt on 2007-10-22
I ran into the same problem. It also happens with the volume control panel plugin

> **g4m3b0y said:**
> Fresh install of xubuntu (7.10) on my laptop and have noticed that the battery monitor disappears from my panel. Tried to go through manually editing :

~/.config/xfce4/panel/panels.xml

and inserting:

<item name="battmon" id="11928562010"/>

as a child of the "<items>" node.

(11928562010) is the appended number of the battery monitor .rc file (battmon-11928562010.rc) in the same directory as panels.xml, which stores my preferences for the panel applet.  The .rc file is there but no line to reference it in the panels.xml file exists.

after the file is saved with the changes, i log out with saving the session (even tried without saving the session). log back in and no luck...my battery monitor applet disappears.... once i reopen the file, the line that i just added isn't there. whenever i try to add the applet to the panel, it doesn't even show up and the attempted addition to the panel isn't reflected in the panels.xml file. anyone have any ideas?

---

### Post by ybmabcd on 2007-11-17
I also have the same problem, it happen with "network monitor , system load monitor & volume control".
In addition, when i click the "xfce meun" - "quit" button, it does not prompt the logout selection dialog, i need to click for a few time until it show on.

---

### Post by Evil_Catbert on 2007-12-12
I'm having the exact same problem. Running Xfce desktop on Gutsy. HW: Acer Travelmate 290.

Anyone of you xperienced guys know anything about this?

---

### Post by Tomas_IV on 2007-12-14
So at least I'm not alone. I can confirm the same problem here on two computers, my volume control applet disappeared and it is not possible to add it again. :confused:

---

### Post by rrwo on 2007-12-22
I've had the same problem with Feisty as well as Gutsy: clicking on Quit in Xfce menu often does nothing and has to be clicked several times.  I think this may be an Xfce issue and not an Ubuntu issue, as I've had it when running the version of Xfce downloaded from xfce.org rather than one from the distribution.

---

### Post by Kevuntu on 2008-01-21
I have the same problem and I think I know why.
It happened when I made a custom .Xsession for compiz.

Here's what I think is going on:
After a fresh install, Xubuntu's default session is "run X session script" or something. This session runs all the additional stuff like volume applet and battery monitor (they both disappeared on my computer) and then, xubuntu-session.
When I made my custom X session script, I overwrote Xubuntu's script (called .Xsession). So now, I select the "run X session script" session in GDM's session list to run compiz, and to run xfce4, I select "Xfce4". BUT, as I said earlier, some things aren't loaded anymore in the Xfce4 session (volume and battery monitor).

What we have to do now, is to find the name of those missing programs' names and add them to the Autostarted Applications list. Could someone look at his default "run X session script" session to check what programs are run? ONLY XUBUNTU USERS CAN DO THAT.

I'm using Xubuntu Gutsy.

---

### Post by mordredp on 2008-02-02
a workaround to solve this is to kill the panel and remove ~/.config/xfce4/panel/ (or make the changes to the config files, i have not tried it). If you have only panel you can just right-click, select customize panel and press the - button to remove it. You can re-enable the panel by running xfce4-panel.

---

### Post by cpetrus on 2008-02-12
I'm having the same issues except only with the battery monitor app at the moment using Gutsy. I noticed the following in my .xsession-errors file so I hope it adds to the discussion. I'm not quite sure how to interpret it. 

> The program 'xfce4-battery-plugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 186 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** Message: Battery Monitor: screen changed: 0

** Message: No valid plug window.

(xfce4-panel:5240): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (socket)' failed

** (xfce4-panel:5240): CRITICAL **: An item was unexpectedly removed: "Battery Monitor".

If anyone has any ideas, that would be great.

---

### Post by Arthur Archnix on 2008-03-06
Same issue. Battery doesn't show up. Haven't tried any of the others.

---

