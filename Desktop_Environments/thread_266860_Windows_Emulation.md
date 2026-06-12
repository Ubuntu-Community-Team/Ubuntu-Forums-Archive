---
title: "Windows Emulation"
date: 2006-09-27
forum: Desktop Environments
---

### Post by WarAngel on 2006-09-27
I have been trying to figure out a way to get rid of my Windows partition and just have the computer run solely on Linux. The reason for this is because Windows sucks. However, I still need use of Microsoft Office 2003 for some courses at school as well as the ability to play Counter-Strike: Source. These are the only two things really holding me back.

What would be your recommendations for me to do? I've heard that I can use Qemu to install Windows as a file onto my harddrive and run Windows from there, but I can't find anything about how well I could actually play games on that. Is the program good enough that I can actually use it to keep gaming? 

I've also heard that Wine/Cedega is good for gaming. Can anyone offer first-hand experience with playing CS:S through Wine/Cedega, or Microsoft Office using one of them?

Thanks in advance!

---

### Post by fnjordy on 2006-09-27
You options are:

* [CodeWeavers](http://www.codeweavers.com/) Wine for Microsoft Office.
* [Wine](http://www.winehq.com/) for Office '97 and most games.
* [Cedega](http://www.transgaming.com) for support of new games, althoug try regular Wine first.
* [VMware](http://www.vmware.com/)'s free Server for Office and non-game software.
* [Qemu](http://fabrice.bellard.free.fr/qemu/) as an alternative to VMware, install the accelerator for a performance boost.
* [Plex86](http://plex86.sourceforge.net/) another alternative.
* [Bochs](http://bochs.sourceforge.net/) emulates an entire PC so can run on other architectures but might be a bit slow.
* [Win4Lin](http://www.win4lin.com/) is a commercial solution like a mix between VMware and Wine but tailored for running Windows only.

---

### Post by WarAngel on 2006-09-28
Sweet! Thanks for the list.

I'm still hoping someone who has experience with gaming using one of these will give me a little insight as to how effective it is. Am I going to have to deal with bugs, or are some of these options stable enough for use?

---

### Post by CatKiller on 2006-09-28
[WineHQ AppDB entry for Counter-Strike: Source]("http://appdb.winehq.org/appview.php?iAppId=871")

---

