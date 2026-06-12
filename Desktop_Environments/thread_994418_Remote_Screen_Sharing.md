---
title: "Remote Screen Sharing"
date: 2008-11-26
forum: Desktop Environments
---

### Post by Angry Dog on 2008-11-26
I've had a search through but I cant seem to made head nor tails of what has been said? :(

I can putty into my Linux PC from XP, but when what I do from there, I don't know.

Do I need to install anything apart from openssh-sever on my linux box?

And have RealVNC on my XP PC - Do I *have* to use Tightvnc on my XP PC?

Thanks

---

### Post by Angry Dog on 2008-11-27
anyone? :)

---

### Post by mitchroberts on 2008-11-28
do you have a vnc server installed? SSH normally just provides you with a shell and allow you to administer from the command line if you use X forwarding you can run gui apps that are installed on your server on you desktop computer check out the page i posted but i thank you need a vnc server installed on your linux box also...sounds like your doing something like a terminal server?For that you need to be using
ubuntu server.or are you just try to use it as a file server?Linux can see a windows drive but windows can't see a linux drive 
for that you need to use samba.

[http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html](http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html)

also 

[http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/)


also linux terminal server setup

[http://www.telemedia.ch/publ/ltsp-howto.html](http://www.telemedia.ch/publ/ltsp-howto.html)

---

### Post by Angry Dog on 2008-11-29
Thanks, I will take a look at your links later today when I have more time :)

---

