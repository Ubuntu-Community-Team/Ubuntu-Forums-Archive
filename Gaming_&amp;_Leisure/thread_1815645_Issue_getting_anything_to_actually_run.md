---
title: "Issue getting anything to actually run"
date: 2011-07-31
forum: Gaming &amp; Leisure
---

### Post by azraelck on 2011-07-31
I recently returned to Ubuntu to run a dual boot, in hopes that 11.4 would be more stable than WIN7 (hard to be more unstable). Specifically, I intended to try to run Dungeons and Dragons Online, which some have claimed works under WINE. 

However, none of the apps I have installed will run, as they are not marked as an executable. Ubuntu will not allow me to set them as executable. Nothing in DOSBox will run, nothing from my Windows games folder will run, nothing. 

There is absolutely no excuse for Ubuntu to block my access to software I already have installed. I am not reinstalling anything just for Ubuntu. Everything is installed, and should be accessible. Whats more, none of the software I have is even listed under wine's install programs list. 

Is there a work around, or is ubuntu now a virus like Windows?

---

### Post by CatKiller on 2011-07-31
> **azraelck said:**
> I am not reinstalling anything just for Ubuntu. Everything is installed, and should be accessible. Whats more, none of the software I have is even listed under wine's install programs list. 

Tell me, if you tried to run a program in Windows from a different Windows install (not installing it, just running the executable from that other Windows' Program Files) would you expect it to work? Would you expect there to be entries in the Start menu? Of course not. Why would you expect Wine's pretend Windows environment to be any different?

The installation process does all that; there are files to be copied, registry entries to be made, DRM to install, dlls to be spread across your hard drive. If you won't actually install anything, it won't be installed.

It isn't magic, and Wine is not a panacea.

---

### Post by 5PUTN|K on 2011-07-31
Although cat killer is actually right I believe all you need is a simple launcher program called pylotro just do a google search and install that I havent actualy tried this myself but I presume dnd online works just like lotro( that one i have tried myself) and the launcher has a lotro dnd switch soswithch it to dnd ant try launching it with pylotro instead of the exe that tou cant mark as an executable which by the way is totaly weird 0.o

---

### Post by doas777 on 2011-07-31
Just an aside Op, if you are having serious stability issues with windows and ubuntu, then you have a hardware problem, or you are doing something that is resulting in a flimsy system. when appropriately administered on functional spec hardware, both oses are quite stable.

as for your wine issue, I have had more failures than sucesses with wine, and my best advice is to reconsider the tools you are using. in this case that isn't an option, but in the long run, you will almost always have a slightly substandard experience running windows apps in linux, even in the best of circumstances. 

there are several tools designed to make configuring wine for applications, including winetricks. 

When I look up your app in WineHQ's appDB, there are instructions for getting it to work, including installing winetricks. did you follow the instructions here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2910](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2910)
?

---

### Post by garvinrick4 on 2011-07-31
> Is there a work around, or is ubuntu now a virus like Windows?
If you have problems with whichever Operating System you choose to run have you
ever considered it could be user error.

---

