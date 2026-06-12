---
title: "Permission denied - NEWBIE Question"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Johank on 2005-04-21
Hey you gurus out there. I have an embarrasingly obviously NEWBIE question. I installed Ubuntu 5.04 a day or two back and am starting to play a little. I'm trying to mount my NTFS (yes ~windows~ Oh, the horror!) drive. I opened a terminal (not the root) and entered mkdir /mnt/hd and pressed enter....All I got back is 
mkdir: cannot create directory `/mnt/hd': Permission denied
I thought that since I'm logged in with the same user name that I created at the install time, I should be able to do this? HELP!

---

### Post by Seth on 2005-04-21
Just use **sudo**.

[font=courier]sudo mkdir /mnt/hd[/font]

You aren't allowed to do anything to system files as your own user. So you use **sudo** to become root temporarily. This makes sure you have to put in a password to damage anything or potentially do something harmful.

---

### Post by Johank on 2005-04-21
THANKS! But does that not also imply that any of my desktop app - e.g. burning a CD - is contantly going to require super user login? I thought that was bad?

---

### Post by bored2k on 2005-04-21
This parameters are much better.

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

Johank no burning CD's wont require sudo.

---

### Post by Johank on 2005-04-21
Great! It works - small steps for experts, giant leaps for newbies! Thanks!

---

