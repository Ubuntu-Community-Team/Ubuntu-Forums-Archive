---
title: "No GUI since latest update - X breakage"
date: 2010-08-30
forum: Desktop Environments
---

### Post by Luis_com_Z on 2010-08-30
Hi guys!

I'm running Ubuntu 10.04 x64 on a Core i7 with a EVGA Nvidia 260 video card (with the nvidia-current driver). This weekend I was offered several updates by the update manager, and I blindly applied all of them. The update completed successfully (or so it seemed), but after a while I found out that I couldn't interact with the desktop or the panels anymore, or launch new programs, only the applications that were already running prior to the update were responding. I was forced to do a hard reboot, but when the system came back on, the login screen didn't show up correctly. All I see now is the login background (in the right definition, 1400x900), the mouse cursor, and a flickering white box where the user name and password fields were suposed to be. I can boot to the console alright, but I've already tried the usual stuff like running dpkg and things like that, to no avail. I can't start the failsafe GNOME session either, and the startx command just shows my desktop background with no icons or panels, and a flickering mouse cursor that alternates between the regular arrow and the spinning ball thingy. 

I've searched through some forums and tried some other stuff, like reinstalling the nvidia driver, but that didn't change anything. What more could I try? I'd like to try switching back to the nouveau driver, but I'm not even sure this is a driver issue or an X issue, and I'm wary of mucking things up further. Maybe I could have a clue about what went wrong if I could see what those updates were, but I don't know how to check the update log from the command line. 

I'd really like to avoid having to do a clean install because I already have a lot of files and programs and virtual machines setup with files in them, and it would be a nightmare to back it all up and set it up again. Not to mention that I have a multiple boot machine with Windows 7 and XP, and I'm using the 7 boot loader to call Grub, so if I was forced to do a fresh install of Ubuntu, that would be a whole new level of pain to setup again. I'm counting on you guys to help me figure out what went wrong and how to fix it. Thanks in advance!

---

