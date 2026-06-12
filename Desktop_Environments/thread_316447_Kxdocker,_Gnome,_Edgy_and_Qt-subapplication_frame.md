---
title: "Kxdocker, Gnome, Edgy and Qt-subapplication frame"
date: 2006-12-10
forum: Desktop Environments
---

### Post by HuanKaktus on 2006-12-10
I try to run kxdocker-1.1.4a on edgy with gnome+beryl. Kxdocker is compiled from sources. All is good, but it display Qt-subapplication window frame :) It is not very beautiful...

[[IMG]http://ilapas.lv/files/articles/images/roberts/kxdocker.jpg[/IMG]]("http://ilapas.lv/files/articles/images/roberts/kxdocker_full.jpg")

Can anyone tell me, what I can remove it? I am not very experienced with linux :(

P.S. if I push "Show desktop" button, kxdocker hidde too... ;)

---

### Post by Nycthbris on 2006-12-11
Hey I had the same problem. This guide helped me out: [http://ubuntuforums.org/showthread.php?t=294511](http://ubuntuforums.org/showthread.php?t=294511) Best of luck!

---

### Post by tuxmap on 2006-12-12
if ur using beryl then add this

beryl-settings->set-window-atrributes->border
p:Kxdocker:1

---

### Post by pferrel on 2007-05-24
I have the same problem.  

A little more explanation of where to change this setting would help.  My beryl-settings has no menu and I can find no setting file that has anything that looks like p:Kxdocker:1  How exactly do I make this change?

---

### Post by rocsak on 2007-05-28
You open Beryl Settings Manager, you choose Window management, you enable plugin "set window attribs by various criteria", option Border (disable windows border), add criteria for window attribute, you select "owning program" and you write kxdocker. Be sure to check deisble window border. 
Worked for me fine in Ubuntu 7.04

---

### Post by pongster on 2007-06-29
how would we disable that window in compizfusion?i've tried but have been unsuccessful with the window rules and regex plugin:)

---

### Post by danowoz on 2007-09-11
FAYI ~ There is a patch for compiz on the XIA project website. I apllied the patch and it took care of the frame problem. It is a real fix.

---

### Post by nievo on 2007-09-26
> **danowoz said:**
> FAYI ~ There is a patch for compiz on the XIA project website. I apllied the patch and it took care of the frame problem. It is a real fix.

I don't suppose you could post a link to this patch? I had a hunt around the site, but I couldn't find it :(

---

### Post by danowoz on 2007-10-03
> **nievo said:**
> I don't suppose you could post a link to this patch? I had a hunt around the site, but I couldn't find it :(

The XIA Project team has been making changes to the website. I emailed them about the patch. Here is Stefano's reply :

    "these days we are working on xiaprojects.com website, i will put the
     patch on kxdocker download page, thanks you."

Update: you can find the patch [[COLOR="Red"]here[/COLOR]]("http://wozlabs.com/linux/kxdcfht.html")!

---

