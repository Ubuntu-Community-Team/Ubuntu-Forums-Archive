---
title: "Hey... XGL woes. ;_;"
date: 2006-09-19
forum: Desktop Environments
---

### Post by SpencerStarnes on 2006-09-19
(its my first week of Dapper.)

Hey, I decided to install and try XGL + compiz.
it ran pretty smoothly, and after a few mins (after opening Gaim, or FF) X just restarts. seemingly randomly. 

So, I decided to go into Gnome safe mode, and go to the package mangager thing. and I uninstall XGL (Not compiz) so... now. it just goes for a few seconds. and then restarts gnome agian. So, I can only use my computer when in gnome safe mode. 

How do I fix these problems without reinstalling 6.06 all together. 

I've done alot of work to get my Harddrives mounted, and to get all the software installed. (automatix etc.)

I really liked XGL. I would still like to use it. 

(also, I cant figure out how to get a widescreen ressolutions (16:10) on my VGA monitor :-\..

some help would be great!
thanks.
spencer

---

### Post by Gun_Smoke on 2006-09-19
By any chance were you typing when it quit?

---

### Post by Dinerty on 2006-09-19
Are you nvidia or ati?, what guide did you use to install xgl/compiz?

---

### Post by bulldog on 2006-09-19
Have you some kind of a startup script in your sessions menu?

Like compiz-start,thefuture,compiz-start.py or /usr/bin/compiz-start.

If so remove it and compiz will not start.

Can you tell me what you have done to install Xgl/compiz or give me the link to the HowTo.

There are several things changed which maybe not updated in your tutorial.

To change your resolution take a look in your /etc/X11/xorg.conf.
Is the desired resolution in the list?

If you gonna alter your xorg.conf make a backup first!!

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

---

### Post by SpencerStarnes on 2006-09-19
yes i was typing when it restarted
i am on an nvidia 5200

[http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/](http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/) 
I used this guide.

I have my nvidia drivers installed through automatix

Thanks for the help guys! 

This is my only OS at the moment.

---

### Post by Gun_Smoke on 2006-09-19
See if Shift+Backspace restarts X for you.. I had that happening for a while.. I don't remember what we did to correct it.. And now I've just been more careful with with my fingers.

---

### Post by SpencerStarnes on 2006-09-19
now it just does it on its own. when im not in safe mode :-\

---

### Post by bulldog on 2006-09-19
Hmmm,it's an older and very limited howto..........
Take a look at this and try it again.

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

---

### Post by SpencerStarnes on 2006-09-19
Thanks guys.
I havn't gotten the chance to try these yet, but im sure they will work. 

I have a few questions for ya guys.

So, does XGL + compiz work with 16:10?
Whats the difference between XGL and compiz?
When I was using Compiz and XGL, I would "Throw" a window. and it would really bog up my sistem, are they any quality settings?

by the way. my hardware.
AMD (Althon?) 3000+
Nvida 5200 (somehting)
i have 1.5 gigs of ram.
1 200 gig harddrive
1 80
and 1 120 Gig SATA drive 

i also have an Envision 19 inch widescreen monitor. 

:-D thanks for all the help guys *hug*

---

