---
title: "Fluxbox"
date: 2004-12-22
forum: Desktop Environments
---

### Post by thekore on 2004-12-22
Has anyone managed to successfully change there WM to fluxbox from the default gdm? i have managed to get it installed and running however whenever i try to customise fluxbox and make a new menu as apposed to the simple (xterm, restart, exit) menu it just doesnt pay attention?  ](*,) 

I have tried copying over the default sample menu... nothing
I have tried writing my own menu.... nothing
I have tried re-writing most of fluxbox but still..... nothing  :-k 

any ideas?  :-s

---

### Post by thekore on 2004-12-22
[QUOTE=thekore]Has anyone managed to successfully change there WM to fluxbox from the default gdm? i have managed to get it installed and running however whenever i try to customise fluxbox and make a new menu as apposed to the simple (xterm, restart, exit) menu it just doesnt pay attention?  ](*,) 

I have tried copying over the default sample menu... nothing
I have tried writing my own menu.... nothing
I have tried re-writing most of fluxbox but still..... nothing  :-k 

any ideas?  :-s[/QUOTE]
 i managed to get the issue fixed... it was a problem with the init file :)

---

### Post by ispmike on 2004-12-23
You can install 0.9.10 from here [http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/) and it'll automatically build the menu for you. 

My Ubuntu/Fluxbox [screenshot](http://home.comcast.net/~michael_dh/ubuntuflux2.jpg)

---

### Post by mr_pollock on 2004-12-29
[QUOTE=thekore]Has anyone managed to successfully change there WM to fluxbox from the default gdm? i have managed to get it installed and running however whenever i try to customise fluxbox and make a new menu as apposed to the simple (xterm, restart, exit) menu it just doesnt pay attention?  ](*,) 

I have tried copying over the default sample menu... nothing
I have tried writing my own menu.... nothing
I have tried re-writing most of fluxbox but still..... nothing  :-k 

any ideas?  :-s[/QUOTE]
 Could someone explain how to get Fluxbox installed at all?

---

### Post by hackerssidekick on 2005-01-04
[QUOTE=ispmike]You can install 0.9.10 from here [http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/) and it'll automatically build the menu for you. 

My Ubuntu/Fluxbox [screenshot](http://home.comcast.net/~michael_dh/ubuntuflux2.jpg)[/QUOTE]


Could you please tell me which style that is?

TIA

---

### Post by lilpac on 2005-01-23
[QUOTE=thekore]i managed to get the issue fixed... it was a problem with the init file :)[/QUOTE]

wich init?

---

### Post by MaTZ! on 2005-01-23
me too!
I'm using FluxBox but i have a problem with the file manager. I would like to create a menu like GNOME (computer->disk). What can i do?

mmm...
i try to explain me better!
i would insert in the menu (right click) called (for example win) that when i click on it it opens a new windows(in which display the contained into hd1).

Thanks.
And sorry for my Englisj!

---

### Post by rdking on 2005-02-06
Love your screenshot....just a couple of questions.  I'm new to flux, and so far like it's speed and simplicity. got my menus the way i want and set my backgrounds...google will give a lot of good help if you look.  Just a question.  Those icons and launchers shown in the bottom corner of the screenshot...how?  that is one thing I miss.  I downloaded the program for icon addition  off ubuntu repos, but can't for the life of me figure it out.  Do I have to hard code them like the menus and background?

thanks for your help in advance...I love ubuntu, it's community, and how it runs.  Will kep gnome cause it looks so polished, but like to try new and lightweight things

---

### Post by ladoga on 2005-02-06
[QUOTE=mr_pollock]Could someone explain how to get Fluxbox installed at all?[/QUOTE]


1. download fluxbox 0.9.11 from their site and compile as usual:
>./configure
>make
>make install

2. create file ".xsession" to your home folder and insert following line(s) to it
```
gnome-settings-daemon &
exec fluxbox
```
("gnome-settings-deamon &" is only necessary if you wish to use nautilus with gnome themes in fluxbox)

then you should be ready to go

---

### Post by QzarBaron on 2005-02-17
[QUOTE=ispmike]You can install 0.9.10 from here [http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/) and it'll automatically build the menu for you. 

My Ubuntu/Fluxbox [screenshot](http://home.comcast.net/~michael_dh/ubuntuflux2.jpg)[/QUOTE]

How do I install it from there? I can't get the package into Synaptic.

---

### Post by stilus on 2005-03-27
Sorry for this long post to an old thread, but maybe the details will help someone (I myself largely depend upon forums for things like this).

I would say the easiest way to install fluxbox in ubuntu is by apt-getting it (using synaptic, for instance). Then, just log out and change your session to fluxbox before you log back in. It will even ask you if you want to make fluxbox your default, or run it "just for this session". 
I've been fiddling around with it a bit, because I wanted some of the more nifty features of nautilus/gnome at my disposal: automount my usbstick, a theme that matched and some nice icons etc. 
In the end, this is what I did:

1) change your init file ( ~/.fluxbox/init ) to read:

```

session.keyFile:        ~/.fluxbox/keys
session.appsFile:       ~/.fluxbox/apps
session.menuFile:       ~/.fluxbox/menu

``` 
This means you can change these files to your liking, without the system overwriting it with defaults. (You might have to copy these things over from /usr/share/fluxbox/ or something, I'm not quite sure if they were there after the first login or not...)

in my ~/.fluxbox/apps it reads:
```

[startup] {gnome-settings-daemon}
[startup] {gnome-volume-manager}

```
The "~/.fluxbox/apps" file is used for a lot of things, but as the [startup] implies, it starts these applications at the fluxbox startup. 

This is where the finer things of a good desktop come in to play: it autmounts my usbstick through gnome-volume-manager, and pops up a nautilus window for me. That in turn looks good because I run gnome-settings-daemon at startup. 

As for the "~/.fluxbox/menu" file, I just used my editor of choice to change the menu to include some of the things I need the most: 
```

         [exec] (Nautilus) {nautilus --no-desktop ~/Desktop}
         [exec] (LyX (Qt\)) {/usr/bin/lyx-qt}
         [exec] (Pybliographic) {/usr/bin/pybliographic}
         [exec] (The GIMP) {/usr/bin/gimp-2.2}
         [exec] (YAFC) { x-terminal-emulator -T "Yet Another FTP Client" -e /usr/bin/yafc}
         [exec] (Gaim) {/usr/bin/gaim}
         [exec] (gmix (Mixer\)) {/usr/bin/gnome-volume-control}
         [exec] (Root Terminal) {gksudo gnome-terminal}
         [exec] (Synaptic) {gksudo /usr/sbin/synaptic}
         [exec] (Bluefish) {bluefish}
         [exec] (TSC) {/usr/bin/tsclient -f}

```
Then I wanted some hotkeys/ shortcuts, so I edited my "~/.fluxbox/keys" file to read: 
```

Mod1 F9  :ExecCommand gnome-terminal
Mod1 F10 :ExecCommand firefox
Mod1 F11 :ExecCommand lyx
Mod1 F12 :ExecCommand pybliographic

```
Whenever I press Alt+F11, I have one of the finer linux-applications in the known universe at my disposal. 

Next, I copied one of the default fluxbox styles/ themes (/usr/share/fluxbox/styles/Cthulhain ) to a ~/fluxbox/styles/ directory, funked it up a bit with a nice background using **feh **:
(it reads *rootCommand:                            feh --bg-center /usr/share/wallpapers/vettii.png* )

It's not perfect, but I call it ~/  ;-) 
The [result](http://avuko.cheeseheadz.net/ubuntuscreenshot.png)

I hope this might be of use to someone. Have fun with Ubuntu! :-)

---

### Post by roffles on 2005-04-08
(caveat: not a guru by any means)

Initially when I installed fluxbox I found changes weren't being saved. So what I wound up doing was installing fluxconf, I ran it as root to change the directory where the profiles are saved to my home directory, then restarted fluxbox. Now I am able to save changed without being root user.

-long story short, the default directory where fluxbox stores everything can only be written to by root :) Don't know if this will help anyone.

---

### Post by Mikebgr on 2006-04-30
stilus thank you for the extended info, i might as well give fluxbox a try myself now :)

---

