---
title: "Google Earth Frustrations"
date: 2009-04-18
forum: General Help
---

### Post by Holden99ca on 2009-04-18
OK I'm new to Ubuntu but I've hit my frustration level with this so I'm requesting assistance. Trying to make a long story short: I wanted to install google earth. I looked it up and it looked like I needed to install medibuntu. Looked up how to do that and did it. It still didn't appear in my packetmanager but there was a command line way to install it so I did that. It still didn't work because (I think) I was unable to accept the license even by pressing the tab key. I did something to re-install but I can't remember what now. Finally I was able to get it installed and running--but it was flaky. It would crash the system and it was recommending upgrading. So I downloaded the most recent version and installed it pretty easily with sh googlearth. I thought it would install over the old version but now I have two versions installed. I can't figure out how to uninstall the old version or even where it is on the system. Arrggghh. If someone could give me a hand here I'd appreciate it. Oh I should add that neither version appears in the packet manager.

---

### Post by ssdt on 2009-04-18
Google should work on linux softwares like Google Desktop and Google Earth. Without that they can't make wine run it like it should.

---

### Post by NightwishFan on 2009-04-18
Google Earth is intended to work. However like Windows, you need to uninstall software before you install the same one from a different source.

I am not sure about the commands, however, if you have medibuntu enables, you should be able to just remove it. If not, then see if the script you installed has a simple uninstallation.

---

### Post by juancarlospaco on 2009-04-18
search the name on synaptic, and remove it.

---

### Post by Holden99ca on 2009-04-18
Hey Nightwishfan and juancarlospaco,

Thanks for the assistance. In my experience of windows, reinstalling, will install overtop of the old installation not install a second time. But it's not important because I've switched to Ubuntu.

I do have medibuntu installed but the script that it specifies to uninstall doesn't appear to work. Moreover, like I said, neither version appears in synaptic. Does it help if I mention that the first version is the older 4.?? version and appears in both my wife's and my menu bar whereas the new version 5.?? appears in only my menu bar (along with the old version).

Holden

---

### Post by oldos2er on 2009-04-18
If you used a package manager e.g. Synaptic or apt-get to install Google Earth 4.x, use the same method to remove it:
```
sudo apt-get remove googleearth-4.3
```
 This won't touch the newer version you installed manually.

---

### Post by Holden99ca on 2009-04-18
> **oldos2er said:**
> If you used a package manager e.g. Synaptic or apt-get to install Google Earth 4.x, use the same method to remove it:
```
sudo apt-get remove googleearth-4.3
```
 This won't touch the newer version you installed manually.

You know that makes a huge amount of sense but it tells me that it's not installed so it can't be removed. I've now just deleted the the new version, which was easy but the old version wasn't budging so I just removed the googleearth directory that was in /usr/shared/

There still seem to be some google earth files left over when I do
locate googleearth-4.2
and moreover when I try to run it, it still tries to run (unsuccessfully) even though there don't seem to be any googleearth files in my home directory. Moreover, application menu option is still there (I've now hidden it) I know this isn't the way one is supposed to do things but I was getting frustrated (a beautiful day outside and I was in front of the computer). I appreciate everyone's help. Do people anticipate any problems as a result of my improper method of removal. Should I remove the remaining files that reference googleearth? Should I re-install 4.2 then take it off again in the hopes that it would perform a cleaner uninstall? So many questions. Apologies.

---

### Post by oldos2er on 2009-04-19
I gave you the wrong version number. Try
```
sudo apt-get remove googleearth-4.2
```

---

### Post by desconocido on 2009-04-20
When I use Syntaptic to search for "googleearth", it only shows me something called "googleearth-package 0.5.2" Is this like Google Earth 5.2 or is it something much earlier before Google Earth 1?

File /usr/share/doc/googleearth-package/README.Debian for example has a date of 3rd October 2007.

---

### Post by desconocido on 2009-04-22
Ah, this web page
> [https://answers.launchpad.net/ubuntu/+source/googleearth-package/+question/61017](https://answers.launchpad.net/ubuntu/+source/googleearth-package/+question/61017)
suggests that it can be used to install the latest version of Google Earth.

---

### Post by SeePU on 2009-04-30
I have the same frustration and GE doesn't work.

I've tried the new one and the one in the medibuntu repository.  

It will install but not run at all.  

It would run in Windows, no problem.

---

### Post by dcstar on 2009-05-01
The **googleearth-package** script in the Ubuntu repositories is a little old, this one seems to work much better:

[http://packages.debian.org/sid/all/googleearth-package/download](http://packages.debian.org/sid/all/googleearth-package/download)

When you do a **make-googleearth-package** there are far less library messages than before, and then you just install the resulting .deb package.

---

### Post by SeePU on 2009-05-01
> **dcstar said:**
> The **googleearth-package** script in the Ubuntu repositories is a little old, this one seems to work much better:

[http://packages.debian.org/sid/all/googleearth-package/download](http://packages.debian.org/sid/all/googleearth-package/download)

When you do a **make-googleearth-package** there are far less library messages than before, and then you just install the resulting .deb package.
Whatever.

Google Earth SUCKS in Linux and that includes Ubuntu, sorry to say.

It just doesn't work or you have to go through WAY TOO MANY hoops to get it working if it even does.

I've tried repositories and also the deb package but no dice.  Same thing happens.   Like I said.....

---

### Post by NightwishFan on 2009-05-02
A long time ago I tried the one from Medibuntu, and it worked fine. I believe it is fairly up to date.

Yeah whine about software incompatibility and how you have to jump through hoops in a world where Windows has 90% of the computer market. We are lucky we get anything.

I prefer to use a system I know in and out and actually have a valid license for. I can move it around easily and have full control over the power management and disk usage. Any features I do not want do not exist for me, if I choose.

Perhaps have a little patience, or bug Google to provide debs/rpm?

---

### Post by DeMus on 2009-05-02
> **Holden99ca said:**
> OK I'm new to Ubuntu but I've hit my frustration level with this so I'm requesting assistance. Trying to make a long story short: I wanted to install google earth. I looked it up and it looked like I needed to install medibuntu. Looked up how to do that and did it. It still didn't appear in my packetmanager but there was a command line way to install it so I did that. It still didn't work because (I think) I was unable to accept the license even by pressing the tab key. I did something to re-install but I can't remember what now. Finally I was able to get it installed and running--but it was flaky. It would crash the system and it was recommending upgrading. So I downloaded the most recent version and installed it pretty easily with sh googlearth. I thought it would install over the old version but now I have two versions installed. I can't figure out how to uninstall the old version or even where it is on the system. Arrggghh. If someone could give me a hand here I'd appreciate it. Oh I should add that neither version appears in the packet manager.

I downloaded the googleearth.bin file from the google site and installed using sh Goo[tab] 
[tab] to complete the right filename without having to type so much.
It is installed in my home directory since I did not use sudo. This way if I don't like it I can simply delete the google-earth folder and it's gone.
In the google-earth folder I renamed a file called libcrypto.so.0.9.8 to libcrypto.so.0.9.8_org so the program has to use the original file supplied by Ubuntu. The one coming from Google is not correct.
Now it works like it should. Btw, I use the 64 bits version of Jaunty.

---

### Post by stimpack on 2009-05-02
Hey thanks DeMus!, never had a problem ever with Google Earth, uptil Jaunty when it crashed. That libcrypto rename fixed it :).

---

### Post by stef-l on 2009-05-02
I'm new to Linux  (ubuntu 8.04) but trying my best! Iwant to install Google Earth.  Have tried via medibuntu, via the ggogle earth website, via synaptic.  I have not had any error messages, and have 2 google earth icons in Applications/Internet, but whenever I try & launch the program, I get the small google earth splashscreen, then I'm back to my ubuntu logon and password screen.  Nothing else ever happens.  And if I try & look for google earth in add/remove programs it's not there!

so - do I have anything installed?

do I have something garbled installed? if so how do I get rid of it?

and how do I get google earth installed?

very grateful for any suggestions

---

