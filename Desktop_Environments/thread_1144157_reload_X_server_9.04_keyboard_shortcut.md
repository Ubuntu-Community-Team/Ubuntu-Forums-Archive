---
title: "reload X server 9.04 keyboard shortcut"
date: 2009-04-30
forum: Desktop Environments
---

### Post by Tobywuk on 2009-04-30
In Gutsy I used to use a keyboard shortcut (cant remember what it was) to reload X server settings and log back into ubuntu.

For some reason this keyboard shortcut is no longer working in 9.04. is it available and if so what is the shortcut?

thanks.

---

### Post by bhaverkamp on 2009-04-30
It was Ctrl-Alt backspace. Yes, i have noticed that too. You can always switch to a console and do 'sudo /etc/init.d/gdm restart'

---

### Post by brookie on 2009-04-30
hello,

the jj 9.04 release notes stated that the ctrl-alt-backspace was disabled by default. you can read it here: 
[http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904")

they also give a way to enable it. hope this helps.

"Ctrl-Alt-Backspace disabled by default in Xorg

The Ctrl-Alt-Backspace key combination to force a restart of X is now disabled by default, to eliminate the problem of accidentally triggering the key combination. Users who do want this function can enable it in their xorg.conf, or by running the command dontzap --disable."

intrepid is running great for me on my machines so i probably won't upgrade until there is no more support for intrepid next year. 

hope the release notes help you with any other issues you might have with the new release and good luck tweaking your new system. 

cheers,
brookie

---

