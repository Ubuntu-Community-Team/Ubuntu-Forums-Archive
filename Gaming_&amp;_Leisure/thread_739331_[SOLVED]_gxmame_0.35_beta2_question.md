---
title: "[SOLVED] gxmame 0.35 beta2 question"
date: 2008-03-29
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-29
Hi,
I have the excellent gxmame 0.35 beta2 installed in Ubuntu 7.10.
Under options>directories selection; I can change the directory of the roms folder to point to my roms at ...Documents/Games-Linux/Emulators/Mame/Roms

However when I try to change the directory to point to my cabinets.zip file at ...Documents/Games-Linux/Emulators/Mame/cabinets the file is greyed out and I cannot select it. Also I cannot point to the icons.zip and other directories.

Does anyone know a solution?

Thank you.

---

### Post by FranMichaels on 2008-03-29
GXMame is out of date unfortunately.

You can try [http://www.anti-particle.com/wahcade.shtml](http://www.anti-particle.com/wahcade.shtml)

or

[https://sourceforge.net/projects/gva/](https://sourceforge.net/projects/gva/)

And this one I haven't tried but will
[http://gmameui.sourceforge.net/](http://gmameui.sourceforge.net/)

It's a continuation of gxmame :)

---

### Post by Rytron on 2008-03-30
Hi FranMichaels,
I am unable to use gnome-video-arcade-0.5.6 or ahcade_0.25_i386.

I can't figure out how to compile gnome-video-arcade-0.5.6. It says go to the directory where the source code is, so I cd to the src folder (is this correct?). 

I installed the wahcade_0.25_i386 package. It is under applications>games, when I click on it nothing happens. Then I go to terminal and type wahcade and it starts as a black screen with All Games and M.A.M.E in white text at the top of the screen. In the terminal it says this:

```
$ wahcade
/home/myname/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/myname/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/myname/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Please Wait. Creating initial filter...
Error: rom path: [~/emulators/mame/roms] does not exist
Error: emulator info file: [~/emulators/mame/mameinfo.xml] does not exist
       cannot create initial filters!
Error: filter file: [/home/myname/.wahcade/files/mame-0.ftr] does not exist
Error: filter file: [/home/myname/.wahcade/files/mame-0.ftr] does not exist
Error: history file: [~/emulators/mame/history.dat] does not exist
Error: Music Path [] does not exist
myname@Tron:~$ 
```

I am baffled. I will stay with GXMame until I sort one or both of the above MAME programs.

---

### Post by wingnux on 2008-03-30
SDLMAME works just fine and it has a built-in rom browser.

---

### Post by DoktorSeven on 2008-03-30
Please refer to [this thread](http://ubuntuforums.org/showthread.php?t=545066&highlight=sdlmame) for instructions on using SDLMame and wahcade and other frontends for MAME.

---

### Post by Rytron on 2008-04-24
Regarding my original post. There is a xmamerc text file in the /etc directory. This can be edited with a text editor as root to change paths.

---

