---
title: "Sharing my desktop with WinXP machine"
date: 2006-06-03
forum: Desktop Environments
---

### Post by donnellymp on 2006-06-03
Hi. I have a colleague in another state who is developing an application in a Windows XP environment, and I need to be able to see his desktop on my Ubuntu screen. I have a Gateway laptop without a lot of bells and whistles. I looked at conferencing tools like Vyew, WebEx and GoToMeeting, but they don't allow desktop sharing between Linux and WinXP. Is there an application out there that will do the trick, or is there some native functionality within Ubuntu that will do the trick?

Any help would be greatly appreciated!

---

### Post by BenTyreman on 2006-06-03
I've used TightVNC before to do this: [http://www.tightvnc.com/](http://www.tightvnc.com/)

Then use vncviewer which should come as default on Ubuntu.

---

### Post by Mr. Picklesworth on 2006-06-25
On the topic of VNC:
I've been looking to go in the opposite direction with this (Ubuntu -> Windows with a VNC client other than the default VNC stuff accessible through System->Prefs->Shared Desktop), and I have trouble dealing with setting up a TightVNC server using the terminal.
Does anyone know of a GUI app which can help me do that?
(Or a really good tutorial that works for buffoons)

---

### Post by aysiu on 2006-06-25
What do you have against *vino*? I've had no problems with System > Preferences > Remote Desktop and using TightVNC in XP to view and/or control Ubuntu.

---

### Post by Mr. Picklesworth on 2006-06-26
Good question :P

Upon realizing my how strange my request is (especially considering that I don't really need anything magical for what I'm intending, anyway...), you may ignore my question.
Thanks for reminding me that I *already do* have something, Aysiu!


So, if I set the image compression on the client side, does it tell the server to compress it like that (or send an image that small) as well, even if the other end isn't using TightVNC?

---

### Post by BKGT on 2006-06-28
[QUOTE=aysiu]What do you have against *vino*? I've had no problems with System > Preferences > Remote Desktop and using TightVNC in XP to view and/or control Ubuntu.[/QUOTE]

Aysiu,

Could you point me in the right direction to set this up (a post or howto)?  There are a few topics on the forum that describe this but I have not had success.  I am trying to access Dapper from my XP laptop using RealVNC.

Thanks

---

### Post by aysiu on 2006-06-28
Hm. I have no experience using RealVNC. I would imagine the process would be similar to TightVNC, but I know only Tight, not Real. So here are the TightVNC instructions:

1. In Ubuntu, go to System > Preferences > Remote Desktop. Enable it and set a password for it.

2. Go to Applications > Accessories > Terminal and type this command: ```
ifconfig
``` This will tell you your IP address (a series of four numbers separated by periods--for example, 192.168.0.110).

3. In Windows download and install TightVNC from the TightVNC website.

4. Launch TightVNC Viewer with best compression. For the server address, type the IP address. For the password, type the password you set earlier.

---

### Post by BKGT on 2006-06-28
[QUOTE=aysiu]Hm. I have no experience using RealVNC. I would imagine the process would be similar to TightVNC, but I know only Tight, not Real. So here are the TightVNC instructions:

1. In Ubuntu, go to System > Preferences > Remote Desktop. Enable it and set a password for it.

2. Go to Applications > Accessories > Terminal and type this command: ```
ifconfig
``` This will tell you your IP address (a series of four numbers separated by periods--for example, 192.168.0.110).

3. In Windows download and install TightVNC from the TightVNC website.

4. Launch TightVNC Viewer with best compression. For the server address, type the IP address. For the password, type the password you set earlier.[/QUOTE]

Thanks aysiu,

I was using the wrong IP address.  RealVNC works fine as well.  I may give TightVNC a try to see if there is much difference.

---

