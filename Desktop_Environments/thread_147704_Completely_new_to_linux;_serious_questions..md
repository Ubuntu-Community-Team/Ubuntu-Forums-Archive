---
title: "Completely new to linux; serious questions."
date: 2006-03-20
forum: Desktop Environments
---

### Post by fenderlicious on 2006-03-20
I snatched linux as an alternative to the easily-broken Windows and the oft-sluggish Mac OS. And I do like how it works, I really do.
All I really do, on my computer though, is listen to the occasional song and get online once or twice a week to check my email, maybe download a new song.
I just installed it yesterday (Had to have my dad overnight me a new disc to install from), and I want to have exactly two items on my desktop: a folder for my music and Firefox so I can get online.
I'm honestly confounded a bit by the lack of support for doing this; I know the OS has a GUI that's 100% customizable but I have no idea how to do so.
When I log in there's just the mouse and a black desktop, I have to goto a command line to do anything.
My computer's an iMac G3, just so you know.
I really just would like help with finding how to make the most of the GUI for my general use.

---

### Post by DirtDawg on 2006-03-20
That's not how Ubuntu normally acts. It sounds like you may have had install problems or a bad copy.

---

### Post by fenderlicious on 2006-03-20
Hmm.
It's a good disc, maybe I should have gone with the expert install?
Ah, just something I realized, I don't know how to run firefox in Linux. How would I do this from the Console, I think it's called?

---

### Post by linbetwin on 2006-03-20
You have a Firefox shortcut on the top panel (it's a blue globe without the fox wrapped around it), but if you want a Firefox icon on the monitor, go to Applications menu > Internet. Right-click on the Firefox browser entry and click Add to desktop.

If you want a folder for your music, right-click on the desktop and click Create folder. Then put your music in that folder.

---

### Post by fenderlicious on 2006-03-20
Ah, can't right-click. Mac machine. When I log in, there's nothing but a blank black desktop and the mouse. That's what I'm trying to fix.

---

### Post by DirtDawg on 2006-03-20
No, basic install should have been fine. 

To start Firefox, just type 'firefox' (without the quotes, of course) into the command line. I'm curious if it will work.

---

### Post by NeghVar on 2006-03-20
It sounds as if you did a server install maybe?

When it asked you what you wanted to install it said something like press enter for normal install, type server and enter for minimal install and F1 for other options.

---

### Post by DirtDawg on 2006-03-20
BTW, if you try to run Firefox and it acts like it's frozen after a minute or two, press CTRL+D to escape or, if that doesn't work, try CTRL+Z.

---

### Post by IYY on 2006-03-20
Clearly, this is a problem. You are supposed to get a full GUI after installation. You could try re-installing the entire system, or at least Gnome.

---

### Post by fenderlicious on 2006-03-20
Dirtdawg: I'll try that, I hope it works. I haven't set up a dial-up connection (obviously coulnd't yet) but I remember FF on windows and it's got that option inside the program.

NeghVar : I did the normal install, the only options were normal install or expert install, and I didn't want to possibly frack it up again by choosing expert, so I did normal.

IYY: Eh, I hope it doesn't come to that, but it might indeed.Where would I go for help if even THAT didn't work?

---

### Post by fenderlicious on 2006-03-21
Nothing helped, but I noticed a couple things:
whenever I log in, I get the blank desktop, but if I hold control-option and press F1 through F6, I get a different command-line that requires me to log in. tty1 - tty6. But, when I hold ctrl-opt and press F7 or F8, it takes me to the desktop (which is still blank, no matter what I do).
And when I type the name of any application into the command-line, I get an error message and returned to the line.

[I](____-bin:####): Gtk-WARNING **: cannot open display:
root@linux-tan:[/I]

---

### Post by nalmeth on 2006-03-21
Do you remember what password you set when you installed? If so, go to CNTL-ALT-F1, and type the following:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
``` 
You will be prompted for your user password. These commands will get your system up to date, and install the ubuntu-desktop which seems to be missing.
Hopefully we will figure out what came up short during install. A regular install should have provided you with the Gnome Desktop Environment (default GUI). Perhaps you have everything required, but the xserver is not configured properly. 

Let us know what you get from the above - post any negative output you might run into.

EDIT: > I haven't set up a dial-up connection (obviously coulnd't yet) but I remember FF on windows and it's got that option inside the program oops I didn't see this part. For updating installing you will need a net connection. Is dial-up all you have? I tend to assume everyone has highspeed.. My bad

---

### Post by fenderlicious on 2006-03-22
[QUOTE=nalmeth]Do you remember what password you set when you installed? If so, go to CNTL-ALT-F1, and type the following:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
``` 
You will be prompted for your user password. These commands will get your system up to date, and install the ubuntu-desktop which seems to be missing.
Hopefully we will figure out what came up short during install. A regular install should have provided you with the Gnome Desktop Environment (default GUI). Perhaps you have everything required, but the xserver is not configured properly. 

Let us know what you get from the above - post any negative output you might run into.

EDIT:  oops I didn't see this part. For updating installing you will need a net connection. Is dial-up all you have? I tend to assume everyone has highspeed.. My bad[/QUOTE]

Yeah, all I have available is dial-up, and not even that until I get this to work. I'll try the desktop install command, hopefully that works.

---

### Post by Snorri Kristjánsson on 2006-03-22
Well personaly I think you shuld strart over from scratch...  As you have not had chance to do anything anyway, I wonder is it worth the hassle to try to fix a bad install.  Strart fresh and see if you can get the brown gnome to work ;)

---

### Post by nalmeth on 2006-03-22
since you have no net connection, try to reconfigure the xserver like so:
sudo dpkg-reconfigure xserver-xorg
when you pick the video driver, pick the vesa driver, if it isn't selected on its own.

Did you ever get any error messages/output about X not being able to start? It's weird that you get the black screen and a mouse. Seeing as you have the mouse, it looks like x just isn't configured properly.

---

### Post by virgule on 2006-03-22
Just so you know.. 
F11 -> middle-click
F12 -> right-click

---

### Post by fenderlicious on 2006-03-23
[QUOTE=nalmeth]since you have no net connection, try to reconfigure the xserver like so:
sudo dpkg-reconfigure xserver-xorg
when you pick the video driver, pick the vesa driver, if it isn't selected on its own.

Did you ever get any error messages/output about X not being able to start? It's weird that you get the black screen and a mouse. Seeing as you have the mouse, it looks like x just isn't configured properly.[/QUOTE]

I'll try that, and if I get a return line I'll post it. But yeah, the few times I tried any X- commands it returned "Could not start X" and returned me to command. I really just need some way to do my email at home, yknow? Wasting an hour on travel just to check it is really getting to me.

---

### Post by nalmeth on 2006-03-23
> I really just need some way to do my email at home, yknow?
Yeah sounds like an easy expectation hey? Sometimes people just run into funny problems, but if you stick it out it will be well worth it.

For some info on your dialup connection read here:
[SIZE=-1][COLOR=#008000]https://wiki.ubuntu.com/DialupModemHowto[/COLOR][/SIZE]

---

### Post by fenderlicious on 2006-03-23
Allright, there's no "vesa" option for my xserver that I can see. the list of drivers for my video is as follows:
ati
chips
fbdev
glint
imstt
mga
nv
rival128
s3
s3virge
savage
sis
tdfx
trident
vga

There is a module list that has the word "vesa" in the explanation of what they are, but the two modules that vesa is dependent on are automatically selected every time I run through the reconfigure. And thanks for that link, I'm positive I'm going to need it if I can get linux working.

---

