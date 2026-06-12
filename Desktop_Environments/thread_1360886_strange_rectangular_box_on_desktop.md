---
title: "strange rectangular box on desktop"
date: 2009-12-21
forum: Desktop Environments
---

### Post by stinkiestbink on 2009-12-21
hello friends. i recently installed xubuntu 9.10 and have thus far only experienced this one issue. randomly a rectangle shaped box pops up in the upper right corner of the desktop. it is blue like the background and i am unable to move it. eventually it goes away but after a while, it comes back. sometimes, when the laptop goes from ac to battery and back, it pops up again. i have yet to catch a screen shot of it. i have seen some screen shots with a volume box that is about the same size and location; if that is it, why would it be blank? any ideas?

Thanks

---

### Post by onyxwolf on 2009-12-21
Is it blue like the background or just transparent?
Does it look something like this (if your using a top panel it will appear just below the panel.):
[IMG]http://lh6.ggpht.com/_ReGMhHpqTE8/Sy_BhqykJdI/AAAAAAAAAF8/FRfwq00eoiU/Screenshot-10.png[/IMG]

Because that is just a notification box. It may be slightly different in XFCE (I'm using Gnome) but as you can see that is were it notifies of volume change as well:
[IMG]http://lh4.ggpht.com/_ReGMhHpqTE8/Sy_C0YbfRMI/AAAAAAAAAGE/lzDp3O_6VvM/Screenshot-11.png[/IMG]

There may be some miscommunication between the system and the notification daemon. Try sudo apt-get install libnotify-bin
then try the command notify-send "Message", so the command I used for the first image was--

~$ notify-send ????

And let us know the results.

PS: Again this is all in Gnome but I would imagine that the notification daemon is the same so the notify-send should work correctly

---

### Post by stinkiestbink on 2009-12-21
so i did all that and it did pop up that broken box when i ran "notify-send ????". however, i am unable to get a screen shot. what do you think the comm issue is? thanks for the response.

---

### Post by mister_p_1998 on 2009-12-23
I got that, I think its the wifi notification box, it displays ok on Gnome, but its blank on Xubuntu.

Steve

---

### Post by onyxwolf on 2009-12-23
I honestly don't know what the problem could be. I don't understand daemons (particularly the notification daemon) to be of help there, BUT half the battle is identifying the problem. The next step is to see if other people are experiencing it (and apparently mister_p_1998 had). If their are, its time to report it as a bug! THOSE NASTY LITTLE CRITTERS NEED EXTERMINATED ASAP!!! (and its fun to hear them squish!) :P

---

