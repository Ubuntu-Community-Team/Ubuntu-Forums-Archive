---
title: "Monitor has no signal!"
date: 2009-02-15
forum: General Help
---

### Post by hulio40 on 2009-02-15
Hello, i recently reconfigured my xorg.conf due to some problems and it auto detected everything for me.

when i reboot the computer, as X is about to start, monitor says "no signal" and shuts down but the computer continues running. what do i do? i know this is related to some error in xorg.conf, also please explain toroughfully because im quite  a noob... thanks

---

### Post by indeterminate on 2009-02-15
If you boot from the CD, under the options for Repairing a broken system, there should be an option to fix your xorg.conf file. I think. I've never actually done it.

Alternately, if you hit CTRL-ALT-F2 after it gives you that "no signal" message, it should drop you to another TTY where you can login to the console. If you're feeling ambitious, you can navigate to your /etc/X11/xorg.conf file and edit it directly with nano/pico/vi/emacs/whatever. 

Good luck! Keep us updated.

Edit: oh yeah, if you're lucky, the autoconfiguration will have saved a backup copy of your old xorg.conf in the /etc/X11 folder, and you can replace the newer broken one with it.

---

### Post by hulio40 on 2009-02-15
erm, thanks for the reply but i fixed the problem, don't know how but it's all good now :S


Typing from that computer right now :)

---

