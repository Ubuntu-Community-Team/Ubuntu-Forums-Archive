---
title: "To run a prog on startup."
date: 2006-01-18
forum: General Help
---

### Post by brakmaren on 2006-01-18
Hi
I'm trying to get Firestarter and gaim to autostart.
This is my 'Start Program' in 'Sessions'.
-
sudo usr/sbin/firestarter --start
gaim --start
-
When i start, they don't :-(
And in current sessions' they are listed with a trashcan !!!!!
Any ideas?

---

### Post by kane77 on 2006-01-18
I have gaim set up to start on startup and it works but I only used "gaim" without the --start tag. You might try that...

---

### Post by brakmaren on 2006-01-18
Thank's. That solved Gaim.
So that leaves Firestarter. How do i get it to autostart ?

---

### Post by Didjit on 2006-01-18
[quote=brakmaren]Thank's. That solved Gaim.
So that leaves Firestarter. How do i get it to autostart ?[/quote]

Did you try opening Firestarter, then logging off choosing the "Save Session" option?

Chris

---

### Post by Horndog on 2006-01-18
[QUOTE=brakmaren]Thank's. That solved Gaim.
So that leaves Firestarter. How do i get it to autostart ?[/QUOTE]

Try looking [here.]("http://www.fs-security.com/docs/faq.php#trayicon")

---

### Post by kaamos on 2006-01-18
> You can set firestarter to start up at boot in the firestarter preferences. The gui is only a tool to change the settings and to view at logs. So just choose that setting and you're good to go, no need to hassle with anything like this. :)

More stuff here: [http://ubuntuforums.org/showthread.php?t=116140](http://ubuntuforums.org/showthread.php?t=116140)

---

### Post by brakmaren on 2006-01-18
Sorry fellows, you where right. It WHAS up and running.
I just expected the icon to apear as it does when i started it manualy.
Me happy now :-)
Thank's

---

### Post by SickTwist on 2006-01-18
sudo is a commandline tool--you won't see the prompt to enter your password if you start firestarter like that. Try gksudo instead:

gksudo firestarter

However, let me mention as someone else already has that Firestarter is just a configuration GUI for the Linux firewall. Once you install Firestarter and set up the firewall, the firewall starts automatically during boot.

---

### Post by Wolfbite on 2006-01-25
BTW, what's the name of the process of the firewall, just so I can rest assured that it is indeed there? ^^

---

### Post by aliencds on 2006-02-11
it should say "firestarter" i believe

---

