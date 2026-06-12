---
title: "HELP ME read-only flash drive"
date: 2009-01-07
forum: General Help
---

### Post by unzoo on 2009-01-07
My 4gb flash drive is write-protected. I have tryed over and over to install ubuntu (live cd) onto the flash drive and nothing seems to work. I am very new to linux (computers) and could realy use some help.

---

### Post by Zeroberry on 2009-01-07
What version of what OS are you using? A simple way is starting your file manager as root. In Ubuntu

gksudo nautilus

This will give you root priviliges in that instance of nautilus.

You could also chmod the file I think

sudo chmod 777 /file/location

Inserting path there. Good luck.

---

### Post by unzoo on 2009-01-07
Hi I have tried that and i still get read-only message. A few weeks ago i tryed creating a USB startup disk with it witch failed. It has been read only ever since. I am using ubuntu 8.10 live cd (i think thats what its called).
My hard drive gave up on me so i was planning on running a usb OS. Any other ideas? Its got me stumped

---

### Post by sidewalkcynic on 2009-01-07
I wish I could help, but I have a similar problem.

I want to reinstall UBUNTU and change the name of my Home Folder. The problem seems to be that I won't be able to copy and access all the files I store on the USB during the reformatting. 

The reason this seems to be is I tried setting up a differnt User Account, and was unable to download the files from the USB. 

So what's the solution?

---

### Post by retiefdv on 2009-01-20
Take a look at the following post - it seems they have solved it (will be testing the solution myself this evening).
[http://ubuntuforums.org/showthread.php?t=1039451&highlight=usb+flash+drive+read-only](http://ubuntuforums.org/showthread.php?t=1039451&highlight=usb+flash+drive+read-only)

---

### Post by unzoo on 2009-01-22
The flash-drive is still read-only.

terminal said
 block device /dev/sdb1 is write-protected, mounting read-only

Any other ideas?

---

### Post by mixmaster on 2009-01-22
OK, a really dumb question.

Your USB stick doesn't by any chance have a little switch or tag on the outside which applies hardware write-protection does it?

---

### Post by unzoo on 2009-01-24
No I looked over it many times. I'm using a Kingston DataTraveler 4GB.

---

