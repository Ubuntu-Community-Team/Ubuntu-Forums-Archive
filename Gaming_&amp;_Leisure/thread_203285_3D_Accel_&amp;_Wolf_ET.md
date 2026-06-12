---
title: "3D Accel &amp; Wolf ET"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by Gorbachev on 2006-06-25
I have a few questions regarding playing Wolf ET.

I had a few small issues setting up Wolf ET but I've got it all installed and patched up to v2.60.

When I launch the game it turns my screen blank for a second, then goes back to the desktop.

After some forum searching, I suspect it's the lack of 3D acceleration (drivers, i suppose).

using the synaptic package thinger I searched for Radeon and downloaded some packages and installed them.

Here is a list:

[b]fglrx-control
radeontool
xorg-driver-fglrx
xorg-driver-fglrx-dev
xserver-xorg-driver-ati[/b]

Probably more than I need, but I wanted to play it safe.

If you need any more info, assume I am retarded and give very explicit directions on how I would obtain it for you :eek:  

Thanks!

---

### Post by Gorbachev on 2006-06-25
So I followed the official ubuntu ATI installation guide found here (somewhere).. still no luck.

Edit: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Here is the output of fglrxinfo


display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

It **should** be a Radeon 9550.

Heres what it's **supposed** to be:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)

Of course, with a different video card, mine being the 9550.

---

### Post by Gorbachev on 2006-06-25
Anyone.. ?

---

### Post by Jasper Houtman on 2006-06-25
In terminal type:

sudo dpkg-reconfigure xserver-xorg

Select the correct video card in the list and set it up.

sudo /etc/init.d/gdm restart

After this it should work fine.

---

### Post by Gorbachev on 2006-06-25
Thanks, I hope so.

---

### Post by Gorbachev on 2006-06-25
That thing sucks.. really..

It doesn't have a list of video cards. It also harasses me about my keyboard and mouse, why?

It also showed my video card as a Radeon 9600.

Ugh, seriously.. that thing isn't helping at all. Perhaps a walkthrough? It asks some very technical things that are beyond me.

---

### Post by Jasper Houtman on 2006-06-25
You do have the driver still installed don't you?
It should select the proper one if it is.

Note: Don't change the standard setting it shows you, these are preconfigured and should work fine.

These technical questions are for people who like to set up extra screen resolutions, etc. just accept them and go to the next screen.

BTW did you try running Wolf et after setting the card to the radeon 9600? might work now.

---

### Post by Gorbachev on 2006-06-26
It didn't work. Same black, then desktop.

I tried the official ATI ones for the Radeon series, which covers the 9550 **here**: [https://support.ati.com/ics/support/KBList.asp?folderID=356](https://support.ati.com/ics/support/KBList.asp?folderID=356)

Could you tell me which drivers i should be using, and where are they/how do i get them?

Which guide should I follow for my Ubuntu installation? Also, I used the alternate 386 iso for installation. I'm going to reformat my linux drive and start over with the regular 386 iso.. would this make a difference?

Also, I hear about things like Breezy, Hoargo or some crap, and other versions of Ubuntu. Are they official ubuntu releases? I can't find them on ubuntu's site. I go to download, and all I see are varions of the one I downloaded and installed.

---

### Post by Gorbachev on 2006-06-27
Bump!

---

### Post by theturtlemoves on 2006-06-27
What is the exact error message? Type ```
et
``` in a terminal and post the output - it might help isolate where exactly the problem is.

---

