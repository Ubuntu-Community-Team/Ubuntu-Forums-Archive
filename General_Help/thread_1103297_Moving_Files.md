---
title: "Moving Files"
date: 2009-03-22
forum: General Help
---

### Post by PhilipV on 2009-03-22
Hi Ubuntu user, this is my first post here and hopefully you guys could help me out with this problem. Okay now I got LAMP set up, and now I want to add files to the server for testing. So I download wordpress, extract the folder, then go to the www folder and stick it in. Permission denied, okay fine - I google my problem, okay I should use gksudo nautilus, tried it. Okay somethings happening, then I see this:

Nautilus-Share-Message: Called "net usershare info" but if failed: 'net usershare' returned error 255: net usershare: cannot open useshare directory /var/liv/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing. 
** (nautilus:6513): WARNING **: Unable to add monitor: Operation not supported

Okay so I guess there is no usershares directory, tried making one, still no permission. Also a new file manager comes up with root at the top, but I still can't put files inside, it's really annoying. Also guys I have tried doing ALOT of different things, from using sudo and other commands - please post ANYWAY you can think of fixing this. I really like using Ubuntu and don't want to go back to XP!

---

### Post by PhilipV on 2009-03-22
Sorry for posting twice, but this is already at the second page and I really need some help!

---

### Post by BrandonND on 2009-03-22
you should be able to type

sudo chown -R *username* /var/www

---

### Post by PhilipV on 2009-03-22
Yay it worked.

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU.

You have saved me from A LOT of stress!

---

