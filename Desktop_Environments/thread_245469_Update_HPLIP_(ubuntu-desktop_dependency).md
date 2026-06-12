---
title: "Update HPLIP (ubuntu-desktop dependency)?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Cable on 2006-08-27
I'd like to update HPLIP to the newest version via checkinstall.  However, when I try to install it, it complains about trying to overwrite a file that is also in the "hplip" package that is already installed.  I went to remove the hplip that was already installed, and it wanted to remove ubuntu-desktop as well.  I'm aware of the fact that ubuntu-desktop is a metapackage and such, no need to explain that.  I'm just wondering how I should go about removing the current hplip so I can install the newest version.  Should I go ahead and remove ubuntu-desktop?  I'm not sure what process I should follow for doing this.  A little help?

---

### Post by Anduu on 2006-08-28
Is the version of HPLIP you are using broken?

If not you should leave well enough alone...the version from the repos is the latest version that is considered stable with Dapper and you could possibly be in for some real breakage by trying to force an unsupported version.

Just my 2 cents :p

---

### Post by useResa on 2006-08-29
Hi,

I run into the same problem (see my thread [http://www.ubuntuforums.org/showthread.php?t=245877)](http://www.ubuntuforums.org/showthread.php?t=245877)), so I figured I bump this one up again.

I am trying to update HPLIP because I am not able to get my HP PSC 1410 working properly.

---

### Post by useResa on 2006-08-29
I finally succeeded in installing the update of HPLIP!

First go to the directory in which you extracted the updated package.
Next the following code did the trick for me:
```
sudo apt-get remove hplip
sudo apt-get remove hplip-data
sudo apt-get remove hplip-ppds
sudo make uninstall
sudo make clean
sudo rm -rf /usr/share/hplip

sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev checkinstall

./configure --prefix=/usr
make
sudo checkinstall

sudo /etc/init.d/hplip restart

sudo /etc/init.d/cupsys restart
``` 
Hope you will also succeed in installing the new HPLIP package.

BTW: If your interested in my complete "struggle" go to the thread I have indicated in my previous reply.

---

### Post by pooslinger on 2006-10-17
> **useResa said:**
> I finally succeeded in installing the update of HPLIP!

First go to the directory in which you extracted the updated package.
Next the following code did the trick for me:
```
sudo apt-get remove hplip
sudo apt-get remove hplip-data
sudo apt-get remove hplip-ppds
sudo make uninstall
sudo make clean
sudo rm -rf /usr/share/hplip

sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev checkinstall

./configure --prefix=/usr
make
sudo **make install**

sudo /etc/init.d/hplip restart

sudo /etc/init.d/cupsys restart
``` 
Hope you will also succeed in installing the new HPLIP package.

BTW: If your interested in my complete "struggle" go to the thread I have indicated in my previous reply.

Thank you.  Updated hplib to 1.6.9 -> 1.6.10.  My 7410 works perfectly now. I did have to change one thing which is boldface in your code section above.

---

### Post by useResa on 2006-10-18
> **pooslinger said:**
> Thank you.  Updated hplib to 1.6.9 -> 1.6.10.  My 7410 works perfectly now. I did have to change one thing which is boldface in your code section above.

Thank you for adding this part. Hopefully it will help others as much as it did help you.

---

