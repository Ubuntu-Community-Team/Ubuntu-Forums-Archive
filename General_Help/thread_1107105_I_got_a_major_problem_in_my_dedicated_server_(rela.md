---
title: "I got a major problem in my dedicated server (related to permissions)"
date: 2009-03-26
forum: General Help
---

### Post by SanZoR on 2009-03-26
Hello people,
I recently messed up my server by changing the ownership & accessing rights.
The problem appeard when i decided to own directory /var/ to me, which was not wise. After that i recieved a lots of error messages to my ssh client, so i changed the ownership back to root.
Anyway, i think i somehow messed around with the ownerships in the other directories too, as my most of them are not accessible.
However, i decided to reboot my server, and fount that the ssh daemon didnt started at all. As far as i know, it is about the permissions, as my website is not accessable either. (my site is [www.gamenet.fi](www.gamenet.fi)) So, i googled a bit, and i MUST somehow execute this command from distance: /etc/init.d/ssh start
How the heck i am supposed to do that, if i cant access to it? :(

I really need help with it! I also need to know what are the default (working) owners & other confings in the directories called /var/, /etc/ and the other important main folders.
My server is a dedicated box located in a datacenter, which is a Co-Location service, so accessing it physically will cost and it is quite far away from me.
Sorry if my help request is a bit messy, since i just typed what popped to my mind about this issue.
Thanks in advance!
- SanZoR

---

### Post by albandy on 2009-03-26
In /var there are a lot of files owned by different users: www-data, root, cups .... you've a lot of work to do, but maybe reinstall it's a better option

---

### Post by SanZoR on 2009-03-26
Hmm...
Or maybe i just give read and write access to every group...
Anyway, is there any way i can change the permissions from distance, without ssh? Or how i can run ssh without ssh? (lol)
Anyway, i must find another way to do it...
Please let me know if you got any ideas how to fix this issue.
Thanks a lot in advance!!!

---

### Post by evilaim on 2009-03-26
The problem is this... Linux bases 99% of it's remote controls on SSH.  If you've some how disabled that, then you can't really do much about it unless you've already added VNC-server or something that will allow you to remote in.  Since you've chmod some directories and you don't seem to understand the issues with this, I would say call your DC and tell them to format it back to it's original state.  If you don't you A) have a compromised box and B) a box that most likely won't work very well for you.

Just bite the bullet and get it formatted.

---

### Post by SanZoR on 2009-03-26
I got a vnc...
But the problem is, how the hell i am supposed to execute it without the ssh? :l

---

### Post by evilaim on 2009-03-27
If you can login via VNC (which is a remote desktop protocal) you can just open a terminal and type: sudo /etc/init.d/ssh start

---

