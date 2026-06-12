---
title: "How to change the background color behind the startup splash"
date: 2005-01-28
forum: Desktop Environments
---

### Post by WirelessMike on 2005-01-28
I've searched unsuccessfully for the answer to this for 2 days.  I thought I came close when I saw mention of it for gnome on linuxquestions.org, but while the answer there may have been good for Red Hat, it was useless for Ubuntu.

Before there are 4 or 5 posts on how to change the splash--  I know how to change the splash.  I know what directory the splash screens are in and I know how to use the configuration editor to tweak it.  I DON'T know how to change the color of the background behind it from that default chocolate color (#4A3C29, I think).

Here's the solution proposed on LQ.org I mentioned earlier:

> Posted by Requestor:

First of all, this is GNOME. But I did go into GNOME's login properties and change the background for the standard greeter (Note: I am using graphical greeter) to black. Still, when I reboot, the colour behind the spash screen is that blue.


Reply:

Woohooo!
Just figured this out.
The hex for that awful blue that you see is #5477A0. I did a 'grep -r 5477A0 /etc/X11/*' and found that hex in 3 different files.
/etc/X11/gdm/Init/Default:/usr/X11R6/bin/xsetroot -solid "#5477A0"
/etc/X11/xdm/Xsession:xsetroot -solid '#5477A0'
/etc/X11/xdm/Xsetup_0:/usr/X11R6/bin/xsetroot -solid "#5477A0"

Actually that Default one in the gdm directory is a symlink to the Xsetup_0. So its only two files.
change the 'xsetroot -solid' line to whatever color you want, logout and login. Watch your new color flash breifly before your eyes.

BTW I'm still using RH8.0. So if these files don't exist on Rh9 or FC1 you might try that grep line again. Unless they changed that blue in later versions.

As I mentioned, this does not work for Ubuntu Hoary.

Any Suggestions?

---

### Post by WirelessMike on 2005-01-28
OK--  I finally figured this out using a similar approach with grep.  Perhaps this can be moved into the "HOW-TO" category if I can get confirmation from another user or 2 that it works across Ubuntu releases (it definitely works in Hoary).

I used the following command to find the original chocolate background color--

grep -r 4E3E29 /etc/gdm/*

That will tell you that the color is found as "BackgroundColor" in the following files--

/etc/gdm/factory-gdm.conf
/etc/gdm/gdm.conf
/etc/gdm/gdm.conf.dpkg-dist

Simply vi into these files as root, page down until you get into the greeter section where you'll find "BackgroundColor=#4E3E29"  Change this to the desired color (I wanted a dark blue, so i changed it to #000045) and viola!

Now you can choose a background color to compliment your custom splash!

 :mrgreen:

---

### Post by WirelessMike on 2005-01-28
xsos gave an even easier solution.  I included it as a reply to this in the HOW-TO section.

---

### Post by Iamiko on 2008-01-13
Sorry to resurrect an old thread but I felt this was worth posting.

I was scratching my head about how to do this for a good fortnight and when I finally couldn't work it out for myself I headed for google, which in turn brought me to this thread.

I tried the method that WirelessMike posted above but it didn't work for me. This might be due to the fact that I run Compiz Fusion and Emerald but I cannot be certain as all my Ubuntu machines are set up the same way. I'm running Ubuntu 7.10 and fully updated too.

The way I had to do it was as follows:
```
grep -r /etc/gdm/*
```
This showed me an extra file to what WirelessMike found... /etc/gdm/PreSession/Default

I first tried the files that WirelessMike mentioned (after making a copy of each file) and that didn't work so I changed the setting in the new file and it worked. I sudo'd to the file with nano (I'm too rookie to know how to use Vi >.>)  and changed the following value....
```
BACKCOLOR="#dab082"
```
to
```
BACKCOLOR="#000000"
```

This worked for me and it hasn't broken anything YET (been running like this for 2 days now) on either of my Ubuntu machines.

Hope this helps and sorry for the post necro but as it was something that had me confused as a new linux user, I felt it was worth posting as this thread comes up in the top 5 on the google search terms i used.

*Edit: Quick edit to say thanks to WrelessMike for having posted this info in the first place, I would still be scratching my head without it.*

---

### Post by bugler on 2008-02-03
I wanted to confirm lamiko's post.  This worked for me of Gutsy Ubuntu.  I would like to add that I am using startup manager (SUM) and Usplash.  I have set the background color by *System|Administration|Login Window* select Local Tab and choose background color of black.  This did nothing and the default chocolate color remained under the splash screen.

In a nutshell follow lamiko's info and it works.  However, I would love to find out why it login window does not change the backcolor in presession.  If anybody has any info, please PM me and post as well.

Thanks

---

### Post by WirelessMike on 2008-02-04
Excellent Update, Iamiko!  I'm using Gutsy, now, too, and can confirm your method works!

:popcorn:

---

