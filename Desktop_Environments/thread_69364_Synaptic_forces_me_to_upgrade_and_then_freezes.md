---
title: "Synaptic forces me to upgrade and then freezes"
date: 2005-09-26
forum: Desktop Environments
---

### Post by nolodude on 2005-09-26
Hi, I have some serious problems with Synaptic.

History:
---
It all started when the Update Manager told me that there is an update available: linux-image-2.6.10-5-386. I tried to update but got an error message about I/O error when accessing some x25.ko file or something (sorry, didn't really write it down and now I can't get to it anymore. Anyway I checked the harddrive and I don't think it's bad sectors or like that).

Ok, I figured that it has something to do with me compiling the kernel a while back (only to enable the OSD-support for my tv-card drivers) so I let it be.

Then I got the "already-discussed-on-this-forum" problem with mozilla-firefox 1.0.7 update. Being a somewhat n00b, I did as somebody told and removed firefox with dpkg.

Situation now:
---
Now, when I start Synaptic, it tells me that 2 of my packages are broken (mozilla-firefox and mozilla-firefox-gnome-support, surprisingly). In the "Marked changes" section there are 3 packages: that linux-image and two Firefox packages.

**Now, here's the real problem:** the linux-image has been marked for upgrade, and I cannot unmark it. It just won't unmark. And if I go ahead and apply changes, the whole computer freezes right after it has started "unpacking package linux-image-2.6.10-5-386...". So I cannot use Synaptic anymore since it doesn't allow me to do anything other than freeze my computer :(

Can anyone give me any hint as to how I should proceed with diagnosing the problem? I still wish there would be a way to fix this without doing a fresh install... :???:

---

### Post by KingBahamut on 2005-09-26
can you output the messages you get from an 

apt-get upgrade

---

### Post by nolodude on 2005-09-26
Sure, here goes... (might look strange since I'm using finnish language version)

```
---------@------:~$ sudo apt-get upgrade
Password:
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu... Valmis
N&#195;&#164;m&#195;&#164; paketit p&#195;&#164;ivitet&#195;&#164;&#195;&#164;n:
  linux-image-2.6.10-5-386
1 p&#195;&#164;ivitetty, 0 uutta asennusta, 0 poistettavaa ja 0 p&#195;&#164;ivitt&#195;&#164;m&#195;&#164;t&#195;&#182;nt&#195;&#164;.
1 ei asennettu kokonaan tai poistettiin.
Noudettavaa arkistoa 0t/15,6Mt.
Purkamisen j&#195;&#164;lkeen k&#195;&#164;ytet&#195;&#164;&#195;&#164;n 0t lis&#195;&#164;&#195;&#164; levytilaa.
Haluatko jatkaa [K/e]? k

Preconfiguring packages ...
(Reading database ... 98554 files and directories currently installed.)
Preparing to replace linux-image-2.6.10-5-386 2.6.10-34.4 (using .../linux-image-2.6.10-5-386_2.6.10-34.6_i386.deb) ...
The directory /lib/modules/2.6.10-5-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.10-5-386 ...

```

...and the machine freezes.

Edit: Oh, by the way I got Firefox working by doing as suggested by evilghost:
> cd /var/cache/apt/archives
sudo dpkg -i --force-all mozilla*1.07*.deb

---

### Post by nolodude on 2005-10-08
Update: I'm still having this problem. If I try to upgrade linux-image-2.6.10-5-386 either with Synaptic or using apt-get, the computer totally freezes. And because both of them insist I upgrade that package even if I wanted to do something else, I currently can't install or upgrade anything on this computer!

I also tried removing linux-image-2.6.10-5-386. Synaptic just crashes, apt-get gives following message when doing sudo apt-get remove linux-image-2.6.10-5-386:
```
dpkg: error processing linux-image-2.6.10-5-386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 linux-image-2.6.10-5-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Am I having this problem because I previously manually compiled the kernel? Is there anything I might try? Anyone?

---

### Post by mike_d on 2006-01-03
[QUOTE=nolodude]Update: I'm still having this problem. If I try to upgrade linux-image-2.6.10-5-386 either with Synaptic or using apt-get, the computer totally freezes. And because both of them insist I upgrade that package even if I wanted to do something else, I currently can't install or upgrade anything on this computer!

I also tried removing linux-image-2.6.10-5-386. Synaptic just crashes, apt-get gives following message when doing sudo apt-get remove linux-image-2.6.10-5-386:
```
dpkg: error processing linux-image-2.6.10-5-386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 linux-image-2.6.10-5-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Am I having this problem because I previously manually compiled the kernel? Is there anything I might try? Anyone?[/QUOTE]

did you have any success with this?  i just installed breezy on an old p-166 that i used as a file server.  right after i installed from the cd, i did a 

apt-get update && apt-get dist-upgrade

and it froze on linux-image-$currentversion.

after rebooting, it told me i need to run dpkg --configure -a, so i did and it froze again at the same place.

any clues?

---

### Post by nolodude on 2007-04-21
I ended up doing a reinstall :|

---

