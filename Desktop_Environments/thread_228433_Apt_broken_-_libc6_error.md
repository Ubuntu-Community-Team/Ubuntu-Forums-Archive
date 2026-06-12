---
title: "Apt broken - libc6 error"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Xeph on 2006-08-03
After doing an upgrade a while ago, my apt seems to have been broken. Last night I did another upgrade and it refused to set up the packages after it had downloaded it.

The following occured:
> 
E: Internal Error, Could not perform immediate configuration (2) on libc6

And it halted the operation. When I try to install or remove something using apt, it just lists a long long list of dependencies and quits.

> 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

"apt-get -f install" produces the "Internal Error" message as well.

Help! Please?

---

### Post by Xeph on 2006-08-03
Please someone! I can't do anything on my computer. Apt won't do anything. It just gives me dozens of dependency errors. I'm assuming my dkpg-application-list-database is corrupt or something. How can I rebuild it? To view the errors see [http://entropyone.com/apt-errors.txt](http://entropyone.com/apt-errors.txt)

please help!!!

---

### Post by jwbirdsong on 2006-08-07
Have you had any luck with this??  I've got the same problems my self..although mine *seems* to be caused by a corupt (blank) /var/lib/dpkg/status file...if you have a status-old you MAY try to replace the orig and see if that helps......my orig was corrupt and had to go to a blank one then this error has started..I'll post more info I stumble across anything else

---

### Post by Anduu on 2006-08-08
What did you upgrade...did you add some non standard repos.

Libc6 is a major system file and should not need to be upgraded in Dapper...

try an apt-get update and apt-get dist-upgrade and see what happens.

---

### Post by RAOF on 2006-08-08
Could you post your **/etc/apt/sources.list**?  As Anduu said, if it's trying to update libc6, it's probably coming from some non-official or Debian repository.  If you fix your sources.list, you should be able to apt-get update, and then try everything again, probably with **sudo aptitude install ubuntu-desktop** or **sudo aptitude dist-upgrade**.

---

### Post by jwbirdsong on 2006-08-08
[Quote=Anduu]What did you upgrade...did you add some non standard repos.
Libc6 is a major system file and should not need to be upgraded in Dapper...
try an apt-get update and apt-get dist-upgrade and see what happens.[/Quote]
My last upgrade was just a "standard" upgrade a few days ago..IIRC it contianed Python 2.3 and a few other fairly standard updates.....My repo has not changed much except for the addation of automatix and E.U repos. since I first installed Ubuntu for 6.04 in Feb 06.....

I didn't mean to "hijack' the thread from OP which is why I didn't post much more info in my origional post. 
  This started a few days ago after a "normal" daily update..for which I use synaptic..If I want to manually add someting; I normally use apt-get  but that is neihter here nor there.  After the sucessful up date the next time I ran synaptic (or any other method for that matter) I recieved a "unable to open or parse error" for /var/lib/apt/status.....
After reading several similar threads in the forums I swapped it out for the status-old..still to receive the "unable to open or parse error" so I went to a blank status file and now have this error.

FWIW I **KNOW** that libc6 is installed and upto date...along with MANY other files on my system; it just not now shown in the status file (like dpkg and apt to name a few others)..so apt-get dist upgrade or install -f tries to D/L and install 512 MG of files.... I've also included my /var/lib/apt/status file along with my source.list ..perhaps some one can tell me why it is "unreadable"???   size perhaps??

If a mod feels the need to split this off to it's own thread; do so with my appologies for hijaking someone else's thread..it was not my intnent.

---

### Post by RAOF on 2006-08-08
That's a particularly odd sources.list.  For example, you've got all the dapper-updates repositories enabled, but none of the base dapper repositories!  I'm a little surprised it hasn't broken already.

Try adding a
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
```
line to your sources.list.

---

### Post by tamzarian on 2008-01-12
Hello,

I had the same problem with an update from Feisty to Gutsy. (AMD64)

  [B] adduser postfix
   addgroup postdrop[/B]

helped.

Regards,
Chris

---

