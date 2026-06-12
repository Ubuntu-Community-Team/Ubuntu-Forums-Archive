---
title: "Compiz - Step 2 :how to configure xorg and create a backup"
date: 2006-07-08
forum: Desktop Environments
---

### Post by CheeseAndToast on 2006-07-08
(Dapper User)

Hi, 

Thanks to Pawel, i've found that compiz work well on my Graphics card; ATI Technologies, Inc. RV280 [Radeon 9200 SE].

I'm currently following step from this [thread]("http://ubuntuforums.org/showthread.php?t=145068"). [HTML]http://ubuntuforums.org/showthread.php?t=145068[/HTML] 

I'm kinda stuck on step two.  I need to configure my xorg - not sure what the command is, if someone could tell me i would be greatful. Also before I edit the file i want to make a backup - i'm not sure how to do this, any ideas?

Just one more thing, if my xserver fails to start as result of editing my xorg, how to reinstate my backup?

Can't wait to get compiz working!!!

Thanks guys.

---

### Post by CheeseAndToast on 2006-07-09
to back up xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

to edit xorg
sudo gedit /etc/X11/xorg.conf 

If it goes wong on start up:
sudo dpkg-reconfigure xserver-xorg

---

