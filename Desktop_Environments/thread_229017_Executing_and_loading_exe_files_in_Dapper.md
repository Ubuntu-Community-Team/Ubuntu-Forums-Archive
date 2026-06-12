---
title: "Executing and loading exe files in Dapper"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Psed on 2006-08-03
I just downloaded an exe file from Grisoft to my Temp folder. When I double click on it to execute and load the file(as I do in Windows) and fails.

What am I doing wrong?

Psed

---

### Post by cantormath on 2006-08-03
> **Psed said:**
> I just downloaded an exe file from Grisoft to my Temp folder. When I double click on it to execute and load the file(as I do in Windows) and fails.

What am I doing wrong?

Psed

Two things,

1)
What are you tring to install from Grisoft?

2) 
exe files are specificly for windows... Linux does not use them unless you use wine to install them (wine is a windows emulator). 

 We want to try to stay away from wine, unless there is no other choice.  So tell us what you are try to install, and maybe we can find it for ubuntu(linux), or maybe we can find any alternative.

please let us know ::Grin::

---

### Post by cantormath on 2006-08-03
being that you are downloading from Grisoft, Im guessing you want AVG Free.
You are in luck, they have AVG for linux.

If you are ok with trying something else, you can install automatix, which will let you install a security suite easily.

here is the install instructions.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

just install automatix and run it, then click on the programs you want and poof, they are installed.  Click on the security suite, and it installs antivirus, and a firewall for you.

once you are done, make sure you click yes, so that it changes your repositories back to normal.

---

### Post by jISh on 2006-08-03
Note that you don't really need a virus scanner for Linux, unless you want to keep files that may be accessed by Windows safe. 

ClamAV is a great choice and is in the repositories, if you need that virus protection.

---

### Post by Psed on 2006-08-04
My sincere thanks for all your replies.

I was trying to install AVG (Grisoft free), and so my problem began. I have since found, with all your help, that I downloaded AVG's windows version instead of the Linux version. My bad.
Now, going back to the AVG download site, I see 3 AVG downloads for Linux, (they are rpm files)but I cannot figure out which one I need.

Thanks for your replies..

Psed

---

### Post by Tomosaur on 2006-08-04
To install a .rpm package/file, you will first need to convert it to a .deb file.

You can do this with a program called 'Alien', which you can download from the Synaptic Package Manager (Applications > Add / Remove). It will install itself automatically.

---

### Post by cstudent on 2006-08-04
How-to written by Artificial Intelligence on how to install AVG.

[http://www.ubuntuforums.org/showthread.php?t=136064](http://www.ubuntuforums.org/showthread.php?t=136064)

---

### Post by Psed on 2006-08-06
My sincere thanks to all who helped by replying to my posts. As a Novice, it  really helped me find my way.

I downloaded Firestarter and it loaded pretty well. One small problem...
Set up says there would be an Icon placed in my tray, but none is there, even after I rebooted and looked again.

Anybody had this problem?:) :)

---

### Post by cstudent on 2006-08-07
> **Psed said:**
> My sincere thanks to all who helped by replying to my posts. As a Novice, it  really helped me find my way.

I downloaded Firestarter and it loaded pretty well. One small problem...
Set up says there would be an Icon placed in my tray, but none is there, even after I rebooted and looked again.

Anybody had this problem?:) :)

Firestarter by default runs in the background as a service. If you would open Firestarter from the menu, you would see an icon placed in the system tray. You can follow some instructions on Firestarters website on how to have it always load when you boot up, but it really isn't necessary. Once you have the firewall set the way you want, Firestarter just runs quietly in the background taking care of business.

---

