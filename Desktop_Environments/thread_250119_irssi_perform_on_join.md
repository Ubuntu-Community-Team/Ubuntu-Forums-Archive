---
title: "irssi perform on join"
date: 2006-09-03
forum: Desktop Environments
---

### Post by someusernoob on 2006-09-03
Ok, i used to use mirc for a long time, and i always had some stuff in my perform file. when i entered a server or a channel it would automaticly change my nickname, set a topic title, just any command you wanted.

I want this for irssi, ive been looking for hours now, through the scripts that are available, man files and other things i found with google, but i cant find it. Can someone help me out, im really getting tired of typing things manually while it used to be automaticly. :-k  Or am i asking something stupid right now?

---

### Post by ayoli on 2006-09-03
edit ~/.irssi/config look for channels section, should look like this
```
channels = (
  { 
   name = "#irssi"; 
   chatnet = "ircnet"; 
   autojoin = "No"; 
   [COLOR="Red"]autosendcmd = "/nick my_killer_nick";[/COLOR]
  }  
);
```
the [COLOR="Red"]red line[/COLOR] is an example of an automatic command which will be sent on joining the channel.

---

### Post by someusernoob on 2006-09-03
Ok, thank you so much.

I looked in the config file before, but didnt know what to add... ](*,) 

This is working great and exactly what i needed!

---

