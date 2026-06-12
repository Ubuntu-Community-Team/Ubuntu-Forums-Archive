---
title: "new updates caused wireless to go away"
date: 2007-12-21
forum: Dell  Ubuntu Support
---

### Post by DouglasAWh on 2007-12-21
I know everyone's updates are different, because they have different stuff installed, but the latest round of updates caused my wireless card not to be recognized.  Are there any known issues with recent auto-updates?

Thanks!

---

### Post by natehall on 2007-12-21
I had that problem with my 1420N. The first time I was so concerned I rebooted the system! Later on I discovered a workaround:  I would click a fictional set-up in the Network manager, wait for the network reconfigure window to pop up and finish out, then change it back to my setup,(Wait  again for the reconfigure,) It works. It still used to drop out occasionaly. Time will tell if the Gutsy Factory DVD I just reinstalled will solve this permanantly.

---

### Post by DouglasAWh on 2007-12-21
> **natehall said:**
>   I would click a fictional set-up in the Network manager, wait for the network reconfigure window to pop up and finish out, then change it back to my setup,(Wait  again for the reconfigure,) 

I have no idea what you mean by this.  What am I supposed to set up?  When I click on the network manager I see Wired Network and manual configuration.  If I click on manual configuration the wireless card doesn't show up.

---

### Post by natehall on 2007-12-21
System>Administration>Network.  Password window pops up, After entering your log in password  you should get a window called "Network Settings" That's the window I'm talking about.  I only use Wireless for my laptop so I click off the wirless connection and click on the wired connection ( The fictional set-up) A lttle window pops up and says "Reconfiguring network" (Or something like that) Then after that window  goes away I click off the wired connection and click on the wireless connnection. The "Reconfiguring Network window pops up once more and after that's done Firefox works again. ( If you have never seen the Network Settings window before click on properties to set it up)

---

### Post by DouglasAWh on 2007-12-21
Right, this is what I was talking about before.  When I go to the screen you mention, my wireless does not show up.  Thus, I cannot click and unclick the wireless.  I just access it through an icon on the top GNOME bar.  Thanks for trying though.

---

### Post by natehall on 2007-12-21
> **DouglasAWh said:**
> Right, this is what I was talking about before.  When I go to the screen you mention, my wireless does not show up.  Thus, I cannot click and unclick the wireless.  I just access it through an icon on the top GNOME bar.  Thanks for trying though.
It could be specific to my computer perhaps. It's a Linux Preloaded Dell 
1420. From what I've been reading on wireless its a tough cookie to make work on Linux because manufactures keep the necessary code to themselves. The usual workaround is something that mimics windows sytems (nsiwrapper)

---

### Post by natehall on 2007-12-21
This link might help;[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by DouglasAWh on 2007-12-21
> **natehall said:**
> This link might help;[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

Cool.  I'll have to burn myself a Gutsy CD as all I've got here is Feisty.

As to Linux wireless.  It's worked on this laptop since June when I got it, but stopped working today after updates...grrr.  I'll post again after I've tried the thread you gave me.

---

### Post by DouglasAWh on 2007-12-21
One of my friends just told me on chat while I was away:

"likely it was the new version of linux-restricted-modules
  get the version one rev back"

anyone want to help me with that?

Thanks!

EDIT: I found out my history:

This is what appears to have been updated today:

findutils (4.2.31-1ubuntu2) to 4.2.31-1ubuntu2.1
libmysqlclient15off (5.0.45-1ubuntu3) to 5.0.45-1ubuntu3.1
libsmbclient (3.0.26a-1ubuntu2.2) to 3.0.26a-1ubuntu2.3
linux-headers-2.6.22-14 (2.6.22-14.46) to 2.6.22-14.47
linux-headers-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
linux-image-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
linux-image-2.6.22-14-rt (2.6.22-14.46) to 2.6.22-14.47
mysql-common (5.0.45-1ubuntu3) to 5.0.45-1ubuntu3.1
samba-common (3.0.26a-1ubuntu2.2) to 3.0.26a-1ubuntu2.3
smbclient (3.0.26a-1ubuntu2.2) to 3.0.26a-1ubuntu2.3
wesnoth (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-all (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-data (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-editor (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-ei (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-httt (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-music (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-trow (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-tsg (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-ttb (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-utbs (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1

Commit Log for Fri Dec 21 12:20:59 2007
Upgraded the following packages:
linux-headers-2.6.22-14 (2.6.22-14.46) to 2.6.22-14.47
wesnoth (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-all (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-data (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-editor (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-ei (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-httt (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-music (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-trow (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-tsg (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-ttb (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1
wesnoth-utbs (1.2.6-1ubuntu2.2) to 1:1.2.8-1~feisty1

looks like my friends suggestion was incorrect.

---

### Post by natehall on 2007-12-22
When I first got my 1420N the screensaver didn't work (3d graphic driver problem) The updates fixed it but made firefox stop downloading. So I tweaked around with the updates to see what fixed  things and what hurt them. Seems like I started getting the dropout problems and a real long boot load time after doing the linux kernel updates. Now that I've done the factory Gutsy DVD fresh install its been good.

---

### Post by DouglasAWh on 2007-12-23
Here's some info that might help someone help me:

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I have Internet access for a short period, so if someone could help me soon, that would be awesome.  THANKS!

---

### Post by jan quark on 2007-12-27
Hi I just wanted to say that I have the same problem.:)

Have a Inspiron 1505. Now I have done a fresh install of Xubuntu Gutsy and have updated NOTHING. The Internet works. But in the past I was so curious to see if my problem was really linked with the updates that I had to reinstall Ubuntu it seems a hundred times. 

Now I am posting from the dell lappy. But not to have the update enabled is not an elagant solution, isn't it?

---

### Post by trooperchix on 2007-12-27
> **DouglasAWh said:**
> Right, this is what I was talking about before.  When I go to the screen you mention, my wireless does not show up.  Thus, I cannot click and unclick the wireless.  I just access it through an icon on the top GNOME bar.  Thanks for trying though.

I had the same problem, and I have the Dell 1420N.  You are going to kick yourself.  On the 1420N there is a switch on the front of the laptop in the right side.  There's a switch and then the little port for photo media cards.  That switch next to the media slot (to the right of it), it enables / disables your wifi card.  Push it to the left your wifi card is disabled.  Push it to the right and.. presto, your wifi wireless network location will show in your network settings window.  

Hope this helps!!

:popcorn:

---

### Post by DouglasAWh on 2007-12-27
> **trooperchix said:**
> I had the same problem, and I have the Dell 1420N.  You are going to kick yourself.  On the 1420N there is a switch on the front of the laptop in the right side.  There's a switch and then the little port for photo media cards.  That switch next to the media slot (to the right of it), it enables / disables your wifi card.  Push it to the left your wifi card is disabled.  Push it to the right and.. presto, your wifi wireless network location will show in your network settings window.  

Hope this helps!!

:popcorn:

my wireless works when I boot to a LiveCD or boot up to another kernel, so that's not the problem.  Thanks though.  On the 1505, it's Fn F2 though, for anyone else who is having that problem.

And, while I'm writing, I've since downgraded (the below is just copied from the original "upgrade")

libsmbclient (3.0.26a-1ubuntu2.2) to 3.0.26a-1ubuntu2.3
linux-headers-2.6.22-14 (2.6.22-14.46) to 2.6.22-14.47
linux-headers-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
linux-image-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47

What else should I downgrade?  This is very frustrating!!

---

### Post by DouglasAWh on 2007-12-27
Somewhere in all of that downgrading and upgrading my menu.lst decided to change the defualt to zero (-rt) rather than whatever it was when -generic kernel was the default.  I'm not sure which of the four downgrades fixed the problem and at the moment I don't much care, but for those that had problems after the upgrades, try 


libsmbclient
linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-image-2.6.22-14-generic

One of these I'll try reinstalling the others...or just wait until the next round of upgrades.  I've wasted quite enough time on this already!

---

