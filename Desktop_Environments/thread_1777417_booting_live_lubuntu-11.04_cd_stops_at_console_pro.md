---
title: "booting live lubuntu-11.04 cd stops at console prompt"
date: 2011-06-07
forum: Desktop Environments
---

### Post by père ubu on 2011-06-07
I wanted to show somebody lubuntu-11.04 using the live option
but I have forgotten the 'incantation' to get the boot process to
continue to the graphical desktop.
It stops at a console 'ubuntu@ubuntu' prompt.

I had found the 'login expression' somewhere but I can't find it
any more.

Can anyone help.
.

---

### Post by ajgreeny on 2011-06-07
You could try **startx** after logging in to the ubuntu@ubuntu, but if the GUI does not start automatically, I suspect something is not right with either the .iso file you used, or the CD/USB you burned, or there is a hardware incompatibility of some sort.

Give it a try, but if it still does not work check the md5sum of the .iso file (76e5865ce8d0d08fa9f833d781016fe3) and if OK burn again as slow as possible.

---

### Post by père ubu on 2011-06-08
I had already tried 'startx', it does not work.
I always check both the iso and the disk before starting.
I have already installed from the disk choosing 'install' on my desktop.
There is no hardware compatibility issue. I was running it on my laptop
where I had used it before.

When I encountered this problem previously I googled and found a site
where somebody gave the answer to another who had asked the same question.
If I remember correctly you had to type 2 words and then the boot continued.
However I forgot to write them down and I can't find the place again.

---

### Post by Catharsis on 2011-06-08
'startlubuntu'? 'sudo service lxdm start'? Is the problem just that it's booting to a command line and not the graphical desktop?

---

### Post by père ubu on 2011-06-08
SOLVED. I should have been thinking instead of posting.
"sudo lxdm" does it.

As a Fedora user I am a bit shaky on Debian/Ubuntu lingo.
I have used Ubuntu for more than 2 years (Ubuntu on laptop +
Fedora on desktop) but that is more than a year ago ...

---

### Post by ajgreeny on 2011-06-08
I am glad you have it sorted to your satisfaction, but lxdm should start automatically and either ask for user and password, or log you in automatically, if that is how you set it up when you installed.

I am running lubuntu on both an old laptop and also my netbook, and both go to the gui login screen with no interaction from me, as I would expect yours to do.

---

