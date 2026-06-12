---
title: "Help with MP3 Encoding... (Grip)"
date: 2005-12-22
forum: General Help
---

### Post by XtremeGamer99 on 2005-12-22
Alright, I followed the instructions here:

[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

To enable LAME support for gstreamer. The encoder works well for programs like Sound Juicer CD Ripper and "CD Player and Ripper". However, I recently found this other CD playing/ripping software that seems much better and more versitile: Grip. However, I can't find out how to rip to MP3. Here's what I currently have for the settings:

[http://xgamer.insder.com/bleh/grip.png](http://xgamer.insder.com/bleh/grip.png)

Now, everytime I try to "Rip + Encode", an error comes up:

Invalid encoder executable.
Check your encoder config, and ensure it specifies the full path to the encoder executable.

Not, /usr/bin/lame does not exist, so that's the main problem. But I want to know how I can make MP3 encoding work for this.

Thanks...

---

### Post by ILikeLinux on 2005-12-22
Looks like that you have not installed lame. Do the following:

Open synaptic. Click on the search, type lame. If it finds lame, 
right click on that and select install and then click on apply. 
Once lame is installed it should be fine. 

If synaptic does not find lame, you have to add repository, 
which has lame. It is in the multiverse repository. If you look 
at the file 
/etc/apt/sources.list
you will see something like this:

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

If it's uncommented (without the hash sign in the beginning), 
this means the repository is enabled. If not, in synaptic you can enable
it. Alternatively, from a command line

sudo gedit /etc/apt/sources.list

Remove that hash, save. Open syanptic, reload the sources. 
You should now find lame, then follow the same steps as at the top.
Hope this helps.

---

### Post by XtremeGamer99 on 2005-12-23
Thanks a bunck. It worked!

---

