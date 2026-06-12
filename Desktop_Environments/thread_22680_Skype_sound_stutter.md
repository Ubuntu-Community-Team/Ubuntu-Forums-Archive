---
title: "Skype sound stutter"
date: 2005-03-29
forum: Desktop Environments
---

### Post by Migmar on 2005-03-29
Hello,

I was finally able to get sound work in Skype by running:
**aoss skype**

But still not perfect, since when calling "echo123" I get a major sound stutter with the following message filling the terminal:[B]
volume_adjust: SOUND_MIXER_WRITE_IGAIN failed: Invalid argument[/B]

Any theories on the reason for this? Solutions? The official Skype FAQ seems to be mainly for KDE users...

Migmar

---

### Post by orion_114 on 2005-04-08
I used Skype on Windows and I would get some major stuttering because my network connection was too slow. What connection have you got ?
I am on a 56k dailup type connection.

---

### Post by Migmar on 2005-04-08
I have a 512kbs adsl, so that should not be the reason.

I found some help in here:
[http://forum.skype.com/viewtopic.php?t=17212](http://forum.skype.com/viewtopic.php?t=17212) 

Skype works perfectly on my Windows box, but it seems to be more troublesome with the linux version. And looks quite ugly, too...
I'd wish it ended up in the Ubuntu repositories, maybe it worked better if installing it with apt.

Migmar

---

### Post by orion_114 on 2005-04-09
Maybe you can add it to the wish list. It seems to be missing at the moment becsuse Hoary was just released, but I am sure that there will be a wish list soon for  The Breezy Badger release.

---

### Post by Marc Higgins on 2005-04-25
[QUOTE=orion_114]Maybe you can add it to the wish list. It seems to be missing at the moment becsuse Hoary was just released, but I am sure that there will be a wish list soon for  The Breezy Badger release.[/QUOTE]
 i had been distro hopping prior to the release of the latest ubuntu but have settled now. This sound skipping is a problem with the skype linux client. It has nothing to do network speed, in the office i have 100mbps fiber up & down & skype skips on all the linux machines in the office regardless of distro, ubuntu, debian, knoppix, suse, fedora, mandrake, kanotix, but seems to work fine on windows. I think we should all be hitting the skype forums [http://skype.org/community/forums.html](http://skype.org/community/forums.html) to get more work done on the skype linux client

---

### Post by chettyk on 2005-04-25
[QUOTE=Marc Higgins]i had been distro hopping prior to the release of the latest ubuntu but have settled now. This sound skipping is a problem with the skype linux client. It has nothing to do network speed, in the office i have 100mbps fiber up & down & skype skips on all the linux machines in the office regardless of distro, ubuntu, debian, knoppix, suse, fedora, mandrake, kanotix, but seems to work fine on windows. I think we should all be hitting the skype forums [http://skype.org/community/forums.html](http://skype.org/community/forums.html) to get more work done on the skype linux client[/QUOTE]

I don't think that is correct. I have a dual-boot on my laptop. I have the stutter problem with Skype running on Ubuntu. The Skype sound is clear and uninterrupted on Mandrake 9.2 that came with the laptop (Compaq Presario 2205AL). On both distros, I am using the same Skype package (Static binary Qt 3.2 compiled in).

---

