---
title: "Cant log on Hardy"
date: 2009-03-20
forum: General Help
---

### Post by ultimate_aektzis on 2009-03-20
Hi guys.

I tried to log in to my ubuntu before some minutes and when I entered my username and password I saw two messages which at last didnt allow me to ente the system.These messages were(in free translation as I dont have English ubuntu)

> The file $HOME/.dmrc doesnt have valid privileges and cannot be found.This blocks the store of your default language and session.The file should belong to the user and have 644 privileges.&#932;he directory of the $HOME user should belong to the user and not to be writable from other users.

And after a while

> The gnome system administrator cannot lock the gile ~/.ICEauthority.Sometimes this happens because the file directory is ont writable.Login from failsafe and ensure that it is not.

I didnt edit anything from yesterday.I would be grateful if someone could help me.

---

### Post by lykwydchykyn on 2009-03-20
I've seen this message before when my /home partition would not mount correctly.  Try hitting ctrl-alt-f1 to go to a virtual terminal and try logging in.  Then type "ls".  If your home directory looks empty, then probably the partition isn't mounted.

The other possibility is that the drive is full and preventing you from logging in because it can't write to /tmp or /home/.  You can determine this with the "df" command.

---

### Post by ultimate_aektzis on 2009-03-20
I tried to change the privileges of my home directory.I typed chown -R user.user /home/user as root and the problem solved.Good experience:D

---

### Post by ultimate_aektzis on 2009-03-21
As I said previously, I solved the problem and logged in.But it seems that solution was temporary.the same problem apperared when I opened again my ubuntu, and I solved it with the same command.Can you tell me something on how to solve it permanently?

---

