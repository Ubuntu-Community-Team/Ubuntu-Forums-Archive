---
title: "audio problem / conflict"
date: 2005-04-28
forum: Desktop Environments
---

### Post by jonhewer on 2005-04-28
hi

i was, up until yesterday, running debian sarge, but decided to switch over to kubuntu.  in both distros i have been experiencing the following problem.

for some reason, as far as i am aware, only one program can play audio at any one time.  for example if i am on a website which is playing sound, and then i open up zinf to play some other music, it wont work.  and so on...

i don't think this is an application specific problem i used to use xmms instead of zinf and had the exact same problem - which makes me think its some sort of driver problem?

i have a asus a7n8x deluxe mobo with onboard sound, and in sound system the audio device is set to auto, however i see it loads up ALSA on startup.

thanks very much
jon

---

### Post by jonhewer on 2005-04-28
just found this:

[http://ubuntuforums.org/showthread.php?t=30076&highlight=nforce](http://ubuntuforums.org/showthread.php?t=30076&highlight=nforce)

but its written for ubuntu with gnome, and i'm using kde.....so i dont know if it'll work or not - any ideas?

---

### Post by jonhewer on 2005-04-28
i dont have a file called '.asoundrc' anywhere

---

### Post by heimo on 2005-04-28
[QUOTE=jonhewer]i dont have a file called '.asoundrc' anywhere[/QUOTE]

That one (if it exists) is in 
/home/username/.asoundrc

according to instructions, you can instead use this "system-wide" config:
/etc/asound.conf

---

### Post by jonhewer on 2005-04-28
i have followed the guide i linked above but it hasn't made a difference.

couple of things i'm unsure about - 

step4:

in order to select alsa in kde's sound preferences i had to enable sound system again.


step5:

i'm not sure if i installed all the dependancies of libesd-alsa0, i just did:

sudo apt-get install libesd-alsa0

---

### Post by 23meg on 2005-04-28
you can also try creating .asoundrc if it doesn't exist.

---

### Post by jonhewer on 2005-04-28
yeh i just created it myself, but i decided to use a systemwide file /etc/asound.conf

just installed synaptic, and i believe i have all of the dependancies installed

---

### Post by jonhewer on 2005-05-04
bump

---

