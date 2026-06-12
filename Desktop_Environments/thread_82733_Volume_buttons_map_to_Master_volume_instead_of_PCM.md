---
title: "Volume buttons map to Master volume instead of PCM/Headphone"
date: 2005-10-27
forum: Desktop Environments
---

### Post by stefann on 2005-10-27
On my Dell Inspiron 8600 I have speakers connected to the headphone-output, and now when I want to change volume or mute via the volume buttons on my keyboard, they just affect the Master volume in alsa, not the Headphone or PCM volume. And the Master volume doesn't affect the Headphone jack.

Is this possible to change?

---

### Post by usacomp2k3 on 2005-11-03
Yeah, I have the same problem

---

### Post by daller on 2005-11-03
What application do you use to activate your hotkeys?

Try using mmkeys!

I have modified the source to fit the 8600:

[http://www.dumazz.dk/mmkeys-8600.tar.gz](http://www.dumazz.dk/mmkeys-8600.tar.gz)

Once downloaded and unpacked, do this:

--------------------

Enter the extracted folder!

sudo apt-get -y install xmms-dev xlibs-dev libxosd-dev gcc libxinerama-dev make

make

sudo make install

sudo mkdir ~/.mmkeys/

sudo cp config ~/.mmkeys/

mmkeys

Have fun

Place a shortcut for mmkeys in:

~/.kde/Autostart/ (Edit: You are using gnome I see, Please find the respective autostart-folder yourself :))

---

### Post by aruckert on 2005-11-24
I have the same problem and I don't think it is about the key mappings... Using the Volume Control application, the Master volume should afect the other volumes. That is, the other volumes should be "proportional" to the Master volume. That's why it is "Master" in the first place.

&#191;Have you found a solution to this problem?

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

### Post by jtbates on 2007-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/63544](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/63544) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Here's a link to the bug in Launchpad:
[Volume control key controls speaker & not headphones]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/63544")

---

### Post by hvbakel on 2007-05-03
In KDE you can right-click the volume control in the system tray and go to 'select master channel'. If you choose PCM here your volume keys should control both the headphone and speaker channels. I imagine gnome might have something similar.

---

### Post by RAOF on 2007-05-04
System->Preferences->Sound->Default mixer tracks - This is where you can select what setting(s) the volume keys should control in Gnome.

---

### Post by XProgrammer on 2007-05-09
wow.. very simple and neat..
Thanks RAOF.

++
XP

---

### Post by HyperY2K on 2007-06-27
> **RAOF said:**
> System->Preferences->Sound->Default mixer tracks - This is where you can select what setting(s) the volume keys should control in Gnome.

Is this entry available in any ubuntu version? I use 6.10 and I don't see any default mixer thing

---

### Post by RAOF on 2007-06-28
> **HyperY2K said:**
> Is this entry available in any ubuntu version? I use 6.10 and I don't see any default mixer thing

Hm, it would seem to be new in Feisty (Ubuntu 7.04).  Sorry, it's been some time since I used Edgy :).

---

### Post by HyperY2K on 2007-07-01
is there any way do configure this via a configuration file?

---

### Post by funkysod on 2008-01-06
hey guys! thanx a lot for that post.. solved my last issue on my laptop. feel kinda stupid for not have figured it out by myself. dough..

---

