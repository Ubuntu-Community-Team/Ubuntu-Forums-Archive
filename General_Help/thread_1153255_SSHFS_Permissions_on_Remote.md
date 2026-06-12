---
title: "SSHFS Permissions on Remote"
date: 2009-05-08
forum: General Help
---

### Post by pgn674 on 2009-05-08
I have a regular Ubuntu machine in front of me, and an Ubuntu Server machine way far away. To edit files on it, I usually use Nano (haven't gotten into vi or emacs yet). But, I miss some things that GUI text editors provide, like color and mouse stuff.

So, I installed SSHFS here, and it works fine for editing files that my user account on the Ubuntu Server owns (namely, anything in that user's directory). However, I also need to edit some files that I would normally use "sudo nano" for. When I try to save those files, it says I don't have permission.

I use "sudo sshfs [email]XXX@YYY.com[/email]:/ /media/server" to do the mounting, where XXX is the user on the server. I can't log on to the server as root, since Ubuntu has disabled that and I don't want to fiddle with it; I like that kind of security.

Would anyone know how I can get sudo ability over SSHFS? I looked around online, but it seems that whenever someone asks a question like mine, they end up going a different route.

---

### Post by spiderbatdad on 2009-05-08
I connect normally like: ssh user@address then run sudo nano or sudo -i.
Also have xfce installed on the server, so I can connect like: ssh -X user@address. Then I can launch thunar or mousepad, as root if desired.

---

