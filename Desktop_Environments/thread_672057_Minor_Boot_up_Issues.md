---
title: "Minor Boot up Issues"
date: 2008-01-19
forum: Desktop Environments
---

### Post by arichards on 2008-01-19
Hello I had a few questions which probably can be resolved in one swoop.

When I start up Xubuntu 7.10, it sort of locks up. Hitting alt-F4 breaks this lock up but gives an error on my ali-mixer (which I found out is my sound).  However after continuing it puts out ~ a screenfull of errors saying IRQ1 is to busy then finally brings me to the welcome screen.

I was hoping there would be a way to to see what lines are running to cause the errors as before they run (like hitting F5 in the windows world) so I can try to figure out what is happeneing.

I am not brand new to linux, nor have I been using it for long. Coming from a windows background I assume this is possible I just need to know what file or where to look.

Thanks for your help!

---

### Post by benerivo on 2008-01-19
You could take a look at something like /var/log/kern.log, or maybe change the boot up, so that it displays all messages when booting. You should be able to do this by going in to /boot/grub/menu.lst and replacing 'quiet splash' to just read 'verbose'```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d54d54df-dfd5454gd-45d4dd ro quiet splash
```

I haven't done this myself before, so find a little bit more about such a change before doing it. I think it would be very easy to put back to the original, using the live cd, should it cause ubuntu to fail to load.

---

### Post by arichards on 2008-01-19
Thanks for your help! It is now able to boot just fine, need to play with the AC '97 (or something like that) mixer to get it to work. Also when I log in as one of my users (non privileged) there is a program that starts automatically anyway to disable this?

Thanks again!

---

