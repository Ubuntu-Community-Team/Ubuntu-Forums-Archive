---
title: "GTK-Gnutella help"
date: 2005-12-09
forum: General Help
---

### Post by Kobra on 2005-12-09
Ok, I just ran "sudo apt-get install gtk-gnutella" and it installed.  But, I can't connect to anything, and it says I'm running an older version.  What could solve this?  Me and my friend are stumped

---

### Post by Dr. Nick on 2005-12-09
You would either have to download and compile teh new version from the developers iste or wait and see if it gets backported to breezy. I have Dapper running ( new developtment release) and and using gtk-gnutella fine with 3 connections. I have gtk-gnutella/0.96b (2005-11-22; GTK2; Linux x86_64)

---

### Post by gonçalo on 2005-12-09
I have gtk-gnutella/0.95.4 and it works connects downloads and uploads. I can't browse or email or anything else because it hogs all my bandwith [I have 512 Kbs only]

I'm on Breezy.

---

### Post by Kobra on 2005-12-09
Ah, thanks.  I went to gtk-gnutella.sourceforge.net and I couldn't fine the download.  I've tweaked my sources.list last night, could that have anything to do with it?

---

### Post by Dr. Nick on 2005-12-09
[http://sourceforge.net/project/showfiles.php?group_id=4467&package_id=4479](http://sourceforge.net/project/showfiles.php?group_id=4467&package_id=4479) has download links, you most likely want gtk2 or the .tar.gz and compile manually. The souce file shouldnt make much difference I dont think. What version shows up as the newest in synaptic? And are you shure you cant connect, check and make sure all proxies are disabled

---

### Post by Kobra on 2005-12-09
Ok thanks Dr. Nick.  I appreciate it

---

### Post by conor on 2005-12-09
Go to:
```
[url]http://switch.dl.sourceforge.net/sourceforge/gtk-gnutella/GTK2_gtk-gnutella_0.96.0-0_i386.deb
```
Then download the chosen version.  The go to a terminal and type:
```
sudo dpkg --install /where/you/downloaded/it/GTK2_gtk-gnutella_0.96.0-0_i386.deb
```
Dpkg (apt) will then install it for you.  Worked for me!  Hope this helps.

---

### Post by Kobra on 2005-12-09
Thanks conor.  Your a life saver

---

