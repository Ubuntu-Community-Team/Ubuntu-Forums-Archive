---
title: "Ubuntu 9.04 no gnome panel and no ALT+F2"
date: 2009-07-29
forum: Desktop Environments
---

### Post by rv65 on 2009-07-29
I have a Ubuntu 9.04 64 bit install that has no gnome panels. I also have no ALT+F2. I can't even make a desktop shortcut. I've used the failsafe gnome and still no panels. Any help would be great.

---

### Post by gettinoriginal on 2009-07-29
First, try rebooting and at the sign in screen, lower left corner choose "options" > select session > gnome > change session, then sign in as usual.

---

### Post by asmoore82 on 2009-07-29
by any chance, have you tried out the netbook-launcher on this machine?

---

### Post by rv65 on 2009-07-30
> **gettinoriginal said:**
> First, try rebooting and at the sign in screen, lower left corner choose "options" > select session > gnome > change session, then sign in as usual.

Still not working. I could try netbook-launcher but I can't access synaptic. I'll try that.

---

### Post by Brandon Williams on 2009-07-31
I think that what asmoore82 was really asking is whether you've tried out netbook-remix. The UNR desktop-switcher in Jaunty was (and perhaps still is) buggy, and would cause this type of problem. If you _had_ tried it out, that would make it easier to suggest a fix. It sounds like you haven't used it, so that won't be the problem.

Alt+F2 is a function of the panel, so if the panel's not there, Alt+F2 won't work either. I suggest that you create a launcher on your desktop so that you can start gnome-terminal. Just right-click on the desktop and select the appropriate item from the popup menu.

Once you've got a terminal running, execute gnome-panel from the command line. This should give you a panel to work with. Does that work? If so, then I think we just need to figure out why it isn't autostarting.

---

### Post by UbuntuNerd on 2009-07-31
can you tell me what happens if you press Ctrl+Alt+f2 hit ctrl+alt+f7 to get back to your desktop :)

---

### Post by rv65 on 2009-08-13
When I try to run gnome-panel from the CLI it says no libasound.so.2 file. I think I tried to run some version of ALSA and it borked it. I have a noALSA and noOSS blacklisted. I tried to set linux-sound-base to OSS. I think thats the reason why it wont run gnome. All because of a stupid little file.

---

### Post by rv65 on 2009-08-14
any response?

---

### Post by rv65 on 2009-08-16
In my lib folder I find a noALSA and a noOSS script. Can I remove them from the blacklist and remove those files. I think those files and possibly reinstalling ALSA could fix my problem I hope.

---

