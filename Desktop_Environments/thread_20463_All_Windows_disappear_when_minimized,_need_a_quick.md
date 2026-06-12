---
title: "All Windows disappear when minimized, need a quick fix."
date: 2005-03-16
forum: Desktop Environments
---

### Post by DR_K13 on 2005-03-16
sorry for the noob question---i am running Gnome 2.6 and whenever I minimize a window ( firefox,term, anything ) It disappears!  I want it to drop into the  Panel when I minimize . I dont know what I changed but its making me mad,  please help! :oops:

---

### Post by Xian on 2005-03-16
Right-click on an unused portion of your panel. 
Select Add To Panel and choose Window List from the options provided.

---

### Post by bored2k on 2005-03-16
[QUOTE=DR_K13]sorry for the noob question---i am running Gnome 2.6 and whenever I minimize a window ( firefox,term, anything ) It disappears!  I want it to drop into the  Panel when I minimize . I dont know what I changed but its making me mad,  please help! :oops:[/QUOTE]
 Right clic on the panel > add to panel > window list

I think gnome 2,6 doesnt have this though ... :S

---

### Post by DR_K13 on 2005-03-16
Thanks .  :oops:    ya gnome 2.6  does have it cool/

another question>  how do i get back to the configuration panel that shows up during  the install,  I need to mess with my soundcard settings?

---

### Post by Xian on 2005-03-16
[QUOTE=bored2k]I think gnome 2,6 doesnt have this though ... :S[/QUOTE]
Yeah, it's got it....but the method is a little different.

Again, right-click and select Add To Panel. 
Then highlight "Utility" in the menu and choose "Window List"

---

### Post by Xian on 2005-03-16
[QUOTE=DR_K13]how do i get back to the configuration panel that shows up during  the install,  I need to mess with my soundcard settings?[/QUOTE]
Open a terminal or choose Run Program from the panel menu and type in:

gnome-control-center

If that's what you mean.....?

---

### Post by DR_K13 on 2005-03-16
[QUOTE=Xian]Open a terminal or choose Run Program from the panel menu and type in:

gnome-control-center[/QUOTE]

it was different, the one I saw during the install was much more involved, you could select video / sound card types / etc.

---

### Post by Xian on 2005-03-16
What install did you use....?

---

### Post by Nis on 2005-03-16
Are you even using Ubuntu?  Ubuntu has never come with GNOME 2.6 and while there is a dialog during the install to select your display resolution there are no controls for video or sound cards.

---

### Post by bored2k on 2005-03-16
[QUOTE=Nis]Are you even using Ubuntu?  Ubuntu has never come with GNOME 2.6 and while there is a dialog during the install to select your display resolution there are no controls for video or sound cards.[/QUOTE]
 Thinking the same thing, maybe mandrake 10 thinking hes a newbie .

---

### Post by DR_K13 on 2005-03-16
its version 4.10 I didnt download the iso, I got the disc from ubuntu in the mail

---

### Post by bored2k on 2005-03-16
I dont think its gnome 2.6 ...

---

### Post by DR_K13 on 2005-03-17
See above post

---

### Post by bored2k on 2005-03-17
[QUOTE=DR_K13]See above post[/QUOTE]
 gnome-about in a terminal .
2.6 ? bizarre

---

### Post by DR_K13 on 2005-03-17
2.8.1

my bad

---

### Post by bored2k on 2005-03-17
[QUOTE=DR_K13]2.8.1

my bad[/QUOTE]
 We thought so ;) .

---

### Post by DR_K13 on 2005-03-17
ok lol, you have to forgive me, I am new to this distro and have only used Suse , mandrake and redhat.

Another problem I am having is trying to start gdesklets.

I get this error


```
/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
``` 

how do I use gtk.man?

---

### Post by bored2k on 2005-03-17
[QUOTE=DR_K13]ok lol, you have to forgive me, I am new to this distro and have only used Suse , mandrake and redhat.

Another problem I am having is trying to start gdesklets.

I get this error


```
/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
``` 

how do I use gtk.man?[/QUOTE]
 Was that a compiled gdesklets or apt-gotten gdesklets gdesklets-data ?

---

### Post by DR_K13 on 2005-03-17
apt-get

---

### Post by bored2k on 2005-03-17
[QUOTE=DR_K13]apt-get[/QUOTE]
 If apt-get fails on desklets heres what I normally recommend [not for the faint of heart] :
Download the official .gz file.

Start compiling it and install applications as it is telling you it needs them. After a while I normally find a requirement I dont find and retry apt-gtting it, and It mostly works. Cheap but does the trick.

It did install normally here [I removed in a quicky though] .

---

### Post by DR_K13 on 2005-03-17
ok after installing a ton of stuff, I cant find this.

```
sr/lib/glib-2.0/include -I/usr/include/pyorbit-2 -I/usr/include/orbit-2.0
checking GDESKLETS_LIBS... -Wl,--export-dynamic -pthread -lgobject-2.0 -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0
checking for glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0... Package gdk-pixbuf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-pixbuf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-pixbuf-2.0' found

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
sean@ubuntu:~/downloaded/gDesklets-0.34.2 $
```

---

### Post by bored2k on 2005-03-17
[QUOTE=DR_K13]ok after installing a ton of stuff, I cant find this.

```
sr/lib/glib-2.0/include -I/usr/include/pyorbit-2 -I/usr/include/orbit-2.0
checking GDESKLETS_LIBS... -Wl,--export-dynamic -pthread -lgobject-2.0 -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0
checking for glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0... Package gdk-pixbuf-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-pixbuf-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-pixbuf-2.0' found

configure: error: Library requirements (glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
sean@ubuntu:~/downloaded/gDesklets-0.34.2 $
```[/QUOTE]
 glib-2.0 gdk-pixbuf-2.0 gtk+-2.0 pygtk-2.0

You need to get those files working, wether its apt or looking them up.

im going to bed so no more live instant help from my side :P .

---

### Post by iomicifikko on 2005-03-17
QUOTE

Code:

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead self.warn(message, DeprecationWarning)


/QUOTE


--> im a newbie <---

wait my friend!

when u get that kind of error, its not the gdesklets doesnt work (as i thought myself dont knowing how gdesklets works), its simply a message but gdesklets is working! (u can give a look in the system monitor).  the thing is that the version of gdesklets in ubuntu repositories doesnt come with any kind of "working icon" in the bar  but is working in "background".

once u started gdesklets u have simply to double click on a ".display" file (gdesklets file type) and move your mouse on the desktop (u will see just like u are moving something) and click where u wanna put the applet.

to find display files go to the gdesklets site (search it in google) or install with synaptic "gdesklets-data" and go to the /usr/share/gdesklets/Displays dir

byez

---

