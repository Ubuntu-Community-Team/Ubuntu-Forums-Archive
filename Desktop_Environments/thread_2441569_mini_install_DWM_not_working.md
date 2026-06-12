---
title: "mini install: DWM not working"
date: 2020-04-24
forum: Desktop Environments
---

### Post by c0rnfed on 2020-04-24
Hi,

I havent used ubuntu for a while.

I installed everything via the mini.iso.

I did not install any of the desktop packages during the setup.

After setup and installation I installed dwm and lightdm.

I rebooted and it boots to lightdm I try to login but it cannot load dwm
Then ctrl+alt +f1 and tried to "exec dwm" and nothing

how can I fix it?

---

### Post by c0rnfed on 2020-04-25
So i solved it..
I had lightdm as the login manager and it is configured to use ubuntu's unity desktop by default so all we have to do is

remove the file with command:
rm /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf


then make a new file (nano stated here but use whatever text editor you want)
nano /usr/share/lightdm/lightdm.conf.d/50-dwm-greeter.conf

and in that file that was just created write the following:

[SeatDefaults]
greeter-session=unity-greeter
user-session=dwm

---

### Post by sisco311 on 2020-04-26
Thanks for sharing your solution!

I don't think that removing the unity-greeter conf file in necessary. You can simply create a new .conf file (with a higher priority) 49--dwm-greeter.conf for exemple.


Normally I would expect that the OS(package manager) creates this kind of files automatically, but in case of a minimal install you have to do some things manually. 

It's hard to tell what happened in your case, but I'm glad you solved it.

Please consider to mark this thread as solved!

---

