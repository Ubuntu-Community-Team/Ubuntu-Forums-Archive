---
title: "Failed to intialize HAL"
date: 2007-08-24
forum: Egypt Team
---

### Post by moh980 on 2007-08-24
[SIZE="5"]when log in Ubuntu 7.04 i start getting an internal error message Failed to initialize HAL! and also no network connection! however i can connect to internet via LAN but can not connect wifi!
did i do something wrong caused this error?!
[/SIZE]

---

### Post by Farghal on 2007-08-24
Hi. When reporting a problem, please specify your computer specs so that members of the forum can help you identify problems quickly.

I see that in another thread you said you had a Toshiba Laptop, what is the model number? I have never had any problems with the wireless with the two Toshiba A100 laptops we have at our home, as the they both use an Intel wireless card, and these are well supported by Ubuntu.

Please reply with your Laptop model and specify what kind of wireless card does it use.. maybe someone over here with more experience than me can help you getting it working.

Cheers.

---

### Post by moh980 on 2007-08-24
[SIZE="4"]Sorry! i didnt provide more spec. 
my machine is Toshiba Satellite L10 and the wirless use to work just fine untill i start getting the Internal error message:Failed to initialize HAL! it will shows no network connection while i'm connected via LAN cable and i have access to the internet!
I start getting this error message after installed AutoMatix and rebooted system!

So, i believe its nothing to do with wirless card! since it was working before installing Automatix and the error message!
you can see the attached pic. 

Thx for your support[/SIZE]

---

### Post by Farghal on 2007-08-25
Oh, OK. So this is not a driver problem. it is just Automatix wreaking havoc on Ubuntu.

You see, simply put: **AUTOMATIX IS EVIL**! The Ubuntu community does not support it; at all. [See this link for more info]("https://wiki.ubuntu.com/AutomatixIssues").

---------------------------------------------------------------------------------

That said, let's see if we can mend your system. Try the following:

Disable the backports repository. Automatix has a habit of enabling that..

Open a terminal (Applications > Accessories > Terminal), copy and paste the following command:
```
sudo gedit /etc/apt/sources.list
```

Input your password

This will open a text editor, look for this part:

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://eg.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

Change the last two lines so they look like this (an additional # at the beginning of each line):
```
# deb http://eg.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://eg.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

Save the file. Close the window.

Type the following command:

```
sudo aptitude update
```

Then:

```
sudo aptitude reinstall hal
``` 

-------------------------------------------------------------------------------

I am not sure if this will work. So if I were you, If it doesn't work after this, I would try the following:

1- See if Automatix allows you to revert the changes it made. Open Automatix itself and look for any option that allows you to revert everything Automatix installed.
(You can probably re-install whatever it installed using Add/Remove Programs, if not, ask here and we'll try to help)

2- Ask on the [Automatix Forums]("http://www.getautomatix.com/forum/").

3- If all else fails, just reinstall Ubuntu again. And remember to **NEVER EVER USE AUTOMATIX AGAIN!!!**

I hope I helped. I was an Automatix user myself, but I found that there really is no need for it after Feisty came out. Trust me, Automatix is not worth the hassle.

Cheers. :-)

---

### Post by moh980 on 2007-08-26
Thank you very much for you help! 
I just took the shourt cut and reinstalled Ubuntu! :lolflag: since i'm still in dual boot, and actually using Wubi to install Ubuntu is so easy! and no more EVIL AutoMatix anymore!:)

day by day i'm loving Ubuntu more and more! today i found the desktop effect! WOW! it rocks :guitar:
Soon i will dump WIndows XP for ever!


Cheers!

---

### Post by tung148 on 2007-10-19
thanks, i got same problems ...

---

### Post by aiser on 2009-12-01
;)

---

