---
title: "re-use hard drive on a new machine"
date: 2009-01-18
forum: General Help
---

### Post by UranUtan on 2009-01-18
Hi,

I am going to have a better computer. Can I re-use the hard drive from the old machine in the new one and expect that Ubuntu will boot OK?

The hardware is very different between the two machines. If Ubuntu boots, can I just adjust the new hardware by doing System / Administration / Hardware Drivers?

If it is not recommended to re-use the hard drive with Ubuntu installed or a different machine. I can of course install Ubuntu on the new machine. The problem is that I don't know how to save system & application settings. Where are these config / settings saved?

---

### Post by theWrkncacnter on 2009-01-19
All of your application settings should be in your home directory, aka /home/username

You will need a fresh install of ubuntu to get your new hardware working, but after that you can import the contents of your own home folder into your new one. That'll preserve your settings, I think. But I'd wait and see what the rest of the forum thinks -- I could be mistaken!

---

### Post by virtuallinux on 2009-01-19
Well, you could probably get by just moving the hard drive to the new machine and not reinstalling, but it would be better to do a fresh install.  Most of your settings and data are stored in your home directory.  You'll either want to copy this to another drive or partition before reinstalling, or you can create a new partition and use it as your home directory.  The method for doing this is described in this tutorial here:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by UranUtan on 2009-01-19
Thank you gentlemen for your answers.

I will save the home/myUserName in an external USB drive. Then I will do a fresh install and hopefully will be able to restore the settings as best as I can.

---

