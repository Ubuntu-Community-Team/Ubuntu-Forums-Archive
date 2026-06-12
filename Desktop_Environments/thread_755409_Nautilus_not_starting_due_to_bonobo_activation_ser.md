---
title: "Nautilus not starting due to bonobo activation server"
date: 2008-04-14
forum: Desktop Environments
---

### Post by Ryan Scott on 2008-04-14
Hi,

Im running Gutsy Gibbon on a Dell Inspiron 1520 and when booting this morning i got the following two errors:
     The panel has encountered a fatal error- the panel could not register with the bonobo-activation          
     server (error code:3) and will now exit. It may be automatically restarted'

and
   
    Nautilus cannot be used now due to an unexpected error.

Doing some research i see that this is common in Apple PPC Users due to a hardware clock issue, i tried to set the hardware clock to the current system clock which did not work. Also reinstall nautilus and the bonobo libraries from synaptic. Also seems that sometimes its to do with an interrupted shutdown or battery running flat, none of these happened. Any help would be greatly appreciated.

Cheers,
Ryan Scott

---

### Post by maxpep09 on 2008-04-25
im running hardy heron x86 and im getting the same error.

---

### Post by tcauduro on 2008-04-25
I was getting this error after upgrading to Hardy Heron.  I had to uninstall mono 1.2.x to get it to function properly.  I haven't tried reinstalling it yet to see if it becomes broken again, but for now I can at least use my gnome environment.

Hope this helps!

---

### Post by Kenda on 2008-04-26
I think I have had something very similar today with Hardy. Nautilus broken and reference to bonobo activation server. It's ok now but I don't know why or whether it will happen again.

---

### Post by rhombus on 2008-04-26
I had the same problem after upgrading from Gutsy to Hardy.

I was able to start a session using the menu at the bottom-left of the login window and selecting Gnome failsafe mode.

I tried uninstalling all the Mono 1.2x packages from Synaptic (since Bonobo is part of Mono I guess) and tried reinstalling Nautilus, but neither helped.

After searching a while I realized that I had installed Mono 1.9 previously, and since I only formatted my OS partition and not the one reserved for my /home folder, somehow Mono 1.9 was still installed. There is an uninstaller in the Mono 1.9 folder. I ran that, rebooted, and I was able to start a normal session, no errors. I reinstalled Mono 1.2x from synaptic as well and everything has been running smoothly since then. I don't know if this is the case for everyone getting this error, but it helped me, so check if you have a wayward Mono 1.9 installation somewhere.

-e

---

### Post by kkroculick on 2008-04-26
I received the same error. I removed mono-1.9 from home directory and everything worked fine.

---

### Post by zariok on 2008-05-02
You do not have to unistall mono-1.9.  Just remove the references, namely in PATH, from your ~/.bashrc file so Gnome uses the installed 1.2.6.

---

### Post by dennis2008 on 2008-06-11
Now if you follow the instructions on 
[http://www.mono-project.com/Other_Downloads](http://www.mono-project.com/Other_Downloads)
to update to mono 1.9 from 
[http://directhex.mfgames.com/](http://directhex.mfgames.com/)

it won't cause crash.

Best,

---

### Post by glok_twen on 2008-06-29
thanks i spent hours with this problem and the simple mono-1.9 uninstall fixed it.

---

