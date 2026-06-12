---
title: "Driver for 1710 printer"
date: 2008-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gwmerc on 2008-11-21
I am using a Dell Inspiron 8600 with Ubuntu 8.04 trying to connect to my Dell 1710 laser printer. Dell is no help they have no print drivers for Ubuntu at all. 

This is a borrowed machine as my desktop that had Windows 2000 and XP as well as Ubuntu died. I was considering a Dell laptop having believed that Dell supported Ubuntu. I guess that is wrong and I should look elsewhere for a new machine unless someone can explain why Dell seems to have abandoned Ubuntu and how to find drivers as a relative non tech type of user. Thanks to any and all for your help.

---

### Post by ytsejam1138 on 2008-11-21
This thread should get you up and running:  [http://ubuntuforums.org/showthread.php?t=107028&highlight=dell+1710](http://ubuntuforums.org/showthread.php?t=107028&highlight=dell+1710)

---

### Post by gwmerc on 2008-11-21
Unfortunately I am fsmiliar with that / those sites. Most refer to the fact that whst they tried didn't work. The others are so sophisticated that I have no idea where to find or implement them. HELP!

---

### Post by ytsejam1138 on 2008-11-21
Ok, I don't have this printer so I cannot test, but according to the above link I posted this driver works for the Dell 1710n, but may not work for the 1710.  [http://ubuntuforums.org/attachment.php?attachmentid=9314&d=1147315439](http://ubuntuforums.org/attachment.php?attachmentid=9314&d=1147315439)

Download this and extract the .ppd file inside.  Next go to Settings>Administration>Printing and add a new printer.  Click the option that says something like I have my own ppd file and point to the extracted file.

Another user reported that when you install the dell 1710 you have to use an HP driver, the HPIJS driver, the best printer i found was the LaserJet 4 driver. It worked out perfectly when i ran the test.  

You should be able to install this by going to Settings>Administration>Printing and add a new printer

---

### Post by Cerny on 2009-01-18
The LaserJet 4 from HP is the best driver I found out there. If you use the default one that Ubuntu gives you when it detects the printer. It will run but the printer won't actually print anything. This is just for the 1710 model.

---

### Post by northband on 2009-05-28
Cool the above worked for me on my 1710 running Ubuntu 8.10 Ibex.  Thanks!

---

### Post by winjeel on 2009-07-09
(sorry for reserrecting an old thread, but...)

Thanks for these instructions, especially the driver file. It's working for me, too, now.  :p

(Yes, I've got the 1710n, too)

---

### Post by shaners on 2009-07-20
Just a thank you note to you folks for having this information out here.
took me about 2 to 3 hours, but a linux newbie got it! Thanks!!! Shane W

---

### Post by ilazria on 2010-04-24
Was looking for a way to set up this same printer, stumbled upon this link. Works perfectly fine for Ubuntu 9.10.

Figured I'd add this as this post is one of the first links to pop up when I was hunting for a solution.

 [http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=30319125C176B28EE040A68F5B282820](http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=30319125C176B28EE040A68F5B282820)

---

### Post by winjeel on 2010-05-05
I've just reinstalled Ubuntu, with 10.04 and had to reinstall the driver. Again I'm using that driver, as it seems to be the easiest to get and set up. However, at first it didn't work, but when I went to: System > Administration > Printing, and then Printer Options > Form Source I selected Tray 1, and the test page worked. Phew!

---

### Post by thor71 on 2010-08-29
thanks everybody I just joined the forum and found this solution to make my 1710n work. I am also on 10.04 and tip on selecting tray 1 was very helpful.

---

### Post by ScruffyHammer on 2011-03-18
Hello everyone!
I am new to Linux (Ubuntu Desktop 10.10 Maverick Meerkat). I also have the Dell 1710n, and thanks to [ytsejam1138]("http://ubuntuforums.org/member.php?u=525398") for the driver and instructions in post#4. My printer is up and working too. I did not have to select tray one for it to work though.

What a great community

Thank You!

Rick.:D

---

