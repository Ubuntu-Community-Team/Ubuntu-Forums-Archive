---
title: "how do i change the directory for a driver that i downloaded?"
date: 2009-03-22
forum: General Help
---

### Post by louislmao on 2009-03-22
i need to know how to change the directory for a driver that i downloaded

i downloaded a driver for my microsoft vx1000 webcam and im trying to install it but i have to put in the directy into a termainal but i have no idea how to find it or change it :confused:

im a complete noob at ubuntu so i really need help!!!
thanks


[COLOR="Lime"]-problem solved thanks to adult swim :D[/COLOR]

---

### Post by Cheesehead on 2009-03-22
copy: $cp /path/to/current/file path/to/destination/
move: $mv /path/to/current/file path/to/destination/

---

### Post by louislmao on 2009-03-22
im sorry can you dumb it down a bit
i mean im really NOOB

i have no idea what all that means

---

### Post by adult swim on 2009-03-22
could you post a link to what you have used for help so far?

---

### Post by louislmao on 2009-03-22
[]("http://ubuntuforums.org/showthread.php?t=1034988")

i used what leachyboy2001 posted and im stuck on "# cd v4l..."

---

### Post by mb_webguy on 2009-03-22
> **louislmao said:**
> []("http://ubuntuforums.org/showthread.php?t=1034988")

i used what leachyboy2001 posted and im stuck on "# cd v4l..."

I'm assuming that leachyboy2001, whoever he is, said that in a different thread, since I don't see any posts by him in this one.  Could you provide a link?

---

### Post by adult swim on 2009-03-22
if this is what you were looking at ```
I opened a shell as root on my system and:
# wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz
# tar zxvf tip.tar.gz
# cd v4l... (whatever the newly created directory name is)
# make all
# sudo make install

then I edited /etc/modprobe.d/blacklist-custom and added:
blacklist sn9c102

# reboot 
``` 

you will want to enter into the terminal ```
cd v4l-dvb-9ff1068bedf9
```
a neat trick in the terminal is to type the first few letters of a file name and then hit the tab key.  for instance if you type cd v4l and then hit the tab key, it will finish the rest of the file name for you.

---

### Post by louislmao on 2009-03-22
yea thats what i was looking at
thanks adult swim its going now

but imma going to go ahead and ask in advance
how do i do the whole backlist part of that post???

---

### Post by adult swim on 2009-03-22
run from the terminal ```
gksudo gedit /etc/modprobe.d/blacklist
``` and when the new window opens up, scroll down to the very bottom of the file and add a line that says ```
blacklist sn9c102
``` then save and close the file

---

### Post by louislmao on 2009-03-22
ok
thank you adult swim
that helped alot
:D

its still going so i just have to wait

thanks again!!!

---

### Post by louislmao on 2009-03-22
-_- i hope someone is still around cuz i have another problem

when i put "sudo make install"
it asks for "[sudo] password for (username):"
when i try to enter a password it doesnt show up as typing so i have no idea what to do

[COLOR="Lime"]*scratch that i got it*[/COLOR]

---

