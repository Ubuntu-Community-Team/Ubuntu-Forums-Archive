---
title: "I need a script for my CSS serv"
date: 2009-01-27
forum: Gaming &amp; Leisure
---

### Post by Millz on 2009-01-27
Hi there. First off I just want to say this site has been extremely helpful for whatever problem I've been having this far, but I just ran into one I couldn't find any help with. I then decided to make a new topic :)

So, I installed a CSS source dedicated server on my ubuntu server. Everythings running fine, but I would really like to get some help making some sort of script for starting up the css server. I got no experience doing scripts, as I am a pretty new to Linux, and especially the whole console thing :P

So, when I downloaded the server, it came with what I guess is a run script for it. Its srcds_run file. My putty display it in green text. If you want what's inside it, let me know, but it's very long.. I guess it would be a whole sheet of text, and I didn't figure out how I could copy it all, sorry :P


So if anyone could provide me with some help on making a script that will run my server at 66 tickrate, max players 24, no autoupdate (as it takes ages for it to start up then), ip 88.84.178.217, port 27015.

Thanks a lot :) Just let me know if there's any more info you need.. :p

---

### Post by Vadi on 2009-01-27
More info is needed, yes. How do you set those values?

---

### Post by Millz on 2009-01-27
I use this line to start my server:

```
screen -S css ./srcds_run -console -game cstrike -port 27015 +ip 88.84.178.217 +map de_dust +maxplayers 24 -tickrate 66
```

millz@serv2:/home/server/css$ uname
Linux
millz@serv2:/home/server/css$ uname -r
2.6.27-7-server

---

### Post by Vadi on 2009-01-27
So to make the script, make a file called "script.sh" or something with this text:

> screen -S css ./srcds_run -console -game cstrike -port 27015 +ip 88.84.178.217 +map de_dust +maxplayers 24 -tickrate 66

Then do "chmod +x script.sh" (to allow it to be executed as a program) and you can then just use "./script.sh" to run it.

---

### Post by Millz on 2009-01-27
Thanks a lot! :D

It's great now! This is exactly why I loooove these forums :) :)

---

### Post by Vadi on 2009-01-27
you're welcome

---

