---
title: "help with compiz"
date: 2009-05-21
forum: Desktop Environments
---

### Post by ozweego5 on 2009-05-21
Hello, I just got my brand new laptop in today its a Gateway T-6859u Notebook PC - Intel Core 2 Duo T6400 2.0GHz, 4GB DDR2  
when I click on extra on the visual effects i get after a box pops up and searches for the drivers, I get "desktop effects can not be enabled??

any help would be appreciated.

---

### Post by raymondh on 2009-05-21
Hello Ozweego5 ....

I'd try to run a compiz check to see if your card can handle/take desktop effects.  See this link (which is also a stickkie on this sub-forum)

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

From there, It can give you an idea towards your next steps.

---

### Post by ozweego5 on 2009-05-21
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N)




thats what i got from following your steps

---

### Post by asmoore82 on 2009-05-21
Likely, you have an Intel integrated graphics chipset that is blacklisted by compiz.
You can try running compiz from a terminal to see the error messages,
Open a terminal and:
```
compiz --replace
```

To return to normal after that, Alt+F2 to open "Run" and:
```
metacity --replace
```

EDIT: posted late.

---

### Post by ozweego5 on 2009-05-21
rick@rick-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

(metacity:5631): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",



thats what i got......

---

### Post by raymondh on 2009-05-22
Hello Osweego (or Rick)

I too have the intel 965/960 on a dell inspiron 1525 laptop.  Sadly, while running 9.04, I could never get compiz running as stable as I wanted.  

I tried to skip the blacklist check but got very dismal/freezing performances. Most irritating when I have 2 or more apps running at the same time.

Then, I tried to follow this thread:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) 

I used  "safe" to no avail ... had constant freezes that I reverted back.  I also tried the rc kernel.

After a while ... since I really wanted compiz in this laptop, I decided to try an older kernel ... (8.10 was OK but still not smooth enough).... finally reverting this laptop to an 8.04 build (24.23 kernel)... and getting compiz running well enough for my liking.  So far so good.

Unfortunately because of my experiences, I cannot recommend a direct fix.  You will have to decide whether to do the workaround/s or not.  What I can tell you is kernel 2.6.24-23 works well for me (albeit an older kernel). 

Here are other links/sites I used for reference

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[http://webupd8.blogspot.com/2009/05/ubuntu-intel-graphic-card-driver-news.html](http://webupd8.blogspot.com/2009/05/ubuntu-intel-graphic-card-driver-news.html)
[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

Good luck and regards,

---

### Post by ozweego5 on 2009-05-22
thanks for the advice, I can just live with out it I guess for awhile until there is a fix for it. Its not the only reason why ubuntu kicks @ss!!! but def. thanks for your advice.....
RICK

---

### Post by raymondh on 2009-05-22
> **ozweego5 said:**
> thanks for the advice, I can just live with out it I guess for awhile until there is a fix for it. Its not the only reason why ubuntu kicks @ss!!! but def. thanks for your advice.....
RICK

May I ask ... is there a particular application you need to run hence the need for compositing?  That is, of course, aside from the now-famous effects.

---

