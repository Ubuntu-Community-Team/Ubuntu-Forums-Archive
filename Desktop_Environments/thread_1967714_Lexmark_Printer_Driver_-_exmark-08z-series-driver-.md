---
title: "Lexmark Printer Driver - exmark-08z-series-driver-1.0-1.i386.deb"
date: 2012-04-28
forum: Desktop Environments
---

### Post by b3nw on 2012-04-28
Note, this is for 12.04 32bit.

Attempting to install my printer drivers from:

[http://support.lexmark.com/index?productCode=LEXMARK_X4650&page=product&focusedTab=DOWNLOADS&locale=EN&userlocale=EN_US#1](http://support.lexmark.com/index?productCode=LEXMARK_X4650&page=product&focusedTab=DOWNLOADS&locale=EN&userlocale=EN_US#1)



```

Extracting file: printdriver.te
Extracting file: lexmark-08z-series-driver-1.0-1.i386.deb
Extracting file: launcher.c
Extracting file: launcher
Extracting file: lsbrowser
Extracting file: lsusbdevice
Using dpkg installation
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz11978/pkg/files/dpkg_msgs

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

=============================
***** ERROR REPORT *****


```

Not sure how to get at the .deb file from the .sh. Otherwise I imagine I could edit it to fix the missing Description field.

---

### Post by kev77 on 2012-04-29
I'm assuming you're using ubuntu 12.04? i had the same problem, it would seem the driver is not compatible with the latest ubuntu, i do hope this gets resolved :-(

---

### Post by b3nw on 2012-04-29
oops, yea should have noted that, using 12.04. I have a support ticket in with Lexmark, we'll see what they say on Monday.

---

### Post by kev77 on 2012-04-29
Brilliant, thanks for contacting lexmark, i'll keep an eye on this thread, in the meantime, if anyone has further info on this problem please let us know

---

### Post by TMSpack on 2012-04-29
Same Problem here.  Let us know what they say!

---

### Post by hbomb on 2012-04-29
I too have this same exact issue. I can also confirm that this worked on Ubuntu 11.10. I have a Lexmark X6650.

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb

I will be keeping a very close eye on this thread! :)

---

### Post by hbomb on 2012-05-01
Any news on this?

---

### Post by b3nw on 2012-05-01
News! Not great news. I've asked if they can provide us with the .deb or when they plan to support Ubuntu since their drivers worked on previous versions. 

> 
On Tue, May 1, 2012 at 7:58 PM, Lexmark Support <support1@lexmark.com> wrote:
Dear Benjamin,

Thank you for contacting Lexmark e-Support regarding your X4650. I really apologize for any inconvenience you may have experienced. Currently, we don't have any printer driver available that fully supports Ubuntu Linux 12.04 but I'll pass on your concern to our Product Engineers so we can address your concern properly and provide the best solution available.

If you have any more questions or concerns, please reply and reference Lexmark Service Request Number 1-8522488391 and we will be happy to assist you.

You may also call our technical support at 1-800-539-6275 or 1-800-332-4120, Mondays through Fridays, 8am-11pm EST and Saturday and Sunday, 11am-8pm EST; Chat support ([www.lexmark.com](www.lexmark.com)), Monday through Friday, 8am-11pm EST and Saturday, 11am-8pm EST.

Thank you again for contacting Lexmark e-Support.

Sincerely,
Efren
Lexmark e-Support Team
[http://support.lexmark.com](http://support.lexmark.com)


---

### Post by hbomb on 2012-05-01
Not good news at all. Since the printer was discontinued a while back this means that we most likely will not see updated drivers, which is sad as this printer still has a lot of life in it. :(

---

### Post by karlson on 2012-05-03
The issue is actually with Packaging rather then the driver itself.  From 11.10 to 12.04 dpkg requirement for Description field has changed not to allow blank lines which is what the problem is. :(

---

### Post by mips on 2012-05-03
See these threads,

[http://ubuntuforums.org/showthread.php?t=1571119](http://ubuntuforums.org/showthread.php?t=1571119)
[http://ubuntuforums.org/showthread.php?t=1021755](http://ubuntuforums.org/showthread.php?t=1021755)

Shows you how to get to the .deb file and install it.

---

### Post by karlson on 2012-05-03
> **mips said:**
> See these threads,

[http://ubuntuforums.org/showthread.php?t=1571119](http://ubuntuforums.org/showthread.php?t=1571119)
[http://ubuntuforums.org/showthread.php?t=1021755](http://ubuntuforums.org/showthread.php?t=1021755)

Shows you how to get to the .deb file and install it.

On 12.04 this won't help directly.  The issue is not package extraction but the field generation for the package.  Once the package is extracted ```
dpkg
``` will complain because **Description** value in the package information contains blank lines which as of 12.04 seems to be not allowed.

---

### Post by hbomb on 2012-05-03
Is it possible to edit the blank lines in order to "fool" dpkg into thinking that the field is populated and therefore lets the package install? Not sure if this can be done. :P

---

### Post by karlson on 2012-05-03
> **hbomb said:**
> Is it possible to edit the blank lines in order to "fool" dpkg into thinking that the field is populated and therefore lets the package install? Not sure if this can be done. :P

When I figure out how to do that I will post the info. :D

---

### Post by hbomb on 2012-05-03
> **karlson said:**
> When I figure out how to do that I will post the info. :D
Sweet! Thanks for all the help :)

---

### Post by karlson on 2012-05-07
Ok.  Here we go.

You can follow instructions in [http://ubuntuforums.org/showthread.php?t=1571119&page=2](http://ubuntuforums.org/showthread.php?t=1571119&page=2) on how to extract the package from the shell archive available for download.  Once that's done the following needs to take place.

```

dpkg-deb -x lexmark-inkjet-08-driver-1.0-1.i386.deb inkjet_install
dpkg-deb --control lexmark-inkjet-08-driver-1.0-1.i386.deb inkjet_install/DEBIAN
vi inkjet_install/DEBIAN/control

```

When editing change the **Description** field value to text not containing empty lines including the line at the **Description: ** tag itself.  When done with editing

```

dpkg -b inkjet_install new-lexmark-driver.deb

```

Now you will be able to install new-lexmark-driver.deb on the Precise.

Similar instructions can be found at [http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise](http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise)

---

### Post by hbomb on 2012-05-07
*"When editing change the Description field value to text not containing empty lines including the line at the Description: tag itself."* Can I just put any text in the line?

---

### Post by karlson on 2012-05-07
> **hbomb said:**
> Can I just put any text in the line?

**Description:** tag is a multiline text field.  If you want to put some garbage on that line you're entirely welcome to it.

---

### Post by hbomb on 2012-05-07
Ok, I have never done such a procedure before, so this will be a new one for me. I'm at work right now, when I get home later I will attempt this. :)

---

### Post by hbomb on 2012-05-09
Hi karlson,

I finally was able to get my printer installed and working. Many thanks for your help and research. Odd thing is though, when I ran the last cmd in your instructions ```
dpkg -b inkjet_install new-lexmark-driver.deb
``` I recieved the following error ```
hmccown@T400:~/Desktop$ dpkg -b inkjet_install new-lexmark-driver.deb
dpkg-deb: error: parsing file 'inkjet_install/DEBIAN/control' near line 8 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'

``` So I followed the instructions at [http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise]("http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise") and it worked perfectly. Once again, thanks for the help! :p

---

### Post by bedwards2000 on 2012-05-18
Thanks I was having the same issue with installing the driver after doing a fresh install upgrade to 12.04 from 10.04.  I successfully installed the driver and was able to print a test page with the printer connected to the desktop, but is there anyway to get it to also work wireless?  It might be something easy that I'm just not getting right now, but I thought I'd ask to see if anyone had that part working and exactly what they did to make that work.

---

### Post by julianloui on 2012-05-29
I downloaded from [http://users.cybercity.dk/~dko.12479]("http://users.cybercity.dk/%7Edko.12479") the following two rpm archives:

z700llpddk-2.0-1.i386.rpm (I'll refer to this below as z7 for brevity)
lexmark-z700-cups-driver-1.1.1-.i586.rpm (I'll refer to this below as lex for brevity)

I then performed the following in sequential order:
sudo alien -t   z7
sudo alien -t   lex
sudo tar xvzf  z700llpddk-2.0.tgz
sudo tar xvzf  lexmark-z700-cups-driver-1.1.1.tgz
sudo ldconfig
So far so good, but I soon encountered some error messages. Anyway, after much playing around, I ended up with the following new files:

z700llpddk-2.0.tar
lexmark-z700-cups-driver-1.1.1.tar
Lexmark-Z700-lxz700cje-cups.ppd

After a reboot, there is still no communication between Ubuntu 12.04 and the Z705.   When I try the following brute-force command, I receive an error from bash.
 
sudo cat test file.txt > /dev/lp0
bash: /dev/lp0: Permission denied.

1) What final files (in terms of file names) does all this extraction work lead up to?
2) How do you actually use them to link the O.S. with the printer in order to send a job to the printer?  

Thanks very much.

Julianloui

---

### Post by wingnux on 2012-07-19
> **karlson said:**
> ok.  Here we go.

You can follow instructions in [http://ubuntuforums.org/showthread.php?t=1571119&page=2](http://ubuntuforums.org/showthread.php?t=1571119&page=2) on how to extract the package from the shell archive available for download.  Once that's done the following needs to take place.

```

dpkg-deb -x lexmark-inkjet-08-driver-1.0-1.i386.deb inkjet_install
dpkg-deb --control lexmark-inkjet-08-driver-1.0-1.i386.deb inkjet_install/debian
vi inkjet_install/debian/control

```

when editing change the **description** field value to text not containing empty lines including the line at the **description: ** tag itself.  When done with editing

```

dpkg -b inkjet_install new-lexmark-driver.deb

```

now you will be able to install new-lexmark-driver.deb on the precise.

Similar instructions can be found at [http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise](http://askubuntu.com/questions/130516/lexmark-x6675-printer-on-precise)
thank you very much!!!

---

### Post by TMSpack on 2012-12-18
I tried a workaround using the the "fixed" package in the following article, but I got the same result.  Not sure what I am doing wrong.  Any ideas?

*[http://askubuntu.com/questions/130516/how-do-i-install-drivers-for-a-lexmark-x6675-printer](http://askubuntu.com/questions/130516/how-do-i-install-drivers-for-a-lexmark-x6675-printer)*

---

### Post by TMSpack on 2012-12-18
I tried the workaround described here:

*[http://askubuntu.com/questions/130516/how-do-i-install-drivers-for-a-lexmark-x6675-printer](http://askubuntu.com/questions/130516/how-do-i-install-drivers-for-a-lexmark-x6675-printer)*

but I had no luck- Has anyone been able to install this?

---

