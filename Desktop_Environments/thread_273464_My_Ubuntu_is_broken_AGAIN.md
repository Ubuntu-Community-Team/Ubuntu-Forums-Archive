---
title: "My Ubuntu is broken AGAIN"
date: 2006-10-08
forum: Desktop Environments
---

### Post by pod25 on 2006-10-08
Here is how it happened and what is happening now :

The other day I had a power cut. When the power came back on I powered up my ubuntu. Straight away I knew something was wrong, it skipped the login and loaded the XFCE default desktop and not my customized desktop. 
I left it be at first. Then what happened was the screen-saver kicked in and eventually the Login Page came up which happens after a certain length of time. 
I entered my login details which were rejected ! so I clicked on New Login then entered my details again, this time it worked and my customized desktop showed.
Now I have my desktop up, nothing is working, nothing from the Applications Menu will work and non of my shortcut links in my customized menu bar work, I can't even access Terminal.

Luckily I can access the ubuntu via ssh from my windows comp.

How can I fix it ?

---

### Post by pod25 on 2006-10-08
After I made my first post the screensaver kicked in, it went straight to a blank black screen, now even after hitting keys on my keyboard and mouse movement will not re-activate it.
I then tried vis ssh from my windows comp to reboot the ubuntu, this has also failed to do anything.
My last resort is to hit the reset button.

Hopefully someone will reply with a little help before I hit the reset button.

---

### Post by pod25 on 2006-10-08
No replies, so I hit the reset button.
Again, after the reboot it skipped the login and loaded the desktop.
I can now at least open Terminal, however I'm logged in as :```
sh-3.1$
```
And I have no permissions to do anything.

---

### Post by Old Pink on 2006-10-08
Ctrl + Alt + Backspace, and log in there? 

Or, is the Ctrl + Alt + F1 terminal any better?

---

### Post by pod25 on 2006-10-08
> **Matt.H said:**
> Ctrl + Alt + Backspace, and log in there? 

Or, is the Ctrl + Alt + F1 terminal any better?

Thankyou, Ctrl + Alt + Backspace, did the job, I'm now back into my desktop, and everything seems to be working.

But what caused this ?  and will it happen again ?

---

### Post by Bigbluecat on 2006-10-08
I suggest you buy a UPS (I use APC CS500). This is basically a large battery and can enable a controlled shut down in the event of a power cut. I suffer from quite a few of these where I live.

The problem with a power cut is it is just the same as yanking the power cord from the PC. Whatever process or file access is in process will just stop mid way with very unpredicatble results.

Once you have a UPS device you will need to install APCUPSD. This programme starts a service that monitors your UPS. With this you can specify the time to smart shutdown in the event of a power interruption.

---

### Post by pod25 on 2006-10-08
> **Bigbluecat said:**
> I suggest you buy a UPS (I use APC CS500). This is basically a large battery and can enable a controlled shut down in the event of a power cut. I suffer from quite a few of these where I live.

The problem with a power cut is it is just the same as yanking the power cord from the PC. Whatever process or file access is in process will just stop mid way with very unpredicatble results.

Once you have a UPS device you will need to install APCUPSD. This programme starts a service that monitors your UPS. With this you can specify the time to smart shutdown in the event of a power interruption.

A good idea.
But I still got problems, some or most apps take an age to open.

---

### Post by Bigbluecat on 2006-10-08
OK.

Well I'm still very much a noob here. Looks like we joined up about the same time.

The thing is we don't know what files may have been corrupted.

I did a quick search on repair and found the following:

[http://www.ubuntuforums.org/showthread.php?t=209443&highlight=repair+ubuntu](http://www.ubuntuforums.org/showthread.php?t=209443&highlight=repair+ubuntu)

It may or may not help. Maybe someone with a little more diagnostic experience will chip in.

By the way - which packages are slow to start? 
Is it consistently the same packages?
Have you tried to uninstall and purge them and then re-install?

---

### Post by Old Pink on 2006-10-08
> **pod25 said:**
> Thankyou, Ctrl + Alt + Backspace, did the job, I'm now back into my desktop, and everything seems to be working.

But what caused this ?  and will it happen again ?

Glad to hear I helped. :) 

Seems, as people have already explained, something running/being edited was interupted by the cut, and it just took a little fiddling to get it sorted again. 

Buy a UPS if your work is important, but don't dish out the cash if your happy with the possiblility of having to fiddle for 10-30 minutes after a power cut. :)

---

