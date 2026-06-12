---
title: "Making programs run at startup"
date: 2006-09-02
forum: Desktop Environments
---

### Post by eeefresh on 2006-09-02
I've tried adding "gDesklets" and "gmail notify" to the menu under System > Preferences > Sessions > Startup Programs, yet neither of them are starting up when I reboot.  Am I missing something?  How can I add these programs to start when the compter is booted?

Thanks in advance!

---

### Post by Illusionistx on 2006-09-02
you most likely didn't type in the right name for each

---

### Post by Malac on 2006-09-02
Under System > Preferences > Sessions > Session Options have you got "Automatically save changes to session" ticked if not Gnome may not ask you if you want to save the changes so it isn't.
That's all I can think of at the moment.

---

### Post by eeefresh on 2006-09-02
Illusion - is there a way to find the exact name to use?  I am used to Windows, where everything is a ABC.exe file...

---

### Post by Illusionistx on 2006-09-02
i usually make a shortcut/launcher on the desktop then right click > properties and see what the launch command is. there might be an easier way but that's just how i do

---

### Post by eeefresh on 2006-09-02
But where are the original files that you are creating the shortcut to?  Where are they stored after the install?

Sorry, I am a Linux noob.

---

### Post by eeefresh on 2006-09-02
Bump

---

### Post by eeefresh on 2006-09-02
Bump

---

### Post by max_dingemans on 2006-09-03
While this may just be something that you've typed differently into the forums,the d in gdesklets shouldn't be capitalized. Case sensitivity can be a pain in the behind for sure.

And upon searching the repositories, it looks like gmail-notify has a hyphen between the words, rather than a space. I don't actually have it installed so I can't check that out for sure though.One way to be sure is to hit alt+f2 (the 'run application' dialogue) and start typing the name of the program you want to start. If the program is recognized, it will often be autocompleted before you finish typing.

To answer your other question, Most programs have links to thier launchers stored in /usr/bin. So if I wanted to run gaim, for example, when I logged in I could add either simply 'gaim' or the full path: '/usr/bin/gaim'.

---

### Post by hraposo on 2006-09-03
Try:
gedit /etc/rc.local
comment (add # at begin) exit 0 (#exit 0)
then put in rc.local one line with the command of the application you want open on boot

---

### Post by eeefresh on 2006-09-04
Thanks, Max!  It was the typo that was causing the problem.  Also, thanks for the Alt-F2 tip.  That was new to me!

---

