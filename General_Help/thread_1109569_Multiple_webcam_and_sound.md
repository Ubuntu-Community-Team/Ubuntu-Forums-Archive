---
title: "Multiple webcam and sound"
date: 2009-03-28
forum: General Help
---

### Post by mikedmor on 2009-03-28
All of my friends just recently install ubuntu over top windows so have completely converted. Now they are really new to all of this and i have been using ubuntu for some time now so im helping them out. they just went out and got webcams to chat and i was hoping to chat with them and show them what they need to do (so really teach them).

My problem is i have no idea where i can find a application for ubuntu that will allow me to stream my webcam to multiple people at once, as well as them able to stream to eachother, like a conference call except with video as well.

we currently use skype to conference call but we want our webcams to work just like that. any ideas of a program or how to get this working?

---

### Post by mb_webguy on 2009-03-29
Both Ekiga (as of v3.0) and Skype (as of v2.0) support video conferencing.

---

### Post by mikedmor on 2009-03-29
we use skype, but it wont allow us to turn on video in a conference. We conference on it all the time but its only working for sound. How to we get the video working?

---

### Post by duke.tim on 2010-04-22
Skype doesn't currently support multiple user video conferencing. I have been working on the problem a bit have have just posted a new thread. check it out you might be able to do this!

[http://ubuntuforums.org/showthread.php?p=9157671#post9157671](http://ubuntuforums.org/showthread.php?p=9157671#post9157671)

---

### Post by duke.tim on 2010-04-24
Just a quick preview of what i've found that works so far.
assuming that you are using at least ubuntu 9.10 

#1 remove pulse audio
#2 create multiple login accounts
#3 ```
xhost +local:accounts
``` repeat for the diffrent accounts
#4 create short cuts or run from the shell
```
gksu -u username skype /secondary
``` repeat with diffrent usernames to open various windows.
#5 call various people one by one and share screen.

---

