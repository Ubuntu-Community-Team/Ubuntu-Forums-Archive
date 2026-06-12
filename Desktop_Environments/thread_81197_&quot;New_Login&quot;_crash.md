---
title: "&quot;New Login&quot; crash"
date: 2005-10-23
forum: Desktop Environments
---

### Post by dhjohnson on 2005-10-23
I have a pretty fresh Breezy installation (I added ssh server and followed the instructions on [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) to make my ATI Radeon 9200 work), and every time someone tries to start a New Login (Applications > System Tools > New Login), the screen turns into a kind of squashed checker board, similar to [http://www.ubuntuforums.org/attachment.php?attachmentid=911&d=1114337486](http://www.ubuntuforums.org/attachment.php?attachmentid=911&d=1114337486) and the machine locks up.

Below is a what I think is the important part of kern.log.  How can I keep this from happening?

 localhost kernel [4295309.694000] [fglrx:firegl_umm_init] *ERROR* UMM area already initialized!
localhost kernel [4295309.694000] [fglrx:firegl_unlock] *ERROR* Process 8345 using kernel context 0

Ubuntu,
David

---

### Post by mannheim on 2005-10-24
Well, I have a very similar problem with a Radeon 9500 Pro. 

With the fglrx driver, it works fine, **except** when I do a "New Login" or when I log out. On these occasions, it usually (not always) locks up, most often with a blank screen (at the time when you would expect to see the spinning cursor appear after a second or two, before the welcome screen returns). Sometimes the screen is not blank, but  a colorful mess instead.

I have tried various recommended additional lines in my xorg.conf file, and none made a difference. With the "ati" driver in place of fglrx, things are fine. Things are also fine on a very my other machine, which has a very similar configuration, but has a 9600 SE (if I remember right).

Peter

---

### Post by dhjohnson on 2005-10-24
The problem that I was having before, was that if I didn't install the binary driver, some of the slick screensavers would lockup my machine (had to do a hard reboot).  If I didn't select the fglrx driver, the slick screensavers moved at a painfully slow speed.

---

### Post by dhjohnson on 2005-10-25
Any idea on this one, folks?

Am I posting in the right forum?

Thanks and Ubuntu!

---

### Post by dhjohnson on 2005-10-27
Well, I got my problem fixed.  My ATI graphics card was the source of the problem--which I was pretty sure of, but being a newbie, I couldn't really nail it down.  After reading a lot of posts about how ATI isn't all that with linux, on a hunch I decided I'd go pick up an nVidia (my ATI was pretty old, anyway).  Anyhoo, if you're in the market, for right now anyway, point your shopping cart towards an nVidia and not so much an ATI.  

To recap:
OpenGL screensavers caused by machine to crash, forcing a hard reboot--Installed binary ATI drivers.

Binary install didn't cause 3D accelleration--Edited xorg.conf to change drivers to fglrx.

Opening "New Login" caused display scramble and lock up--???--New nVidia graphics card.

---

### Post by arsya on 2006-03-14
I guess this is quite an old post. I am facing the same problem with my notebook , ati radeon mobility 9600.
I downloaded the latest driver: ati-driver-installer-8.23.7-i386.run
then followed the instruction I found in this site.
I could see that the 3d accelleration working. Just when I tried to logout (back to the login screen) or shutdown, the screen just goes blank.
This does not happen everytime, just occationally, randomly.
Anybody can give hint?

---

### Post by arsya on 2006-03-16
Fortunately, after doing some googling around, i found something about this problem.
There is a workaround for solving this problem, by configuring the session manager (gdm/kdm) to restart X when logging out.

See this link:
[http://www.thinkwiki.org/wiki/Problems_with_fglrx]("http://www.thinkwiki.org/wiki/Problems_with_fglrx")

Check on the "Hardlock on X logout" part on that site.

I don't get the Hardlock anymore after making the changes in my /etc/gdm/gdm.conf

---

