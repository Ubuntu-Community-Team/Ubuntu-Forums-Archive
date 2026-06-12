---
title: "Slideshow Desktop is GNOME?"
date: 2004-10-31
forum: Desktop Environments
---

### Post by Faramirtook on 2004-10-31
How do I get my desktop to do a slideshow in GNOME? I know I can do it in KDE, but I like GNOME much better.

---

### Post by markw on 2004-10-31
Applications>Graphics>Gthumb Image Viewer and the browse to the folder with the images on the left and click slideshow on the toolbar. :D

---

### Post by Faramirtook on 2004-10-31
No, no, I mean have my deskop rotate between a bunch of pictures.

---

### Post by Faramirtook on 2004-11-01
bump

---

### Post by Faramirtook on 2004-11-01
[QUOTE=Faramirtook]No, no, I mean have my deskop rotate between a bunch of pictures.[/QUOTE]
 Anyone?

---

### Post by Razvan on 2004-11-01
do you mean like in MacOSX - where the desktop background changes from timt to time to another pic when you want?

shure...that'd be cool...didn't even know you can do that in kde :-)

---

### Post by fng on 2004-11-02
mail it to a gnome developer for 2.10 :)

---

### Post by gamehack on 2004-11-02
Hey :P
> About Gnome Desktop Change	  Gnome Desktop Change is a daemon that changes randomly your GNOME desktop background. 

[http://www.gnomefiles.org/app.php?soft_id=510](http://www.gnomefiles.org/app.php?soft_id=510)

Cheers,
gamehack

---

### Post by Faramirtook on 2004-11-03
[QUOTE=gamehack]Hey :P
 

[http://www.gnomefiles.org/app.php?soft_id=510](http://www.gnomefiles.org/app.php?soft_id=510)

Cheers,
gamehack[/QUOTE]


Thanks alot, dude.

---

### Post by clasqm on 2004-11-25
BTW, don't bother trying chbg - it doesn't work in ubuntu. Believe me I've tried.

---

### Post by mr_ed on 2004-11-25
[QUOTE=clasqm]BTW, don't bother trying chbg - it doesn't work in ubuntu. Believe me I've tried.[/QUOTE]
 I believe this is because KDE and GNOME have their own backgrounds (try changing your background to something else, and then restart X, and when GNOME gets fully loaded, you'll see the background change from Ubuntu brown to what you selected).

I believe that chbg only changes the X root background and not the GNOME background.

---

### Post by piedamaro on 2004-11-25
You can use various scripts you can find on gnome hacks site. They use gconftool to change the background. There is also a plugin for gkrellm which does the same.

---

### Post by clasqm on 2004-11-26
[QUOTE=gamehack]Hey :P
[http://www.gnomefiles.org/app.php?soft_id=510](http://www.gnomefiles.org/app.php?soft_id=510)
Cheers,
gamehack[/QUOTE]

Hmm, after downloading about half the dev packages available :lol:  I got it to ./configure, but it won't make. Has anybody succeeded in compiling this on warty? I was hoping to do a checkinstall and make a deb that way.

---

### Post by piedamaro on 2004-11-26
Uh? It uses fam which is deprecated (it isn't in hoary by default).
You can do everything without a daemon, with a simple script.

---

### Post by clasqm on 2004-11-26
[QUOTE=piedamaro]Uh? It uses fam which is deprecated (it isn't in hoary by default).
You can do everything without a daemon, with a simple script.[/QUOTE]
That's right, I had to d/l and install libfam-dev to get ./configure to work (and also xlibs-dev). But "make" just stops at a certain stage. (sorry, didn't keep the output)

I'll try the gnome-hacks scripts next, thanks

---

### Post by clasqm on 2004-11-26
Well, none of the scripts on gnome-hacks worked right away, but they pointed in the right direction: here is my version, it works flawlessly on my warty box:

```
#!/bin/sh

#Name: ranwp.sh
#Function: Wallpaper randomiser
#Adapted for Ubuntu Warty from suggestions 
#found on http://gnome-hacks.jodrell.net/
#License: Public Domain

#Instructions: Place this script in a /bin directory
#and do a chmod +x <filename> on it.
#Then put it in a crontab or with your startup programs.
#Or both. Ubuntu Warty doesn't have a crontab editor, 
#but you can install gcrontab via synaptic.

cd /usr/share/backgrounds
#Change this location if you keep your backgrounds elsewhere.
#Just one location allowed, sorry

IMGS=`find . -iname '*.jpg' -o -iname '*.png' -o -iname '*.svg'`
#You may want to get rid of the tiger head in 
#/usr/share/backgrounds/scalable, in fact, blow
#that directory away!

N=`echo $IMGS | wc -w`
#Find out how many pictures we got

((N=RANDOM%N))
#Take a random number between 1 and N

BGNAME=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`
#We have to cut twice to get rid of an irritating " ." at the 
#end after the first cut

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/$BGNAME"
# end of gconftool command

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
#Possible values are "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched"
# end of gconftool command


#That's it, your background should have changed.
```

Thanks to all concerned for the tips and links

---

### Post by jdong on 2004-11-27
Awesome. Now, if someone would like to do a writeup on this solution for the HOWTO forum, that'd be GREAT.

---

### Post by Razvan on 2005-01-26
no, it doesnt quite work for me...it doesnt print anything, it just executes and nothing changes...

i tried debugging it and ran all the commands in a shell and it seems to me the thing with the random doesnt quite work out...it always returned 0...

---

### Post by piedamaro on 2005-01-26
Now if someone amend the script at gnome-hacks to mount iso images, I will be a happy guy:D
(I've worked on it to make it use gksudo under ubuntu, but it works until there are no spaces in your filenames...too bad :()

---

### Post by xaet on 2005-09-21
Here are my modifications, it works for me. I wish it works for you.

[QUOTE=clasqm]Well, none of the scripts on gnome-hacks worked right away, but they pointed in the right direction: here is my version, it works flawlessly on my warty box:

```
#!/bin/sh

#Name: ranwp.sh
#Function: Wallpaper randomiser
#Adapted for Ubuntu Warty from suggestions 
#found on http://gnome-hacks.jodrell.net/
#License: Public Domain

#Instructions: Place this script in a /bin directory
#and do a chmod +x <filename> on it.
#Then put it in a crontab or with your startup programs.
#Or both. Ubuntu Warty doesn't have a crontab editor, 
#but you can install gcrontab via synaptic.

cd /usr/share/backgrounds
#Change this location if you keep your backgrounds elsewhere.
#Just one location allowed, sorry

IMGS=`find . -iname '*.jpg' -o -iname '*.png' -o -iname '*.svg'`
#You may want to get rid of the tiger head in 
#/usr/share/backgrounds/scalable, in fact, blow
#that directory away!

N=`echo $IMGS | wc -w`
#Find out how many pictures we got

[COLOR=Green]#[/COLOR]((N=RANDOM%N))
#Take a random number between 1 and N
[COLOR=Green]#That take a number between 0 and N-1. We must to add 1.
((N=(RANDOM%N)+1))[/COLOR]


[COLOR=Green]#[/COLOR]BGNAME=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`
#We have to cut twice to get rid of an irritating " ." at the 
#end after the first cut

[COLOR=Green]#The above code returns error at first element because it is a dot alone.
#And never selects the last one.
#I think this one works correctly.
BGNAME=`echo -e $IMGS | sed s@\./@@g | cut -d ' ' -f $N`
[/COLOR]
# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/$BGNAME"
# end of gconftool command

# start of gconftool command - all on one line!
gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
#Possible values are "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched"
# end of gconftool command


#That's it, your background should have changed.
```

Thanks to all concerned for the tips and links[/QUOTE]

---

### Post by Mustard on 2005-09-21
Would this work in Hoary Hedgehog?

---

### Post by rpkehoe on 2007-11-17
In case anyone doesn't have this yet:
[http://wallpapoz.akbarhome.com]("http://wallpapoz.akbarhome.com")

---

