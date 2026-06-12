---
title: "jdownloader not starting anymore. forefox downloads not starting. ..."
date: 2012-02-05
forum: Desktop Environments
---

### Post by nico23 on 2012-02-05
Dell Inspiron 6400 newest xubuntu stable version. Crypted /home.

My System is really acting srange. Jdownloader is not starting and FF dont starts teh download. It just does nothing and the window i just got asking me if u want to update/save the stored password on forum login. I could not click it! I was able to close it but not to click it.

Last hink happening to my system was hat my disk run full again. But sadly xfce never warns me and i always figure it out later. anyway now there is a lot of space

i tryed "sudo touch /fs..." to scan my disk on startup. It scanned - no problem. In midori brower i can download.

I dont like to reinstall any suggestions?

can even dran and drop urls into FF bookmarks bar and i cant bookmark this page now in in any other way. wtf is this.

---

### Post by Rodney9 on 2012-02-05
Try ```
sudo apt-get update && sudo apt-get upgrade
```

You could try re-insatlling Firefox in Synaptic.

Try Chromium instead

Space problems see here -

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)  Thanks to drs305

Rodney

---

### Post by nico23 on 2012-02-06
suggesting another brower is not a solution. i said i have midori installed and it worked so why the **** should i "try" cromioum?

reinstalling FF is just stupid. what shoudl it help? with --purge it would have helped yes but totally innessasary because nothign is changed on programm files of FF if u run it.

and i dont need help with disk space i know why i dont had space just because i download stuff its that simple. xfce never warns be by default for low disk space and thats pretty ****. i could have guessed myself that there are tools for this but not really taught about it untill i clicked that link i guess i have to thank you for that. so thank u. i will get some tool now to warm me when my disk goes low. (wasnt what already into win95? xubuntu really should have some kind of warnung by default)

anyway that was not really help. even trying FF in save mode was not helping.

I just renamed .jdownloader .mozilla to force the programms to generate the default settings. and now it works again.

i dont even know why i posted here looks like i know stuff good enough not to need this.

---

