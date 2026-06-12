---
title: "GNOME to KDE switch problems"
date: 2005-11-28
forum: Desktop Environments
---

### Post by mfarquhar on 2005-11-28
i recently tried to switch from Ubuntu to kubuntu by installing the 
Kubuntu-Desktop metapackage through aptitude (its a text only package manager)
long story short it didn't work. there was no GUI :( 
then i tried to "upgrade" from a kubuntu install disk (breezy)
it says it upgraded to ubuntu breezy release and still no GUI :( 

i would really like to switch to KDE

help the poor n00b pleeze :???:

---

### Post by kingsidy on 2005-11-28
in order to use kde you have to select kde session from the login screen and make it your default. So when you boot, at the login screen, you'll see session, click it and you should see kde. Select it. It will then ask you whether you want to make kde your default session. Click yes then enter your usuername and password. and the WM should be KDE.
I use XFCE and Gnome alternatively and that is how i do it.

---

### Post by mfarquhar on 2005-11-28
my problem is a little more severe. there is no login screen
at least not a graphical one

it's text only. and i don't really know how to do all that much from a terminal

---

### Post by JShadow on 2005-11-28
There may be video problems then that is preventing your X from starting. What kind of video card do you have?

---

### Post by mfarquhar on 2005-11-28
My setup is as follows

Emachine: Emonster

Pentium III 600 MHz
8 MB NVidia 128-bit TNT2
20 Gb HD / 10 for ubuntu, 10 for windows
190ish MB RAM
100MHz system bus

(i know it sucks but it was "The Best Gaming Machine" 6 years ago):mad: 

but i dont think video is the problem because it worked fine for several month's. i also had this problem with one or two Warty edition computers when i tried to upgrade them to Hoary at school (they were HP Vectra's with Pentium II's)

---

### Post by JShadow on 2005-11-29
Ok well the first thing to do would be to try and start x when you log in. After your text login typing "startx" and pressing enter should get you into KDE.

If this doesn't work then look for errors on the screen, otherwise try "less /var/log/Xorg.0.log" and look for any error messages. That should give us a little more idea of whats wrong.

---

### Post by mfarquhar on 2005-11-30
This is the error message i get when i try to startx :mad: 

mfarquhar@ubuntu:~$ startx
xauth: creating new authority file /home/mfarquhar/.serverauth.5722
xauth: error in locking authority file /home/mfarquhar/.Xautority
xauth: error in locking authority file /home/mfarquhar/.Xautority
xauth: error in locking authority file /home/mfarquhar/.Xautority
xauth: error in locking authority file /home/mfarquhar/.Xautority

/etc/X11/xinit/xserverrc: line 2: /usr/bin/X11/X: No such file or directory
/etc/X11/xinit/xserverrc: line 2: exec: /usr/bin/X11/X: Cannot execute: no such file or directory
giving up.
xinit: connection refused (errno 111): unable to connect to X server
xinit: no such process (errno 3): server error.
xauth: error in locking authority file /home/mfarquhar/.Xautority

---

### Post by f1dave on 2005-11-30
how.... strange.

To me, it looks like it thinks X is not installed... Can someone confirm this for me?

---

### Post by kingsidy on 2005-12-01
I have had that error a while back. What i did is that i deleted the .Xauthority from the command line. then typed startx.

do this:

rm /home/mfarquhar/.Xautority
then as a regular use type in : startx

---

### Post by mfarquhar on 2005-12-01
i did the remove thing and now the new error message is this

mfarquhar@ubuntu:~$ startx
xauth: creating new authority file /home/mfarquhar/.serverauth.5627
xauth: creating new authority file /home/mfarquhar/.Xauthority
xauth: creating new authority file /home/mfarquhar/.Xauthority

/etc/X11/xinit/xserverrc: line 2: /usr/bin/X11/X: No such file or directory
/etc/X11/xinit/xserverrc: line 2: exec: /usr/bin/X11/X: Cannot execute: no such file or directory
giving up.
xinit: connection refused (errno 111): unable to connect to X server
xinit: no such process (errno 3): server error.

](*,)

---

### Post by GeneralZod on 2005-12-02
Try

```

sudo X -version

```

and

```

dpkg --list | grep xorg

```

and for the latter, ensure that xserver-xorg and xserver-xorg-core are present.

As f1dave noted, it looks like you don't have X installed, for some reason.

---

### Post by mfarquhar on 2005-12-03
I installed xserver-xorg-core

then after startx attempt (the window flickers like it’s trying to start then gives this:

__________
Fatal server error:
Could not open defaul font ‘fixed’;
The X server’s font paths might be misconfigured, remote font server9s) may be unreachable, and/or local fonts may not b installed opr are not configured correctly

People inexperienced with the X Window System should have either the “x-window-system” or the “x-window-system-core”

________________________
Then it goes on talking about commands to run to install the two aforementioned packages, and something about the X org site.

at the end there is this:
__________________
XIO: 	fatal IO error 104 (connection rest by peer) on X server “:0.0”
	After 0 request (0 known processed) with 0 events remaining.
___________________

like the n00b i am i installed "x-window-system-core" and got the same results

on the plus side at least i'm making progress;)

---

### Post by mfarquhar on 2005-12-05
[QUOTE=mfarquhar]
Fatal server error:
Could not open defaul font ‘fixed’;
The X server’s font paths might be misconfigured, remote font server(s) may be unreachable, and/or local fonts may not b installed opr are not configured correctly
[/QUOTE]

how do i get these fonts
will they be on the install CD

---

### Post by kingsidy on 2005-12-07
after u delete it create a new file in the same place and copy and paster the name (.Xauthority)

---

### Post by mfarquhar on 2005-12-07
[QUOTE=kingsidy]after u delete it create a new file in the same place and copy and paster the name (.Xauthority)[/QUOTE]

:-s what does that mean? how do i do it? i can remove the .Xauthority file, but i don't know how to create files from terminal.:-k 

i removed the file as per your previous instructions but now i still get the Font error.](*,)

---

### Post by features on 2005-12-12
I **think** what the problem is here is that aptitude has uninstalled gdm for you.  Nice of it to do that.  If that is the case you can:

```
sudo apt-get install ubuntu-desktop kubuntu-desktop
```
to get it going again.  You can do this from the command line no worries.  Please type that command as it is above.  Don't use aptitude for this, as it makes some arbitrary decisions about which packages you want and don't want.

Chear,

Mark

---

### Post by mfarquhar on 2005-12-14
update time:

okay i udated a few font packages and X works \\:D/ 
but now all i get is that grey screen with a X for a cursor :-k

---

### Post by mfarquhar on 2005-12-15
i just found out that i cant do anything

i can't switch to terminal via <ctrl>+<alt>+<f1-6>
i cant shutdown
and i don't get a menu when i right click
the system won't reboot with a <ctrl>+<alt>+<delete>

---

### Post by mfarquhar on 2005-12-15
[QUOTE=mfarquhar]i just found out that i cant do anything

i can't switch to terminal via <ctrl>+<alt>+<f1-6>
i cant shutdown
and i don't get a menu when i right click
the system won't reboot with a <ctrl>+<alt>+<delete>[/QUOTE]

after leaving it unfuntionaly on for 3 days i did a HARD reboot ( i pulled the power pluG0 and when it booted up it loaded a kde login prompt splash thing
i logged in
anxd have the SAME PROBLEM as before except now i have a nice blue screen with KUBUNTU in the corner:evil:

---

### Post by sav2005 on 2005-12-16
I don't know if it will work :( , but try 

[INDENT]"sudo dpkg-reconfigure kubuntu-desktop" [/INDENT]

I installed kubuntu-desktop via apt and I was prompted for the display manager I wanted to use - kdm or gdm.

---

### Post by mfarquhar on 2005-12-17
IT'S ALIVE!!!!\\:D/ 

i tried what you told me (reconfigure kubuntu-desktop) and when it told me that the package was invalid and wasn't installed i looked in aptitude to find it and reinstalled all the unsatisfied dependencies rebooted and it works. KDE loads. HOORAY!

i have some minor concerns though
because when i checked back at aptitude about 6 packages were still unsatified such as K3B and some pcmcia and bluetooth packages (there are undoubtedly others but i can't remember them right now

so thanks for all the help everybody:D , will check back if i have further problems:)

ps. how do i change the thread title to say it's solved?

---

### Post by mfarquhar on 2005-12-24
i recently installed Kubuntu-desktop on another computer (the right way)
and foun out that the reason i had all this trouble was that i never had "Upgraded the distribution" i had typed in 
$apt-get upgrade
not
$apt-get dist-upgrade
so all packages were upgraded therefor causing havoc witht the system

this time around i had no problems (i used synaptic this time. BAD APTITUDE BAD APT-GET. BAAAAAD);) 
i upgraded to 5.10 breezy first then installed kubuntu-desktop
everything works great. hooray

---

### Post by angrykeyboarder on 2005-12-29
[quote=mfarquhar]My setup is as follows

Emachine: Emonster

Pentium III 600 MHz
8 MB NVidia 128-bit TNT2
20 Gb HD / 10 for ubuntu, 10 for windows
190ish MB RAM
100MHz system bus[/quote] 
No wonder you're having problems. ;-)

Forget KDE (or GNOME).   Think XFCE or Fluxbox.  You're computer will be very very slow but it won't completly crawl.

Better yet, go out and buy the cheapest low-end (but new) Video card you can find. 

Whatever it is, it wil be 10X better than what you have now.

Oh and add as much RAM as possible.  In a box that old, I'm guessing you could up to 512 or 768 MB.

---

