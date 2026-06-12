---
title: "Quake4 Installation."
date: 2006-02-12
forum: Gaming &amp; Leisure
---

### Post by Jaygo333 on 2006-02-12
I'm trying to install Quake4 demo for Ubuntu and get snagged at one point.
I've downloaded the quake4.run file and installed it. The question is what do I do next.I've tried following [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)
but get stuck when it says
The following files must be copied from the install CDs [1]
to your q4base/ directory ( md5 sums provided as reference ):

If you copy them before running the installer you will need to
create the paths, by default /usr/local/games/quake4/q4base
If you copy after running the installer, make sure not to
replace any paks the installer might have provided.

What CD's are they talking about and the md5 sums. Where do I copy them.
I've tried running quake4 in terminal but it says quake doesn't exist.

:h34r: Jaygo333 :h34r:

P.S. Just incase the process is a pain. How do I remove everything I've installed. I just installed the .run file

---

### Post by Horndog on 2006-02-12
I'm afraid that is for the retail game.

---

### Post by Jaygo333 on 2006-02-12
Then where can I get the demo. And Install It.

Also How do I remove this one then.

:h34r: Jaygo33 :h34r:

---

### Post by Horndog on 2006-02-12
[QUOTE=Jaygo333]Then where can I get the demo. And Install It.

Also How do I remove this one then.

:h34r: Jaygo33 :h34r:[/QUOTE]

That's a good question. The only Quake 4 Demo I played was for windows.  A guess would be that you need the windows version and some how you load it
with the quake4-linux-1.0.6.x86.run it's only 18MB. Not enough to be the game itself. Maybe some one else could say howto.

---

### Post by Jaygo333 on 2006-02-12
Thanks

Do you now know how to remove this one.
Also, do you know anywhere I can go get some linux FPS Native games or demos I could play.

:h34r: Jaygo333 :h34r:

---

### Post by Jason_25 on 2006-02-12
[QUOTE=Jaygo333]Thanks

Do you now know how to remove this one.
Also, do you know anywhere I can go get some linux FPS Native games or demos I could play.

:h34r: Jaygo333 :h34r:[/QUOTE]

ID software is friendly to the linux community.  The demo and retail game runs in linux natively.  [This]("ftp://ftp.idsoftware.com/idstuff/quake4/demo") is the link to the linux demo.  Obviously, choose the second one down.  Everything is contained in the file.

---

### Post by Jaygo333 on 2006-02-12
Do I just sh xxx and everything done.

:h34r: Jaygo333 :h34r:

---

### Post by Jason_25 on 2006-02-12
Technically yes.  I had a sound problem because I'm using the 64 bit version.  If you are using the 386 (default) or 686 it should install without problems.  You may want to put sudo in front of sh.

---

### Post by Jaygo333 on 2006-02-12
Thanks.
Just one Question. 
How do I remove the other quake.run retail version that I installed?

:h34r: Jaygo333 :h34r:

---

### Post by Jason_25 on 2006-02-12
It will probably be in /usr/local/games.  Just delete the folder.

---

### Post by Jaygo333 on 2006-02-12
Thanks. You seem clever in the ways of ubuntu.
Could I just ask you a question that is completely off topic just for one second.
If it offends you just say so.
My problem is short. Every time I start Syanptic, I get the following errors:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

Should I just delete them from sources.list or what. Yesterday, apt-get update was working well, today I get these error. I tried adding extra repositories but those didn't work. I deleted those but still get these errors.
What's wrong.?

:h34r: Jaygo333 :h34r:

---

### Post by Jason_25 on 2006-02-12
Check [this]("http://www.ubuntuforums.org/showthread.php?t=128684") thread out.  Post 2, specifically.  If you don't have "us" in front of your servers in apt-get, I suggest you wait until the servers recover as it seems they are having trouble.  The main site and wiki have been giving me trouble today as well.

---

### Post by Jaygo333 on 2006-02-12
I now seem to be getting different errors from apt-get update

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

What Now. Especially the first few lines. They scare me.

:h34r: Jaygo333 :h34r:

---

### Post by noko on 2006-02-12
I have Quake4 installed and it runs good graphically on medium quality and at 800x600. The sound though is all distorted and sounds like 2 bits out of 16. The install program placed files in my directory and not the games directory, noko/quake4.

Anyone have anything for to try on this? Ubuntu 5.10 i386, system spec below. I have OpenGl drivers installed, audio is the problem as far as I can tell.

---

### Post by Jason_25 on 2006-02-12
[QUOTE=noko]I have Quake4 installed and it runs good graphically on medium quality and at 800x600. The sound though is all distorted and sounds like 2 bits out of 16. The install program placed files in my directory and not the games directory, noko/quake4.

Anyone have anything for to try on this? Ubuntu 5.10 i386, system spec below. I have OpenGl drivers installed, audio is the problem as far as I can tell.[/QUOTE]
Are you running the nvidia OSS drivers?  There is a bug with ID linux games and certain card's OSS output.  It has to do with matching the sound frequency rate. If you bring up the console you will see where it is expecting a certain frequency but the hardware is delivering something different.  There are patches for the Doom games but not quake 4.  I gave up messing with the hex editor and went back to alsa sound. That was unfortunate for me because I can't figure out the spdif output with alsa.

---

### Post by Horndog on 2006-02-12
Use this either at startup command or you can put it in your config. The OSS drivers are the key.


```


+set s_driver oss +set s_numberOfSpeakers 2


```

---

### Post by noko on 2006-02-12
Thanks for quick reply Horndog, is that the Quake4 config file? or Ubuntu? I am really new at this. Thanks in advance.

Thanks Jason as well, I am using an ATI card so no Nvidia drivers loaded I hope :cool:.  *OOPS, sorry, I just realize I am using NF2 Nvidia chipset, so I am using what ever Ubuntu installed for the MCP chip*.

---

### Post by Horndog on 2006-02-12
Sorry I should have been more clear. Either but in the /.quake4/q4base/Quake4Config.cfg

 or use it and the start command.


```


/usr/local/games/quake4/quake4 +set s_driver oss +set s_numberOfSpeakers 2



```

---

### Post by noko on 2006-02-13
Cool!!! Cool!! Cool! :mrgreen: Fragging away. Thanks Horndog!! Ubuntu and the community is really impressing me.

---

### Post by Jaygo333 on 2006-02-13
Sorry for the Distraction.!?!

Did all of you buy Quake get it through torrent. 
If throught torrent, maybe, "share". I'd also like to enjoy the benefits of Saving earth through Ubuntu.
Also, if possible, give short walkthrough as to how you installed it.

:h34r: Jaygo333 :h34r:

---

