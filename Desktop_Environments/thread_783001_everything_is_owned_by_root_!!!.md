---
title: "everything is owned by root !!!"
date: 2008-05-05
forum: Desktop Environments
---

### Post by ubuntu_jazzbach on 2008-05-05
Hi !!!

I've just updated to Hardy and I have the following problem: Everything I do in Nautilus, everything does in the name of root !!! If I create a folder, its owned by root. If I want to change a network setting, I have to run the command with root, If I want to upgrade, I can't because I'm not root !!!

For example: I remember in Gutsy, whenever I wanted to change a network setting, I only had to enter the password of the current user. Now If I do this, all the options in Network Manager are disabled !!!

Please help me !!

---

### Post by ubuntu_jazzbach on 2008-05-05
I forgot to tell:

The files that I cannot rename and that are owned by root have a very strange group name: plugdev. And are not in my home. They're part of a separate partition (FAT32)

---

### Post by TheMemphisExperience on 2008-05-05
So you upgraded instead of doing a clean install? I suppose this is one of the horror stories rumored to afflict upgraders.

I'm not sure of the commands that will enable you to change ownership over to you from root, but hopefully they can be googled or someone here will post instructions. I am aware of commands that can change ownership of things like iPods(and i think they should do the same for partitions...though I don't know your setup or if chown will work for this) Also, I do not know the context "chown" needs to operate successfully, if that is a valid command.

All I can tell you is to back up your data as best you can and brace for a full install using a Hardy install/live CD. Some things aren't quite right with my own install and have been considering a reinstall myself.

Good luck.

---

### Post by DirtDawg on 2008-05-05
</clip>
Pardon, I posted on the wrong thread.

---

