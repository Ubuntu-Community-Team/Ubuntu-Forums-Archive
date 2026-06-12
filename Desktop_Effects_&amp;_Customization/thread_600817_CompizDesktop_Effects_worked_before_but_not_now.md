---
title: "Compiz/Desktop Effects worked before but not now?"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by ogwilson on 2007-11-02
I had it working before with no effort, and now i always get the message "Desktop effects cannot be enabled" or something of the nature. I downloaded ATI's drivers from their site and and installed them, but still won't work. I'm gonna try the Proprietary drivers next and see if that works. Anyone can help?:confused:

---

### Post by revchris on 2007-11-02
If you had compiz working on Feisty and upgraded to Gutsy, you have to un-install compiz then reinstall it.  There is a thread on here somewhere on how to do this, I'll try to find it again (I had this problem)

Edit:  Heres a link on how to remove compiz:   [http://ubuntuforums.org/showthread.php?t=600577&highlight=ccsm](http://ubuntuforums.org/showthread.php?t=600577&highlight=ccsm)

---

### Post by ogwilson on 2007-11-02
no i did a clean install of GG and it was working. and due to complications, i had to reinstall, and now nothing i try seems to work.

---

### Post by ogwilson on 2007-11-02
Bump

---

### Post by Forlong on 2007-11-02
> **ogwilson said:**
> I downloaded ATI's drivers from their site and and installed them, but still won't work. I'm gonna try the Proprietary drivers next and see if that works.
ATI's driver **is** the proprietary one.
If you installed the latest one, see the last step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support).

If not, you need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by aeonwings on 2007-11-03
> **ogwilson said:**
> I had it working before with no effort, and now i always get the message "Desktop effects cannot be enabled" or something of the nature. I downloaded ATI's drivers from their site and and installed them, but still won't work. I'm gonna try the Proprietary drivers next and see if that works. Anyone can help?:confused:


have you try to uninstall compiz then install it again? might work.

---

