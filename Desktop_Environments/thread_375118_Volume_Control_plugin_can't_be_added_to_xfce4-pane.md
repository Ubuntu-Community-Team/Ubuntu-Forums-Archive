---
title: "Volume Control plugin can't be added to xfce4-panel"
date: 2007-03-03
forum: Desktop Environments
---

### Post by picpak on 2007-03-03
Hello,

With Xfce 4.4 on Xubuntu 6.10, I cannot add the Volume Control plugin to my panel.

I right click the panel, click add new item, and add the Volume Control plugin.

A little black line appears on the panel, then disappears. No plugin.

Can anyone help me?

---

### Post by picpak on 2007-03-04
This might help -- it's what xfce4-panel tells me when I try to load the Volume Control plugin:

```
kim@komputer:~$ xfce4-panel
The program 'xfce4-mixer-plugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 182 error_code 10 request_code 33 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** Message: Volume Control: screen changed: 0

** Message: No valid plug window.

(xfce4-panel:6296): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (socket)' failed

** (xfce4-panel:6296): CRITICAL **: An item was unexpectedly removed: "Volume Control".
```

---

### Post by picpak on 2007-03-04
Would this have anything to do with using [Xorg 7.2](http://ubuntuforums.org/showthread.php?t=373087)?

---

### Post by f03el on 2007-03-27
I had the same problem, but discovered that it works if you drag the volume plugin from the list to the panel.

---

### Post by Munksgaard on 2007-09-20
Thank you, that worked :)

---

### Post by picpak on 2007-09-21
> **f03el said:**
> I had the same problem, but discovered that it works if you drag the volume plugin from the list to the panel.

THANK YOU!!! I've had this problem for ages. Now if only I read this six months ago...

---

### Post by predaeus on 2007-10-26
Yes! Thanks, it works.

---

### Post by EisenPM on 2007-10-26
It seems to depend on the theme. With Murrina Stormcloud it works, with my theme (Tish Ubuntulooks) it doesn't work, not even with dragging the appelt into the panel.

There are two bug reports:

[https://bugs.launchpad.net/xfce4-mixer/+bug/90261](https://bugs.launchpad.net/xfce4-mixer/+bug/90261)

[http://bugzilla.xfce.org/show_bug.cgi?id=2971](http://bugzilla.xfce.org/show_bug.cgi?id=2971)

---

### Post by mrmts on 2007-11-09
Oh wow.. you are absolutely right.
I had to switch themes to mistyclouds, then i was able to drag an drop it to the bar. Then i switched themes back and it worked.
Sweet!

---

### Post by cerceaux on 2007-11-09
Instead of clicking on the 'Add' button, just drag the Volume control icon to the panel

---

### Post by mrmts on 2007-11-14
In response to my previous reply...
Every time I restart PC, The volume control doesnt load, (or dissapears)
Which means that i have to go through the whole process of changing the theme, adding the volume, then changing the theme back(to the one I prefer)


...not fun

---

### Post by gtr225 on 2007-12-16
> **mrmts said:**
> In response to my previous reply...
Every time I restart PC, The volume control doesnt load, (or dissapears)
Which means that i have to go through the whole process of changing the theme, adding the volume, then changing the theme back(to the one I prefer)


...not funOnce I log out and log back in the volume control is gone from my panel.

---

### Post by hangar_18 on 2008-02-26
NOW POSTED IN RIGHT TOPIC (sorry for that):

after about 2 hours of reading bug reports i found out that it is theme issue,
i use Xfce-dark theme, i have succesfully fixed it now!
just edit your theme..volume control is working only with engine murrine
most of the themes are using xfce engine
editing file /usr/share/themes/your_theme/gtk-2.0/gtkrc,
replacing engine part

with engine part grabbed from MurrinaStormCloud
>   engine "murrine" 
  {
	listviewstyle = 0 # 0 = nothing, 1 = dotted
	menuitemstyle = 1 # 0 = flat, 1 = glassy, 2 = striped
	glazestyle = 0 # 0 = flat hilight, 1 = curved hilight, 2 = concave style, 3 = top curved hilight, 4 = beryl style
	scrollbar_color = "#d4d4d4"
    	contrast = 1.5
	menubarstyle = 1 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
	menubaritemstyle = 1 # 0 = menuitem look, 1 = button look
	listviewheaderstyle = 1 # 0 = flat, 1 = glassy, 2 = raised
	roundness = 2 # 0 = squared, 1 = old default, more will increase roundness
    	animation = TRUE # FALSE = disabled, TRUE = enabled
	scrollbarstyle = 0 # Enable or disable circles, stripes, handles
  }
fixed the problem, volume control is still there after restarting xfce!
it changed some colors,but thats no problem to fix,question of 5 minutes :)
hope this will help

---

### Post by hangar_18 on 2008-02-27
ok i figured out that my last solution was working only when restarting xfce, after system restart it was gone from the panel....
i played with it for a while and i get to the point when volume control is stil there after 2 system restarts..
i did this:

1. go to the /home/.config/xfce4/panel/

2. you find a file or files with diferrent numbers in name there called 
xfce4-mixer-12041202040.rc !!the numbers aren't same in yours!!

3. make a copy, rename it to xfce4-mixer.rc put it to the same folder, and delete old xfce-mixer.. file/files with number

4. open panels.xml with mousepad. find <item name="xfce4-mixer"....>
and replace it with <item name="xfce4-mixer" id=""/>

5. add volume control dragging it on the xfce panel

6. restart xfce

7. restart system

8. you can write here if it worked cause it may depend on theme you are using

if this won't work tommorow i [censored] :lolflag: :lolflag:

---

### Post by dark_phantom on 2008-02-27
I'll try some suggestions, thanks!

---

