---
title: "speed up older machine"
date: 2009-05-09
forum: General Help
---

### Post by stuart.reinke on 2009-05-09
Simple question: Will an older computer with a p3 processor run noticeably faster with xubuntu as opposed to ubuntu?

---

### Post by mkvnmtr on 2009-05-09
For me on several low memory machines Xubuntu did not seem to use less resources than Ubuntu. I have had good success using the Ubuntu minimal install disk and then using xfce4. Works with 128Mb of ram and is a good desktop. Not really hard to do if you read the instructions and take your time about what you wish to do.

---

### Post by DLG102282 on 2009-05-09
I would say yes, but you won't know untill you try it. It will also depend on how much RAM is in the system.

---

### Post by stuart.reinke on 2009-05-09
I think it has 312 Mb of ram. All it is used for is internet surfing. No frills or eye candy is required. 

Thought maybe I could gain a little speed.

---

### Post by Sealbhach on 2009-05-09
Try openbox. 

sudo apt-get install openbox

Select an openbox session when you login, that should be faster than using xfce. You need to right-click on the desktop in openbox to get a menu.

To speedup your browser try the Fasterfox add-on for Firefox or try the Opera browser.

.

---

### Post by hexanol on 2009-05-09
Xubuntu isn't the lightest/fastest distro around. Distrowatch recently made a comparaison between Debian 5.0.1 Xfce and Xubuntu 9.04 that you can see [here]("http://distrowatch.com/weekly.php?issue=20090427#feature")...

---

### Post by stuart.reinke on 2009-05-09
Am I to understand that I can have multiple desktop configurations to choose from at startup, depending on my mood?

---

### Post by Sealbhach on 2009-05-09
Yes, instead of the default Gnome session you can choose Xfce, or Openbox or Fluxbox and I suppose others too. Just select which session you want before you login.

.

---

### Post by stuart.reinke on 2009-05-09
That is the coolest thing I've learned all week. Thanks. 

If I prefer openbox to gnome, will sudo apt-get purge gnome, remove the gnome desktop permanently?

---

### Post by MaxIBoy on 2009-05-09
You know, you can use openbox with GNOME. There should be a "GNOME (openbox)" session available. Openbox runs fine by itself though.

But yeah, if you want to you can get rid of software by using "sudo apt-get purge [name of package]." I'd recommend "apt-get remove" instead, that way all your settings are still there should you change your mind, and the configuration files don't take much room anyway.

---

### Post by Sealbhach on 2009-05-10
> **stuart.reinke said:**
> That is the coolest thing I've learned all week. Thanks. 

If I prefer openbox to gnome, will sudo apt-get purge gnome, remove the gnome desktop permanently?

I'd recommend leaving it there. While you're running Openbox it's not using any memory and it's a backup in case your Openbox session goes all weird on you.

.

---

