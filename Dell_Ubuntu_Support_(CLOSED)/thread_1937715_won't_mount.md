---
title: "won't mount"
date: 2012-03-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimberWolf5871 on 2012-03-08
I downloaded and created a boot flash drive using the instructions and software the site said to use and everything went fine. When I went to run it from the flash like it said I could, it wouldn't load. It gave me a message saying "can not boot \dev\loop to \cow." 
What does that mean and how can I fix it so it will run?

I'm on a Dell Latitude D630, my normal OS is WinXP which I desperately want to get rid of, and my CDRW/DVD-Rom is non compus mentus. (translate to broken)

---

### Post by gordintoronto on 2012-03-08
I suggest this site and tutorial for creating an Ubuntu bootable flash drive from Windows: [http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows)

Sadly, "the instructions and software the site said to use" is not unique, and some versions are outdated.

---

### Post by TimberWolf5871 on 2012-03-08
Instructions and software meaning the ones provided by the Ubuntu site itself, which are ecactly what your link says to do.

---

### Post by TimberWolf5871 on 2012-03-11
So basically, no one is going to help any more than "follow the instructions"? Well I followed the instructions and they didn't bloody work. I need more help than that.

---

### Post by gbrainin on 2012-03-11
Did you check the download (md5) to ensure it was okay?  The error message you got seems odd for at least two reasons: first, Linux uses the forward slash (/) not the backslash (\); second, I'm not familiar with any distribution that has a directory called "cow."

---

### Post by TimberWolf5871 on 2012-03-11
I dont know how to check the download, but as far as I could tell it was fine.

---

### Post by gbrainin on 2012-03-11
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by TimberWolf5871 on 2012-03-11
ok the MD5 says it's fine.

---

### Post by gbrainin on 2012-03-11
I'm not familiar with the windows-based USB software.  Can you step through exactly what you did to a) create the bootable USB drive, and b) to boot from it?

---

### Post by TimberWolf5871 on 2012-03-11
Ok.

1: Download iso for Ubuntu and the universal usb installer (links provided in instructions), use the installer to create the boot drive on selected flashdrive, at least 2gb large.

2: restart computer, bringing up boot options as it powers on. Reset to boot from USB Storage first, then let it go on. past that it's automatic as far as I've been told/read.

---

### Post by gbrainin on 2012-03-12
Hmm.  I'm getting into guesswork, here, but the backslashes and "cow" are still bothering me.  Did you erase/format the USB drive before you did the install?  Perhaps there was something on it already that is somehow interfering?  (AFAIK, that shouldn't be a problem, but I'm just trying to eliminate variables.)

---

### Post by TimberWolf5871 on 2012-03-12
@gbrainin no, I had the install program format it for me.

Either way, I got it working finally. I re-dl'd the iso to a different part of my HDD, and used that the same way I did the other. This time it worked. Thanks for the assistance anyway.

---

### Post by gbrainin on 2012-03-12
Strange problem, but I'm glad you got it working.

---

### Post by TimberWolf5871 on 2012-03-12
And now that I've run it, I'm not going to go with it. It doesn't support alot of my games. Terraria for one.

---

### Post by gbrainin on 2012-03-13
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23556&iTestingId=63917](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23556&iTestingId=63917)

---

### Post by TimberWolf5871 on 2012-03-13
It's for Terraria 1.0 only? Terraria's up to 1.2.

---

### Post by gbrainin on 2012-03-13
[http://lmgtfy.com/?q=terraria+1.2+wine](http://lmgtfy.com/?q=terraria+1.2+wine)

---

