---
title: "blank screen after dual moniter reboot - help!!!"
date: 2009-05-10
forum: Desktop Environments
---

### Post by zachthejones on 2009-05-10
I was trying to get ubuntu (intrepid) to work on two moniters - my laptop's screen and our HD TV. It detected the Sony TV just fine (plugged in through a monitor cable). Yesterday I ran it, and just used the checkbox for "mirror the screens", but today I wanted to try using both as different moniters. So I didn't check the "mirror screens" button, but turned on the second moniter (TV), with the correct resolution... a screen popped up saying that it would have to edit a configuration file to do the action and did I want it to? I clicked yes, it asked for my password, and I entered it.

Then  it told me to log out and back in. When I did, everything seemed to load fine, but when it finished, the screen was blank. Well, almost blank. it was the cream-ish gnome color. I could open a program (using gnome-do...just typing in and hitting enter, never actually seeing a thing), and the program would open, and I could switch to it using my compiz shortcuts.

But I can't use the laptop like this. I've tried booting in Xubuntu, Kubuntu, and gnome-safe and it's all the same.

Is there a way to boot into the terminal and then edit this config file? I'm not even sure what the file is called or where it is, but I'm thinking I could edit it if you could point me in the right direction and tell me what to reset...

thanks!!!

---

### Post by exutable on 2009-05-10
Have you tried fixing your x by going into recovery mode?

If you have already tried that then attempt thiss

trying hitting alt-f1, and then editing xorg.conf using the command "nano /etc/X11/xorg.conf

---

### Post by zachthejones on 2009-05-10
Thanks for your quick response! It took me a bit to resort to the recovery mode - wish I had done that sooner! The GRUB recovery mode did the trick, just selected it from the GRUB boot menu and let it run, and then choose to just boot as normal. Everything worked great!

thanks for the help. I had tried to fix the xorg.conf file and ended up screwing it up enough that it was just booting to a terminal prompt - no gui whatsoever!

thanks again!

---

