---
title: "[Tutorial] Dell Wireless 1390 WLAN Card on 8.04 LTS"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nitrokid759 on 2008-04-26
First off, make sure you have a different Internet connection, I recommend using the ethernet cable used on your computer with the router.

Run This In A Terminal:
> 
wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
unzip -a R151517.EXE


Go to add/remove software.Scroll down and apply Windows Wireless Drivers. 
[[IMG]http://img159.imageshack.us/img159/6996/screenshotjy2.th.png[/IMG]](http://img159.imageshack.us/my.php?image=screenshotjy2.png)

Then run it. Select the bcmwl5.inf and enable it.
[[IMG]http://img159.imageshack.us/img159/2862/screenshotut9.th.png[/IMG]](http://img159.imageshack.us/my.php?image=screenshotut9.png)
 Restart. You should get some notice about a driver, install it. Then it should work.

---

### Post by gunninks on 2008-04-27
> **nitrokid759 said:**
> Go to add/remove software.Scroll down and apply Windows Wireless Drivers. Then run it. Select the bcmwl43.inf or whatever it is and enable it, then restart. Then it should work.
Ok i have a dell vostro 1500 with the 1390 wireless card and i followed what you said and installed the "windows wireless driver" and after i open the program i do not see any drivers to select. o you have any suggestions?
Thank you.

---

### Post by nitrokid759 on 2008-04-27
i need to update some things, give me a few minutes, ima get screenshots too

---

### Post by gunninks on 2008-04-27
Ok....I am not sure as to why i am stuck on this. When i select the  driver it finds the hardware but when i reboot i have no luck getting it to work. If you can help what info do you need.
Thanks

---

### Post by nitrokid759 on 2008-04-27
After you do the windows wireless driver thing and restart, the driver thing should pop up and tell you to install it, then u install it and click the network icon and ur wireless network should be there

---

### Post by gunninks on 2008-04-28
This is what i have. As you can see there is no wifi bars a the top of the screen yet it shows that it see's it
[[IMG]http://img155.imageshack.us/img155/3381/screenshotdw2.th.png[/IMG]](http://img155.imageshack.us/my.php?image=screenshotdw2.png)

---

### Post by nitrokid759 on 2008-04-28
idk it worked for me, what kind of laptop do you have?

---

### Post by StefAndrew on 2008-04-28
Just wanted to say that I found out that download is only recommended for users outside of USA and Japan.  So that may be why it's not working.  I'm downloading the newest version listed on Dells website right now and I will give that a try and see how it goes.

I've consistently had trouble with this 1390 card.  I might see about buying a replacement card and swap it out.

(edit)
Here is the link I am downloading:

[http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

(/edit)

---

### Post by StefAndrew on 2008-04-28
I will have to try when I get home.  I can't get internet access on my laptop while at work.  It gets blocked by the security filters when trying to install apps.  In the browser windows I can use my network login to get internet access, but when trying to use APT or Add/Remove it doesn't prompt me so therefore it blocks the attempts.

I'll post again later tonight to see how it goes.

---

### Post by Eion on 2008-04-29
I have a 1300, do you think this would work with that?

---

### Post by StefAndrew on 2008-04-30
I think this one might be better suited for your card.  It was the only thing I could find on Dell's website by searching for wireless 1300.  And this one is for US users only apparently, in case you live outside of the US.

[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R115321&formatcnt=1&libid=0&fileid=152055](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R115321&formatcnt=1&libid=0&fileid=152055)

---

### Post by iamroot on 2008-04-30
> **StefAndrew said:**
> 
(edit)
Here is the link I am downloading:

[http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

(/edit)

I downloaded this link and installed the correct driver. I restarted, and my Wifi light is still off, and it still doesn't recognize any wireless networks. I have a Dell Vostro 1000.

---

### Post by StefAndrew on 2008-05-01
I got the drivers to install, I just don't have any Wifi close enough that I can use to try out.  So I'll keep you posted.

---

### Post by ucal on 2008-05-01
Is there anyway I could do this without an Ethernet connection (that doesn't work for me either)?  Maybe save the .exe on an ipod?

---

### Post by 85fb on 2008-05-01
1500 vostro with 7.10. maybe work? (inside usa)

---

### Post by cl3aner on 2009-08-13
Confirm this worked flawlessly for me using a Dell Inspiron 1000 with a fresh installed Ubuntu using the Dell 1350 WLAN (MODEL:WL-611GD) thanks a bunch!

---

### Post by hannabace on 2009-10-14
Hey!

I've got a problem with that.

I have a Dell vostro 1000 and it doesn't work...it says after the driver installation "no hardware" and after the reboot nothing happens. 
and i tried both links ([http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE) and [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)) 
who can help me?

---

