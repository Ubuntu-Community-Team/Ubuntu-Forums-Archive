---
title: "Xfce is good, now what to delete?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by SirThom on 2008-06-07
I've played around with both gnome and KDE before Xfce, and I have decided to stick with Xfce.  Now it looks like the gnome and KDE helpers used for running apps designed for those environments.  So, if I want to get rid of gnome and KDE (to have HD space), how do I do that, and how do I do that without breaking anything?

---

### Post by sisco311 on 2008-06-07
Type:
```
sudo tasksel
```in the terminal and make sure *Ubuntu Desktop* and *Kubuntu Desktop* is not selected.

---

### Post by SirThom on 2008-06-07
OK, thanks.  I also installed some of the A/V packages which should make my editing of videos easier.

<edit>Actually, now I'm getting 'tasksel: aptitude failed (100)'.  I'm searching google for that and not finding any solutions . . .</edit>

---

### Post by sisco311 on 2008-06-07
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by SirThom on 2008-06-07
Following the first instructions but trying again without installing new software, but only removing Kubuntu and ubuntu desktops, it proceeded to delete pretty much all of my majour software.  When I tried rebooting then I could only go into the command line.  I am now running off the ubuntu gutsy boot disk to download the xubuntu boot disk (I hope it lets me take the boot disk out to burn the new CD) :-/

---

### Post by molotov00 on 2008-06-07
You can do a lot from the command line. You can install xubuntu by doing: sudo apt-get install xubuntu-desktop, I believe.

Sorry that you removed the major apps. Xubuntu does not come with OpenOffice and others. It's a light desktop. Many apps are a part of the Kubuntu and Ubuntu installs.

If I were you, I would NOT use the CD as you are, because then you will need to redownload the packages such as OpenOffice and other major apps. I'd install XUbuntu (as above) and then install the individual programs you want. The packages have not been deleted from your drive so apt-get won't need to redownload them. This will be the fastest way to get back up.

M

---

### Post by SirThom on 2008-06-07
OK, I'll try that.  the CD image is 2 minutes away from downloading so I will let it finish in case.
Mainly what I wanted to do is that I had the system running more or less as I liked it and I just wanted to delete whatever additional files that I would never use again linked to ubuntu ant kubuntu, like the windowing environment itself.
I'll be back with updates.

---

### Post by SirThom on 2008-06-07
That didn't work, it wants to download the software, and for some reason even though I am jacked into the network directly it's not finding that.  I can't get the extra external plextor drive that I have to be recognized by ubuntu when i boot from the liveCD, and when i try to pop out the liveCD to burn my image to it (with eject -r in terminal) it doesn't recognise that I have popped in a new blank CD.
Sooo, I am doing a quick and dirty install of gutsy on my HD so that i can burn my xubuntu and then install that.
I'm also going to take this external hard drive, which I did have set up as an emergency WinXP boot disc (and never really used) but suddenly stopped being booted off of, put on a xubuntu set up for my system, and make another partition for storing large files.

---

