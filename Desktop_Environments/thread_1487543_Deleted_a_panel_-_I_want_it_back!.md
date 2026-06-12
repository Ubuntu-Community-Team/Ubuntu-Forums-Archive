---
title: "Deleted a panel - I want it back!"
date: 2010-05-19
forum: Desktop Environments
---

### Post by andrew375 on 2010-05-19
I accidentally deleted the default, upper, panel and I can't see how to get it back! I've tried recreating it but I cannot see how to populate it with certain items, specifically the wireless networking control applet.  So how do I get back the panel i deleted?

---

### Post by ingeva on 2010-05-19
> **andrew375 said:**
> I accidentally deleted the default, upper, panel and I can't see how to get it back! I've tried recreating it but I cannot see how to populate it with certain items, specifically the wireless networking control applet.  So how do I get back the panel i deleted?
I have also found this a little tricky because it's not as easy as it might seem. The panels are defined in the directory ~/.gnome2 (look for panel*.d) but there's not a one-to-one correspondece, so backing up those files is not always enough.

As an extra precaution I have now set up a text file with all the icons defined, so I can manually restore one by one. This is clumsy, so if someone has a better solution that's also safe (like it will also restore the networkmanager applet) please do so!

---

### Post by 3Miro on 2010-05-19
You basically have to add a new panel and then manually add one by one all the menus and icons. This sux, but I don't think there is any other way.

(There might be a default panel setup file somewhere which you can just copy into ~/.gnome2, but this will only give you the default menu and icons)

---

### Post by r_s on 2010-05-19
> **3Miro said:**
> 
(There might be a default panel setup file somewhere which you can just copy into ~/.gnome2, but this will only give you the default menu and icons)

Why don't you just delete that directory and reboot, you will then have your default panels again.

---

### Post by bigsmitty64 on 2010-05-19
Do you have a bottom panel still? If you do just right click it and add a new panel, set it to the top, then you can just right click THAT panel and then click "add to panel" in a main menu, and all the other stuff you need. Easy enough, IF you still have the bottom panel. Hope this helps.

---

### Post by andrew375 on 2010-05-20
Sorry to have wasted your time, should have googled the question first.  Basically there are three [ lines of code](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html) to restore the default panel or alternatively all I needed was to install the "Notifications" applet on my new panel.  Thank you for the replies.  For information this is with the Gnome desktop running on ubuntu 9.1.

---

### Post by mric on 2010-05-20
> **andrew375 said:**
> Sorry to have wasted your time, should have googled the question first.  Basically there are three [ lines of code]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html") to restore the default panel or alternatively all I needed was to install the "Notifications" applet on my new panel.  Thank you for the replies.  For information this is with the Gnome desktop running on ubuntu 9.1.

nice one, maybe should be taken into  "**** 			                          			 			[The Great Desktop  Effects FAQ of 2010]("http://ubuntuforums.org/showthread.php?t=809695")"

---

### Post by mric on 2010-05-20
not working for me :(


UL30A
Ubuntu Lucid 10.04
2.6.34-020634rc7-generic

---

### Post by keyshawn on 2010-05-21
> **andrew375 said:**
> Sorry to have wasted your time, should have googled the question first.  Basically there are three [ lines of code]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html") to restore the default panel or alternatively all I needed was to install the "Notifications" applet on my new panel.  Thank you for the replies.  For information this is with the Gnome desktop running on ubuntu 9.1.

Although this only restores back to the default panel, it works for me. 

thanks.

---

