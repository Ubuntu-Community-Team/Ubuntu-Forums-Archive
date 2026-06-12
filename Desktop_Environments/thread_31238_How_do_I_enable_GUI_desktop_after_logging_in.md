---
title: "How do I enable GUI desktop after logging in?"
date: 2005-05-02
forum: Desktop Environments
---

### Post by RodneyJM on 2005-05-02
Hello All,

I'm not sure if this is the right place to post this, I have searched back several pages and looked throught the documentation but can not see a solution to this.

I have just installed ubuntu v4.10 and enabled it to update everything that it needs today, so I think its safe to assume that is the newer 5.04 version.

My problem is this: after booting into unbuntu, It asks me to logon and enter the password, good, fine  :smile: . But then It just sits there waiting for text commands. How do I get it to go into graphical mode like other Linux distros such as Fedora core series. I don't have a problem logging in through text mode, but don't feel comfortable learning a lot of text commands  :???: . You could say that I am from the school of GUI and like it to be that way as soon as I log on. So how do you get ubuntu to display the GUI desktop?

---

### Post by SGC on 2005-05-02
By default you should log on to a gnome session, make sure you are not using failsafe from the gdm.


I'am not an expert in this stuff, but try the following:

**startx**

Then type:

**gnome-session**

---

