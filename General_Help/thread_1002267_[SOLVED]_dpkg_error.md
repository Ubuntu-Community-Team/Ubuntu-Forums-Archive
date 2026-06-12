---
title: "[SOLVED] dpkg error"
date: 2008-12-04
forum: General Help
---

### Post by eternalnewbee on 2008-12-04
Hi there.
Can someone tell me how to solve this error? (see attachment)

---

### Post by abn91c on 2008-12-04
> **eternalnewbee said:**
> Hi there.
Can someone tell me how to solve this error? (see attachment)

there's no attachment but sudo dpkg --configure -a, then sudo apt-get install -f fixes a lot of dpkg errors

---

### Post by eternalnewbee on 2008-12-04
> there's no attachment but sudo dpkg --reconfigure -a, then sudo apt-get install -f fixes a lot of dpkg errors
Indeed. Thanks. There is one now:D
And I will try the sudo and come back.

---

### Post by eternalnewbee on 2008-12-04
> sudo dpkg --reconfigure -a
> sudo apt-get install -f
Didn't work. Got the same message...

---

### Post by falcon61102 on 2008-12-04
You may have a broken package or two.  Try going to the Synaptic Package Manager, then to Edit>Fix Broken Packages and see if that fixes it.

---

### Post by eternalnewbee on 2008-12-04
> You may have a broken package or two. Try going to the Synaptic Package Manager, then to Edit>Fix Broken Packages and see if that fixes it.
Thanks for your reply. Unfortunately, I can't get into Synaptic, as I get the error message and Synaptic disappears when I close the error message...

---

### Post by fooman on 2008-12-04
what error message do you get when you run this in a terminal:

```
sudo dpkg --reconfigure -a 
```

post the output please.

---

### Post by eternalnewbee on 2008-12-04
It's not on my own computer. It's my mother's. She just sent me a screenshot of the output:

---

### Post by fooman on 2008-12-04
she is combining 2 commands into one (sudo apt-get update sudo dpkg --reconfigure -a) .

have her run this command *only*:

```
sudo dpkg --reconfigure -a 
```

if that throws up an error...please post it.

if it runs without an error...*then* try this:

```
sudo apt-get update
```

---

### Post by falcon61102 on 2008-12-04
Have her try running the codes independently.

```
sudo dpkg --reconfigure -a
```

Then

```
sudo apt-get update
```

EDIT: Oops, I type too slow.

---

### Post by eternalnewbee on 2008-12-04
> EDIT: Oops, I type too slow.
Better two replies than one:D
OK. Next screenshot:

---

### Post by fooman on 2008-12-04
still not right...she did not include the 2 dashes in front of reconfigure.

must be *exactly* like this:

```
sudo dpkg --reconfigure -a
```

---

### Post by eternalnewbee on 2008-12-04
> still not right...she did not include the 2 dashes in front of reconfigure.

must be exactly like this:
I 'm starting to feel more and more embarrassed:oops::oops:
OK. Here we go again:
nadia@nadia:~$ sudo dpkg --reconfigure -a
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by eternalnewbee on 2008-12-05
Everybody who helped me in this thread are gone. Can anyone else assist?

---

### Post by fooman on 2008-12-05
your embarrassed??

sorry,  *i'm* embarrassed...try this:

```
sudo dpkg --configure -a
```

don't know where i was getting the "re"configure from.  ...my apologies.

---

### Post by eternalnewbee on 2008-12-05
> 
Re: dpkg error
your embarrassed??

sorry, i'm embarrassed...try this:

Code:

sudo dpkg --configure -a

don't know where i was getting the "re"configure from. ...my apologies.:D
No worries.
OK. Hold on (my mom's washing her hands)

---

### Post by eternalnewbee on 2008-12-05
OK. Here it is:
nadia@nadia:~$ sudo dpkg --configure -a
[sudo] password for nadia: 
Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...
Downloading...
--2008-12-05 16:19:39--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Resolving fpdownload.macromedia.com... 118.214.18.70
Connecting to fpdownload.macromedia.com|118.214.18.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3958745 (3.8M) [application/x-gzip]
Saving to: `./install_flash_player_10_linux.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 98.2K 39s
    50K .......... .......... .......... .......... ..........  2% 59.0K 51s
   100K .......... .......... .......... .......... ..........  3%  221K 39s
   150K .......... .......... .......... .......... ..........  5%  145K 35s
   200K .......... .......... .......... .......... ..........  6% 69.8K 38s
   250K .......... .......... .......... .......... ..........  7%  221K 34s
   300K .......... .......... .......... .......... ..........  9%  105K 34s
   350K .......... .......... .......... .......... .......... 10% 96.5K 33s
   400K .......... .......... .......... .......... .......... 11%  117K 33s
   450K .......... .......... .......... .......... .......... 12%  108K 32s
   500K .......... .......... .......... .......... .......... 14%  103K 32s
   550K .......... .......... .......... .......... .......... 15%  108K 31s
   600K .......... .......... .......... .......... .......... 16%  105K 31s
   650K .......... .......... .......... .......... .......... 18%  108K 30s
   700K .......... .......... .......... .......... .......... 19%  105K 30s
   750K .......... .......... .......... .......... .......... 20%  104K 29s
   800K .......... .......... .......... .......... .......... 21% 96.1K 29s
   850K .......... .......... .......... .......... .......... 23% 81.4K 29s
   900K .......... .......... .......... .......... .......... 24%  107K 28s
   950K .......... .......... .......... .......... .......... 25%  105K 28s
  1000K .......... .......... .......... .......... .......... 27%  107K 27s
  1050K .......... .......... .......... .......... .......... 28%  105K 27s
  1100K .......... .......... .......... .......... .......... 29%  108K 26s
  1150K .......... .......... .......... .......... .......... 31%  105K 26s
  1200K .......... .......... .......... .......... .......... 32% 72.5K 26s
  1250K .......... .......... .......... .......... .......... 33%  197K 25s
  1300K .......... .......... .......... .......... .......... 34%  104K 24s
  1350K .......... .......... .......... .......... .......... 36% 83.7K 24s
  1400K .......... .......... .......... .......... .......... 37% 76.4K 24s
  1450K .......... .......... .......... .......... .......... 38% 87.1K 23s
  1500K .......... .......... .......... .......... .......... 40% 97.7K 23s
  1550K .......... .......... .......... .......... .......... 41%  108K 22s
  1600K .......... .......... .......... .......... .......... 42%  105K 22s
  1650K .......... .......... .......... .......... .......... 43% 89.9K 21s
  1700K .......... .......... .......... .......... .......... 45%  105K 21s
  1750K .......... .......... .......... .......... .......... 46%  112K 20s
  1800K .......... .......... .......... .......... .......... 47% 81.4K 20s
  1850K .......... .......... .......... .......... .......... 49% 58.1K 20s
  1900K .......... .......... .......... .......... .......... 50%  107K 19s
  1950K .......... .......... .......... .......... .......... 51%  104K 19s
  2000K .......... .......... .......... .......... .......... 53%  108K 18s
  2050K .......... .......... .......... .......... .......... 54%  105K 18s
  2100K .......... .......... .......... .......... .......... 55% 94.0K 17s
  2150K .......... .......... .......... .......... .......... 56%  117K 17s
  2200K .......... .......... .......... .......... .......... 58% 94.9K 16s
  2250K .......... .......... .......... .......... .......... 59%  107K 16s
  2300K .......... .......... .......... .......... .......... 60%  101K 15s
  2350K .......... .......... .......... .......... .......... 62% 90.3K 15s
  2400K .......... .......... .......... .......... .......... 63% 83.6K 14s
  2450K .......... .......... .......... .......... .......... 64% 91.6K 14s
  2500K .......... .......... .......... .......... .......... 65% 83.6K 13s
  2550K .......... .......... .......... .......... .......... 67%  126K 13s
  2600K .......... .......... .......... .......... .......... 68% 48.0K 13s
  2650K .......... .......... .......... .......... .......... 69% 79.1K 12s
  2700K .......... .......... .......... .......... .......... 71%  107K 12s
  2750K .......... .......... .......... .......... .......... 72%  104K 11s
  2800K .......... .......... .......... .......... .......... 73%  102K 10s
  2850K .......... .......... .......... .......... .......... 75%  104K 10s
  2900K .......... .......... .......... .......... .......... 76%  107K 9s
  2950K .......... .......... .......... .......... .......... 77% 80.9K 9s
  3000K .......... .......... .......... .......... .......... 78% 92.2K 8s
  3050K .......... .......... .......... .......... .......... 80% 92.6K 8s
  3100K .......... .......... .......... .......... .......... 81%  105K 7s
  3150K .......... .......... .......... .......... .......... 82%  108K 7s
  3200K .......... .......... .......... .......... .......... 84%  105K 6s
  3250K .......... .......... .......... .......... .......... 85% 85.0K 6s
  3300K .......... .......... .......... .......... .......... 86% 91.8K 5s
  3350K .......... .......... .......... .......... .......... 87%  108K 5s
  3400K .......... .......... .......... .......... .......... 89% 92.2K 4s
  3450K .......... .......... .......... .......... .......... 90%  102K 4s
  3500K .......... .......... .......... .......... .......... 91% 90.6K 3s
  3550K .......... .......... .......... .......... .......... 93%  105K 3s
  3600K .......... .......... .......... .......... .......... 94%  108K 2s
  3650K .......... .......... .......... .......... .......... 95%  105K 2s
  3700K .......... .......... .......... .......... .......... 97%  108K 1s
  3750K .......... .......... .......... .......... .......... 98% 94.1K 1s
  3800K .......... .......... .......... .......... .......... 99%  122K 0s
  3850K .......... .....                                      100%  107K=40s

2008-12-05 16:20:19 (97.7 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3958745/3958745]

Download done.
Flash Plugin installed.

---

### Post by fooman on 2008-12-05
sorry, i gotta leave for work.

if that command goes without error,  then try this next:

```
sudo apt-get update
```

and if that goes without error,  finally run this:

```
sudo apt-get upgrade
```

good luck,  hope that helps.

---

### Post by eternalnewbee on 2008-12-05
Thanks for your help fooman. Really appreciate it.

---

### Post by Anvariel on 2008-12-05
I have the same problem only when I run sudo dpkg --configure -a it freezes at the following point:

anjjo53@anjjo53-desktop:~$ sudo dpkg --configure -a
Setting up language-pack-sv-base (1:7.10+20080205) ...
Generating locales...
  sv_FI.UTF-8... 

And it just stays there. Any hints?

---

### Post by eternalnewbee on 2008-12-06
> And it just stays there. Any hints?
Sorry anvariel. No idea.
Btw, this thread is now solved. No dpkg errors anymore, after:
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```
and ```
sudo apt-get upgrade
```
Thanks again fooman.

---

### Post by Anvariel on 2008-12-06
My problem is now also solved. I did something along the lines of these:

sudo dpkg -P language-pack-sv
sudo dpkg -P language-pack-sv-base
sudo dpkg -a --configure
sudo apt-get update
sudo apt-get install language-pack-sv-base
sudo apt-get dist-upgrade

---

