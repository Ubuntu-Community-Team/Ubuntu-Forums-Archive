---
title: "No sound in Gnome:("
date: 2005-03-26
forum: Desktop Environments
---

### Post by wxm505 on 2005-03-26
Hi , I have a problem about the sound.
I installed Ubuntu about a week ago.
everything had been running well untill this morning.
When log in the gnome it has no sound.
I am sure the
sound is working, because when the GDM login screen shows up 
I can hear the tab-beat sound effect.
There must be something worng about the gnome
configure.
When I choose the volume control it pop up 
a error message:Sorry, no mixer elements and/or devices found.
When I logged in as another user , the sound wokred well.
any help???  cheers!!

---

### Post by neighborlee on 2005-03-27
[QUOTE=wxm505]Hi , I have a problem about the sound.
I installed Ubuntu about a week ago.
everything had been running well untill this morning.
When log in the gnome it has no sound.
I am sure the
sound is working, because when the GDM login screen shows up 
I can hear the tab-beat sound effect.
There must be something worng about the gnome
configure.
When I choose the volume control it pop up 
a error message:Sorry, no mixer elements and/or devices found.
When I logged in as another user , the sound wokred well.
any help???  cheers!![/QUOTE]
---------
I have error " no volume control elements and/or devices found', although I do have most sounds working other than being able to bring up volume control ( xchat sounds wont work atm ).

l8r
nl
-------

---

### Post by gaza on 2005-03-30
hi, i'm totally new to linux. like a month old. But, I had lost all of the sound in my laptop, and a friend of mine helped me out today.

He ran alsaconf (as root), alsa connected to the internet, searched the soundcard databases and now i'm listening to music  :D 

Hope running ```
alsaconf
``` is enough for your problem.

---

### Post by wxm505 on 2005-03-31
cheers mate. I have solved out my problem.
I added audio to my main user group.
It works now:)

---

### Post by chettyk on 2005-04-21
I don't believe this! As you suggested, I included my username in the audio group and, hey presto, my laptop's audio was working. Here I have been breaking my head, trying out all sorts of other suggestions and getting nowhere. What made it doubly irritating was that audio worked when I booted from the Live CD. wxm505, I owe you a beer -- actually, as many beers as you care to drink in an evening.

---

### Post by jecepede on 2005-04-22
Ola !


the command alsaconf is not installed ?????
What package do I need for this ?




Greets


Jessy

---

### Post by wxm505 on 2005-05-10
[QUOTE=chettyk]I don't believe this! As you suggested, I included my username in the audio group and, hey presto, my laptop's audio was working. Here I have been breaking my head, trying out all sorts of other suggestions and getting nowhere. What made it doubly irritating was that audio worked when I booted from the Live CD. wxm505, I owe you a beer -- actually, as many beers as you care to drink in an evening.[/QUOTE]
hehe wonderful. I got the suggestion from friends in  the forum as well.
cheers mate

---

### Post by rsreston on 2005-05-25
In my case I had to go to Debian.org and download alsaconf_0.4.3b.orig.tar.gz. I opened it and ran ./alsaconf. It then "asked" for Alsa 0.5.0. I just opened Synaptic (or Kynaptic) and downloaded some files after looking for "alsa". Then, I reconfigured my sound options from Volume Control icon and it worked! I just ran alsaconf later just to be sure. Thanks and I hope I could help ! :D

---

