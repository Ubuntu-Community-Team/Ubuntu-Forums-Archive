---
title: "My system broke"
date: 2009-03-21
forum: General Help
---

### Post by Gr8world on 2009-03-21
Hi,

So my story is as follows:

I tried to change permissions of the whole file system so I used 'sudo nautilus' and went to file system -> preferences and changed it to read and write and did 'apply permissions to enclosed files' and the system broke (no wallpaper, no icons,...) that I couldn't even close the system. so when I cut the power and turned the machine back on it couldn't boot because it found no init and other files... 
And finally I came to a sort of a command line where I did 'reboot' and I use the live CD now....

Well this is my situation and can someone me get out of this fast?

---

### Post by taurus on 2009-03-21
Your best bet is to backup your personal files with Ubuntu LiveCD and reinstall!  Changing permissions or ownerships of / is the worst thing you could have done to your machine.

Next time, just leave the permissions and ownerships of root filesystem, /, the way they are.

---

### Post by tacomodo on 2009-03-21
Unless he also took away execute permissions, and set 444, why would it break anything, I wonder...

---

### Post by Gr8world on 2009-03-22
But isn't there a way to change them back how they were? with the live CD or something? 
I tried to do so and it does change it how I want it but when I select all in there, I can't set root as owner, it's just '--'.

Well when I reboot now it gets 'Error 21' when loading GRUB.

So thank you all for your response but isn't there a way to just change the permissions back?

---

### Post by change_mode on 2009-03-22
There's always a way, but in this case it would be much more work than just reinstalling.
You shouldn't mess with the / permissions. Not only can it break your system, it's also bad from a security standpoint.

---

### Post by Gr8world on 2009-03-22
> **change_mode said:**
> There's always a way, but in this case it would be much more work than just reinstalling.
You shouldn't mess with the / permissions. Not only can it break your system, it's also bad from a security standpoint.

Yea, I know but I just wanted to copy the whole system to an other drive without doing a fresh install on it and return all the settings one by one. 

So this is also the reason why I don't want to do a fresh install now. I want to keep all my settings.

---

### Post by change_mode on 2009-03-22
As far as I know there's no way to automatically reset all the permissions, so the only thing you can do is look up (in another Ubuntu installation or the internet) what the permissions need to be like for the files and set them all manually...

You can just back up your home folder by the way, many options are stored there.

For the future, search google or these forums for 'ubuntu system backup', there are easy ways to copy your installation.

---

### Post by Gr8world on 2009-03-22
Well, thanks guys, 

I did a fresh install anyways...

---

