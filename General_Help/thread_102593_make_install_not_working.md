---
title: "make install not working"
date: 2005-12-12
forum: General Help
---

### Post by maccom on 2005-12-12
i am trying to install linux firmware for my speedtouch 330 modem.
i have configured everything but when i type into root terminal : "make, make install" 
it says: Bash : make command not found
so then i tried "sudo make, sudo make install"
and then it says: "sudo make command not found"

what is happening....what can i do??

---

### Post by DrBair on 2005-12-12
Funny question, but we have looked at the INSTALL file for this, right?

Next thing is to make sure you have the make package installed, you'll probably need the rest of the build-essentials package as well if you don't have that already.

---

### Post by carlosqueso on 2005-12-12
EDIT: DrBair got to it first....

---

### Post by maccom on 2005-12-12
i have followed a tutorial on the [wiki.ubuntu.com/UKSpeedtouchDSLHowTo](wiki.ubuntu.com/UKSpeedtouchDSLHowTo) downloadsed the firmware from the alcatel website and the firmware-extractor.

i followed the readme in firemware-extractor...

extract, copy correct firmware, then ./configure then make, make install

it is here i get the errors.
i am a n00b and this is the first thing i am installing!!

is it something i have done, or a missing file?... i cant remember seeing an INSTALL fie in the extracted firmware-extractor

---

### Post by carlosqueso on 2005-12-12
Okay...you probably don't have the build-essentials package.  Open a terminal and type ```
sudo apt-get install build-essential
```  After that installs,   you should then be able to go to the directory in which the firmware resides and type ```
./configure
make
sudo make install
```  As long as you install build-essentials FIRST it should work.


Edit...fixed my misspelling

---

### Post by maccom on 2005-12-14
sorry for the delay.

i tried the apt-get install build-essentials and i got the error

```
E: couldn't find package build-essentials
```


which probably means its not installed??!!  is there somewhere i can download it??

edit: typos!!

---

### Post by hod139 on 2005-12-14
The package name is build-essential, not essential**s**
```

sudo apt-get install build-essential

```

---

### Post by teaker1s on 2005-12-14
If you don't have internet access and Build-essential isn't on the install cd you will have a problem

---

### Post by maccom on 2005-12-14
[QUOTE=hod139]The package name is build-essential, not essential**s**
```

sudo apt-get install build-essential

```[/QUOTE]

ok i was told essentialS ill try that.

tia

---

### Post by carlosqueso on 2005-12-14
my bad, typing ran faster than my brain.

---

### Post by maccom on 2005-12-14
no worryies...

i have followed
[wiki.ubuntu.com/UKSpeedtouchDSLHowTo](wiki.ubuntu.com/UKSpeedtouchDSLHowTo)
and got everything installed now, thanks for thati have configure the adsl, chap and pap-secrets files.
then it says to go to terminal and type "pon adsl" its says that its loaded the script (can't remember the file name soz) then is there anything else to do, as when i go to firefox and go to google.com it can't connect.

TIA

---

### Post by tlc on 2005-12-14
What's in your /etc/resolv.conf file?

```
sudo nano /etc/resolv.conf
```

There should be two lines - your DNS servers, in the format:

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

with the x's being the IP addresses of the servers.

---

### Post by maccom on 2005-12-15
... nothing is in my /etc/resolv.conf file

come to think of it...my ip is only given to me once i connect.


(again sorry for the delayed reply)

---

### Post by tlc on 2005-12-15
Well then, *put* something in your /etc/resolv.conf file... ;)  The DNS servers that your ISP uses, for instance... :p

---

### Post by maccom on 2005-12-15
> The DNS servers that your ISP uses, for instance...  

where do i find these...?   
i'm with wanadoo UK

---

### Post by tlc on 2005-12-15
[http://www.wanadoo.co.uk/help/connection/freeservesettings.htm?linkfrom=Time_ret_rest_account&link=Additional_help_button](http://www.wanadoo.co.uk/help/connection/freeservesettings.htm?linkfrom=Time_ret_rest_account&link=Additional_help_button)

```
DNS
Domain name service is dynamic - but if domain name server (DNS) addresses 
are required, you should use 195.92.195.94 and 195.92.195.95

 
```

---

### Post by maccom on 2005-12-15
thanks tlc, i am just going to try this now...

---

### Post by tlc on 2005-12-15
*forum user follows tlc's advice, is never heard from again...* :p

---

### Post by maccom on 2005-12-15
[QUOTE=tlc]*forum user follows tlc's advice, is never heard from again...* :p[/QUOTE]


unfortunatly not true....

it still don't connect...

what to try next?

---

### Post by tonysathre on 2005-12-15
are u connecting with a cat 5 or some kinda network cable to your modem, if so open your network settings and enable your NIC

---

### Post by maccom on 2005-12-15
no im not...i'm trying to use my speedtouch 330 USB

---

