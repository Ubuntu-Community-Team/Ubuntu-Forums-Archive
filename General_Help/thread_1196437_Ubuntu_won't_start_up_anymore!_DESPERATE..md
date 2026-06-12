---
title: "Ubuntu won't start up anymore! DESPERATE."
date: 2009-06-24
forum: General Help
---

### Post by knowndarkness on 2009-06-24
Hi. i am new to Ubuntu. I've been using Ubuntu 9.04 for about 3 weeks now. And i loved every single moment. Until it just stopped working.

This is what happened:

I installed ubuntu 9.04 to run alongside Windows Vista. "NOTE: MY INSTALL WAS INSIDE VISTA" So then i had a dual boot option when i start my computer. Today, i wanted to backup my Ubuntu, in case anything happened. So i installed "remastersys backup" on Ubuntu. I tired using it, and it didnt work out so well for me. So then i uninstalled it. Right when i did that, i restarted the computer just because. then it just wouldnt load anymore! 

Tell me if i'm wrong, but are my files inside "C:\ubuntu\disks" in the "root.disk" file? Well, it they are, i REALLY DESPERATELY HAVE to get a file out! My homework for my english class is in there! And i honestly don't know how to get it out. Is there a way for me to look inside this "root.disk" file, so that i can take it out / copy it?! I read and searched everywhere on the internet. I really need help!

I have a picture of what my boot up screen looks like when i try to load Ubuntu. I tinypiced the picture since it was 2.5 MB. but here the link to picture : *removed by user*



EDIT: 

My fix:

Make a copy of the root.disk file and paste it somewhere you'll remember. (If you made you're virtual disk very high in capacity, it'll probably take a while. For me, I gave myself around 15 GB, and whenever i want to download/install/etc stuff, i direct it to the Windows Drive. That is located in "/host". Navigate there, and it should look familiar)
Then, delete the ubuntu folder. 
Then install, using the CD, inside Vista.
After installing, restart; load Ubuntu, let it go through the first time processes, then restart again; go back to windows, and take that root.disk file, and put it into the ubuntu folder. Yes, that means to replace the root.disk file you just installed with the CD. 
Restart. And if should load back to normal. 

This is awesome. Now I know how to back up Ubuntu! ;D
Hopefully this helps anyone who had the same problem I did, or if you want to just back up Ubuntu when its installed Vista, i guess.

---

### Post by benerivo on 2009-06-24
If you can still boot windows, then you can try section 8-13 from the link below. If not, then i would boot in to the Ubuntun live cd and try section 8-14...

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by knowndarkness on 2009-06-24
fortunately, i can still boot windows. thanks for the reply. i'll look at the section again. i tried mounting or whatever through live CD 30 minutes ago. no success story there.

i have no idea what this is. i tried it, but i dont know what it does exactly > How can I access the Wubi files from Windows?
There are a few Windows applications that can mount ext2-based file systems. See for instance:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
[http://www.fs-driver.org/](http://www.fs-driver.org/)
The relevant Wubi files you need to access are located under C:\ubuntu\disks\

---

### Post by mikey.duhhh on 2009-06-25
I'm not an expert on remastersys or on running Ubuntu inside Windows, but I would try booting from the live CD.  Once the CD is running, try going to Places (top left of screen) and clicking on the Ubuntu directory already installed in Windows.  Then see if you can find and move the file(s) you need to the Windows Desktop or at least to C:\.

Then delete the Ubuntu install and start over.  My guess is that you somehow used the wrong parameters with remastersys and either stored that in the Ubuntu install or failed to move it to a DVD or CD.

Hope this helps.

---

### Post by Vikhyath on 2009-06-25
**this is not a rectification of the problem but a <hope> try to retrieve your files.**
If you hav the ubuntu installation cd, boot up your computer with that and enter the **try ubuntu ** <or something like that>...
with this open the file browser and check if your file is alive!

---

### Post by knowndarkness on 2009-06-25
> **mikey.duhhh said:**
> I'm not an expert on remastersys or on running Ubuntu inside Windows, but I would try booting from the live CD.  Once the CD is running, try going to Places (top left of screen) and clicking on the Ubuntu directory already installed in Windows.  Then see if you can find and move the file(s) you need to the Windows Desktop or at least to C:\.

Then delete the Ubuntu install and start over.  My guess is that you somehow used the wrong parameters with remastersys and either stored that in the Ubuntu install or failed to move it to a DVD or CD.

Hope this helps.

i was thinking of doing this. but i have a question. well, i have access to windows, it boots fine. i can access the directory of ubuntu and boot.disk and everything, but ubuntu just wont load. i think i did do something wrong. so if i were to copy the "root.disk" file and save it to replace the one after i reinstall inside windows with, would it work?

---

### Post by benerivo on 2009-06-25
> **knowndarkness said:**
> fortunately, i can still boot windows. thanks for the reply. i'll look at the section again. i tried mounting or whatever through live CD 30 minutes ago. no success story there...

How can I access the Wubi files from Windows?
There are a few Windows applications that can mount ext2-based file systems. See for instance:
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
[http://www.fs-driver.org/](http://www.fs-driver.org/)
The relevant Wubi files you need to access are located under C:\ubuntu\disks\

...i have no idea what this is. i tried it, but i dont know what it does exactly

The ext3 drivers such as [http://www.fs-driver.org/](http://www.fs-driver.org/) allow you to browse partitions and wubi installations that use the ext3 format. Installing one is relatively simple using the instructions, although i've never used it to browse a wubi install myself.

---

### Post by Vikhyath on 2009-06-25
if you didn't leave lot of content in the native ubuntu drive, you could try reinstalling

---

### Post by knowndarkness on 2009-06-25
> **benerivo said:**
> The ext3 drivers such as [http://www.fs-driver.org/](http://www.fs-driver.org/) allow you to browse partitions and wubi installations that use the ext3 format. Installing one is relatively simple using the instructions, although i've never used it to browse a wubi install myself.
i tried using that. when i try to target the ubuntu directory from windows, theres no file that has ".ex2" or ".img", so i dont know how to view it.

---

### Post by knowndarkness on 2009-06-25
> **mikey.duhhh said:**
> 

Then delete the Ubuntu install and start over.  My guess is that you somehow used the wrong parameters with remastersys and either stored that in the Ubuntu install or failed to move it to a DVD or CD.




THANK YOU SO MUCH! I didn't do the live CD part thing you told me to do, but it was the part where you told me to delete and reinstall again. THANK YOU SO MUCH.

I JUST BACKED EVERYTHING INTO MY EHD. That'll teach me. Now i can go back to writing and spelling correctly! Windows can't do that very well for me.

This was my fix, in case anyone ever faces the same problem.

Make a copy of the root.disk file and paste it somewhere you'll remember. (If you made you're virtual disk very high in capacity, it'll probably take a while. For me, I gave myself around 15 GB, and whenever i want to download/install/etc stuff, i direct it to the Windows Drive. That is located in "/host". Navigate there, and it should look familiar)
Then, delete the ubuntu folder. 
Then install, using the CD, inside Vista.
 After installing, restart; load Ubuntu, let it go through the first time processes, then restart again; go back to windows, and take that root.disk file, and put it into the ubuntu folder. Yes, that means to replace the root.disk file you just installed with the CD. 
Restart. And if should load back to normal. 

This is awesome. Now I know how to back up Ubuntu! ;D
Hopefully this helps anyone who had the same problem I did, or if you want to just back up Ubuntu when its installed Vista, i guess.



Thank you guys so much! [:

I <3 UBUNTU!

---

