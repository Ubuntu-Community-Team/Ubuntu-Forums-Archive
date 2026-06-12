---
title: "XBMC on UBUNTU 11.04"
date: 2011-05-24
forum: Desktop Environments
---

### Post by 0SNiX on 2011-05-24
Installed ubuntu 11.04 today to use xbmc on it, i can"t get it to install and tried everything i can find to make it work without any luck. can someone help me get this work :confused:

I hope i can get xbmc running on this OS as it"s smooth as hell (im loving it)

---

### Post by 0SNiX on 2011-05-24
This is what i see when trying

sudo apt-get install xbmc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xbmc



got it working by 

sudo add-apt-repository ppa:team-xbmc

Since that adds a repository supposed to work for Natty, which isn&#8217;t available just yet, I then proceeded to do the following:
Go to the Package Manager. Click *Settings* -> *Repositories*. Under &#8220;Other Software&#8221;, highlight the XBMC PPA and click *Edit*. For the distribution, change it to *maverick*.

Then
sudo apt-get update
sudo apt-get install xbmc

---

### Post by papibe on 2011-05-24
Original post:
> You need a few more steps:
```
$ sudo add-apt-repository ppa:team-xbmc
$ sudo apt-get update
$ sudo apt-get install xbmc
$ sudo apt-get update
```
For more information check the XBMC's wiki [pages]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide").
Regards.

EDIT: there's no version for Natty 11.4 in that repository. However there's a version in their unstable ppa:

```
ppa:team-xbmc/unstable
```

---

### Post by leftkidney on 2011-05-27
it doesent work

you cant add 3rd party software sources apparently

I am probably going back to 10.10 or 10.04 because everything worked properly there, this "new" is just crap imo

---

### Post by papibe on 2011-05-27
> **leftkidney said:**
> it doesent work
You are correct, the last instructions do not work.

> **leftkidney said:**
> you cant add 3rd party software sources apparently
You have a misconception here. You can add the xbmc ppa, so you're allowed to add 3rd party software. What is happening is that 'ppa:team-xbmc' does not contain a specific version for Natty.

As today, it is in the unstable ppa:
```
ppa:team-xbmc/unstable
```
Feel free to go ahead and ask the people who maintain the ppas ([Team XBMC]("https://launchpad.net/~team-xbmc")) to add an version for Natty in the stable one. Another good place would be the [XBMC forums]("http://forum.xbmc.org/").

Regards.

---

### Post by 0SNiX on 2011-05-27
> **leftkidney said:**
> it doesent work

you cant add 3rd party software sources apparently

I am probably going back to 10.10 or 10.04 because everything worked properly there, this "new" is just crap imo

It does work, works great actually am using xbmc on 11.04 now :D

---

### Post by notcosi on 2011-05-29
unstable ppa worked for me

---

### Post by 86themachine on 2011-05-31
Give this a try.

Credit to:
[http://magvar.wordpress.com/2011/05/15/xbmc-running-on-ubuntu-11-04/](http://magvar.wordpress.com/2011/05/15/xbmc-running-on-ubuntu-11-04/)


                       [SIZE=2]Since I&#8217;d installed Ubuntu 11.04 on the machine earlier, and [XBMC]("http://ubuntuforums.org/http%3a//www.xbmc.org") doesn&#8217;t officially exist on 11.04, I did a little &#8220;fix&#8221; (found on the net) to get it installed.
[/SIZE] [SIZE=2][FONT=Courier]sudo add-apt-repository ppa:team-xbmc[/FONT][/SIZE]
[SIZE=2]Since that adds a repository supposed to work for Natty, which isn&#8217;t available just yet, I then proceeded to do the following:
 Go to the Synaptic Package Manager under System Settings. 
[/SIZE]
[SIZE=2]Click *Settings* -> *Repositories*. Under &#8220;Other Software&#8221;, highlight the XBMC PPA and click *Edit*. For the distribution, change it to *maverick*.[/SIZE]
    [SIZE=2]Then, I did;
[FONT=Courier]sudo apt-get update
 sudo apt-get install xbmc[/FONT][/SIZE]

---

### Post by ruimarto on 2011-07-04
And for those who don't have a GUI? I can't go to "Settings > bla bla bla" in the terminal. :(

---

### Post by ramoncio on 2011-07-09
This worked perfect for me from console:

```

sudo add-apt-repository ppa:team-xbmc/unstable
sudo apt-get update
sudo apt-get -y install xbmc
 
```

---

### Post by papampi on 2011-07-26
unstable works !!!!
thanks.

---

### Post by adhitya369 on 2011-08-09
Works for me. Thanks

---

### Post by xltrigger on 2011-08-24
Adding unstable didn't work for me. Editing /etc/apt/sources.list.d/team-xbmc-ppa-natty.list and changing both lines from natty to maverick did work for me on an install I did a few weeks ago.

---

### Post by lovetaart on 2011-12-12
Solved.. thanks :)
I try using step at #2 post and it works well in my laptop :P

---

### Post by luiang on 2011-12-17
XBMC on Ubutnu11.04&#65292;I should need to wait.Because XBMC work on ARM so difficult,It is used with Ubuntu.04.
The good news is that after today we can see on the market to run XBMC in CortexA8.[http://www.bodtek.com/](http://www.bodtek.com/)

---

