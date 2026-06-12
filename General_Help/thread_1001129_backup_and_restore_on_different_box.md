---
title: "backup and restore on different box?"
date: 2008-12-03
forum: General Help
---

### Post by firsttimeuser on 2008-12-03
Hi there, 

I have been testing ubuntun for a while, and so far really like it. 

The laptop used to test drive is a pretty old one, and am thinking about getting unbunt on my new laptop, so here I have this question:

Is it possible somehow I can backup all my current setting and installed applications and restore them to another laptop?

I think copying all my home dir over can partially address this request, but the thing is, there are some apps not being installed under my home directory, what can I do for those ones?

---

### Post by Idefix82 on 2008-12-03
Copying the home folder will, as you said yourself, deal with the settings. If you want to transfer the installed applications, the easiest thing is to copy the downloaded package files into the new installation and then install them again through Synaptic. You will still have to install, but you won't have to download them again.

If you want to do that, just copy the content of the /var/cache/apt/archives folder on the old laptop into the same folder on the new installation.

---

### Post by firsttimeuser on 2008-12-03
> **Idefix82 said:**
> 
If you want to do that, just copy the content of the /var/cache/apt/archives folder on the old laptop into the same folder on the new installation.

this sounds really cool, and I just took a look under that dir, and it seems all the applications are there..

So basically I just copy all the files under this dir over to the new laptop, and fire "sudo apt-get update" ?

---

### Post by Idefix82 on 2008-12-04
> **firsttimeuser said:**
> this sounds really cool, and I just took a look under that dir, and it seems all the applications are there..

So basically I just copy all the files under this dir over to the new laptop, and fire "sudo apt-get update" ?

Exactly. Be sure to copy them into the folder with the same name on the new installation.

---

### Post by firsttimeuser on 2008-12-04
thank you and one THANKS! :)

---

### Post by mixmaster on 2008-12-04
You could also try remastersys.

It allows you to create an live cd/dvd customised to your setup which can be used to install a clone on another machine with all settings and installed software preserved.

See here for more info :
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by scouser73 on 2008-12-04
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

