---
title: "system crashing every 5 minutes....please help"
date: 2010-10-09
forum: Desktop Environments
---

### Post by abelito8 on 2010-10-09
Hi there, 

I am using ubuntu 10.4 on a Sony vaio and I never had troubles with the previous versions...just in those days something strange is happening. With no apparent reason, few applications running, the system will just freeze...sometimes I would be able to open a further application, some other things not. I have tried everything (in my knowledge)...after which I simply use Alt F2, call the terminal and reboot (the only operation that the system will allow me to do

I have found no pattern of behaviour but his has happened with the following application running

Firefox, Openoffice and Rhythmbox
Firefox and Torrent
now Firefox alone (yes it might be firefox...but still, if I am not wrong it happened also when firefox was shut and I was working on openoffice)

now I have logged on into xfce environment to write this message (and I am using Midori as browser)...but I am really puzzled...could this be a bug?

---

### Post by roggenschrotbrot on 2010-10-09
since you are able to open other programs (if i got you right there) its probably either firefox or (less likely) nautilus freezing. could you elaborate what exactly you are able to do once this happens? in case it is firefox it might be a addon running amok. try to disable all and see if your system still freezes.

ps: if you session freezes you can hit "alt"+"print"+"k" to kill your current xsession without having to reboot.

---

### Post by abelito8 on 2010-10-09
Thanks for your reply

do I have a button "print" on my keyboard? I've never seen it (ctrl-print-k you suggest...)

and sorry for the ignorance, xsessions are not only the sessions you run in xfce? This was happening in a gnome environment

when a programme freezes the mouse and touchpad get crazy immediately

there are two possibilities, in a lucky version of my freezing I could press ctrl+A, ctrl+C and paste the text I was using into OOwriter, did not save it but I could recover it the next session

in an unlucky version everything gets mad but I can still use ctrl+F2, call the terminal and ask to reboot

in the worse scenario I just have to press the start button until the computer shuts down

---

### Post by abelito8 on 2010-10-09
...and I basically have no add ons in Firefox...I have zotero and ubuntu firefox modifications package 0.9rc2

---

### Post by roggenschrotbrot on 2010-10-09
> do I have a button "print" on my keyboard? I've never seen it (ctrl-print-k you suggest...)
depending on your keyboard layout it should be somewhere near pageup/pagedown/pause. if you are using a netbook it might be a fn-key.
edit: [http://en.wikipedia.org/wiki/File:KeyboardWithPrintScreenRinged.svg]("http://en.wikipedia.org/wiki/File:KeyboardWithPrintScreenRinged.svg") /edit
edit2: oh, and it should be altgr+printscr+k /edit2
> and sorry for the ignorance, xsessions are not only the sessions you run in xfce? This was happening in a gnome environment
its used to run any desktop environment, killing it will get you back to your login screen.
> when a programme freezes the mouse and touchpad get crazy immediately

there are two possibilities, in a lucky version of my freezing I could press ctrl+A, ctrl+C and paste the text I was using into OOwriter, did not save it but I could recover it the next session

in an unlucky version everything gets mad but I can still use ctrl+F2, call the terminal and ask to reboot

in the worse scenario I just have to press the start button until the computer shuts down
sounds like something is causing 100% cpu-load. run gnome-system-monitor to monitor you cpu-load for a while. once your lockup happens one program will cause a 100% or near 100% usage.

---

### Post by abelito8 on 2010-10-09
ok found the print key, found system monitor, will keep an eye on it, thank you

---

