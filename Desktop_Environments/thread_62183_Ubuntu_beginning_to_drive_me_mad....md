---
title: "Ubuntu beginning to drive me mad..."
date: 2005-09-03
forum: Desktop Environments
---

### Post by fannymites on 2005-09-03
A couple of weeks ago I encountered a problem - I was no longer able to login to ubuntu, the screen would go black then go straight back to the login screen.
After much googling I found a forum thread that suggested doing chmod 1777 /tmp.
Now, although this did allow me to login I have been having problems running certain programs as root and I am unable to change the root theme from the default human theme with the crappy gnome icons.
The big problem is I now encounter the login problem every 2-3 days and I just don't understand how permissions keep changing by themselves.
I've tried searching google over and over again and tried every suggestion I can find but I'm still getting all these problems.
Can anyone help?

---

### Post by Weav on 2005-09-03
Did anything spur on these login problems? Did you install anything weird or unsual before these events started happening? Maybe uninstalled programs on accident or edited some conf file?

---

### Post by fannymites on 2005-09-03
The last time I used ubuntu before I first got the problems, all I did was browse the wed a little, check emails, did an apt-get update (there were no updates so nothing new installed or upgraded).
There was a certain update a couple of days earlier (libc6 or something) which always messes my time up (something to do with british summer time) but I was logging in ok after that.
The only other thing I have done is install Fedora Core but I haven't mounted the fedora partition from within ubuntu or mounted the ubuntu partition from within fedora so I can't see that causing anything.
I can't really think of any more info that could help but just in case this is any use - 
I use kde and gnome and login via kdm login manager.

Some of the apps that are having problems running as root are - 

- "administrator mode" in kde control centre fails but I can run sudo kcontrol and that works ok.
- When running synaptic, if I try to look at the repositories or preferences or do an update it crashes but apt-get works fine.
- Cannot change the root theme or icons in gnome at all, either via sudo gnome-control-center or sudo gconf-editor but I can change the root theme in kde and the user themes in both.
- Cannot run most kde gui based apps from command line but no problems with text based ones.

There are many other niggling little things like this that all add up to a major pain.

[EDIT] Just to point out, I wasn't having any of these or any other problems whatsoever before the sudden login problem.

---

### Post by Weav on 2005-09-03
Hhhmm is it possible you tried to install KDE programs? I think i did that once and it constantly nagged and screwed over some of my Gnome problems.

Other than that suggestion I really don't know what it could be. Maybe some more of the more experienced Ubuntuers could help outt here...

---

### Post by fannymites on 2005-09-03
I installed kde the day I installed ubuntu and there haven't been any kde updates for some time and I haven't installed any new kde apps since then.
I have had ubuntu running pretty much problem free for about 3 months.

---

### Post by Weav on 2005-09-03
[QUOTE=fannymites]I installed kde the day I installed ubuntu and there haven't been any kde updates for some time and I haven't installed any new kde apps since then.
I have had ubuntu running pretty much problem free for about 3 months.[/QUOTE]
Hhhhmmmm danget i really have no idea i'm sorry

---

### Post by fannymites on 2005-09-03
After more messing around I noticed that /var/tmp/kdecache-username had the wrong permissions.  What few error messages I could make sense of had always pointed to /tmp so I never new what else to look at.
I've changed permissions and everything seems ok again so far...

---

### Post by Galoot on 2005-09-03
Please, if you don't mind, update this thread in a few days/weeks to tell us if your fix worked.

---

