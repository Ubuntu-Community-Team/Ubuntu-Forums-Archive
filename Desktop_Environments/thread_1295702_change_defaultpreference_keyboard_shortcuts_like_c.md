---
title: "change default/preference keyboard shortcuts like copy &amp; paste"
date: 2009-10-19
forum: Desktop Environments
---

### Post by meka4996 on 2009-10-19
Hi! May I know how to change or customize the default Ubuntu Gnome shortcuts like copy ctrl+c, paste ctrl+v,...

I know there are Preferences-> Keyboard Shortcuts, and some programs like keytouch, xbindkeys, GNOME Metacity, autoHotkeys/IronAHK, xbindkeys, XMacro[discontinued], ... They all require some commands to work. Are there such commands? As I only know ctrl+c, ctrl+v, or middle mouse key.

xmodmap and XKeyCaps... utility for modifying keymaps and pointer button mappings in X ... I don't think this is what I want...
[http://www.xfree86.org/4.0/xmodmap.1.html](http://www.xfree86.org/4.0/xmodmap.1.html)
[http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)

kbd-mangler?? discontinued?
[http://kbd-mangler.sourceforge.net/](http://kbd-mangler.sourceforge.net/) a tool to modify the keyboard behaviour at a low level in the linux kernel. Modifications are transparent for the entire system and work

Crikey ... current
[http://shallowsky.com/software/crikey/](http://shallowsky.com/software/crikey/)
Conveniently Repeated Input Key: a program to map strings to keys on Linux

KBDE ... discontinued?[http://kbde.sourceforge.net/](http://kbde.sourceforge.net/) 
keyboard emulator. It allow emulate keyboard input for keyboardless x86 computers. 

xrebind ... discontinued?
[http://linux.softpedia.com/get/Utilities/xrebind-11128.shtml](http://linux.softpedia.com/get/Utilities/xrebind-11128.shtml)
xrebind allows you to bind keys or buttons. These can be used to generate mouse motions, button presses or releases, key presses or releases, or to launch programs.


So my question is:
How to make a keyboard shortcut invoke another keyboard shortcut?
or 
any commands that can copy highlighted texts in X-Windows??
Thanks!

---

### Post by martrn on 2009-10-19
> **meka4996 said:**
> May I know how to change or customize the default Ubuntu Gnome shortcuts like copy ctrl+c, paste ctrl+v,...

How to make a keyboard shortcut invoke another keyboard shortcut?

Any commands that can copy highlighted texts in X-Windows??

1. [http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts]("http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts")
(Gnome keyboard shortcuts to the far right.)

2.  Why would you want to invoke a keyboard shortcut from another, you could just change the keyboard shortcut action in System-->Preferences-->KeyboardShortcuts, like you say.

3.  You can in gnome (though not in xwindows i guess).  Its the windows manager which is part of the Desktop environment that invokes the keyboard shortcut.  Although also note that when a application is compiled (say using gcc) the keyboard short cuts can be passed to an application on an per-application basis because the signals get sent like this....

Key_pressed  --->   Gnu/Linux/Kernel   --->  DesktopEnviroment(or X11Windows)  -->  Application........  etc......

You could compile/run an/any application to catch key-presses to perform actions if you wish.

What exactly do you wish to do ???

---

### Post by meka4996 on 2009-10-19
Hi! yes, System--> Preferences--> KeyboardShortcuts -> no copy or paste functions... only sounds, search...
I can't add one because I don't know the command that read highlighted texts...

windows manager, nautilus?
well, like when I press Super_L, then it will invoke ctrl+c, as if I've pressed ctrl+c. Examples like copying texts from websites[Firefox] to text files[gedit], as my fingers need a rest =) 

an application to catch key-presses? what kind of application? 
emulator application??
thanks!

---

### Post by martrn on 2009-10-19
> **meka4996 said:**
> Hi! yes, System--> Preferences--> KeyboardShortcuts -> no copy or paste functions... only sounds, search... I can't add one because I don't know the command that read highlighted texts...

Dough !

> **meka4996 said:**
> windows manager, nautilus?  well, like when I press Super_L, then it will invoke ctrl+c, as if I've pressed ctrl+c. Examples like copying texts from websites[Firefox] to text files[gedit], as my fingers need a rest =)

[URL="http://sourceforge.net/projects/jwmodgen/files/JW_Record_Playback/"]
http://sourceforge.net/projects/jwmodgen/files/JW_Record_Playback/[/URL]
[http://xmacro.sourceforge.net/]("http://xmacro.sourceforge.net/")

> **meka4996 said:**
> an application to catch key-presses? what kind of application?  emulator application?? thanks!

I mean a Macro package for recording and replaying keyboard and mouse events on an X server.

---

