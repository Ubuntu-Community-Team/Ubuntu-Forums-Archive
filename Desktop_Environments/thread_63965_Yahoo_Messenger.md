---
title: "Yahoo Messenger"
date: 2005-09-09
forum: Desktop Environments
---

### Post by srinath on 2005-09-09
Debian Linux

   1. Save the file to your machine.
   2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.


How do I install this? How am I supposed to go about doing this?

---

### Post by KingBahamut on 2005-09-09
[QUOTE=srinath]Debian Linux

   1. Save the file to your machine.
   2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.


How do I install this? How am I supposed to go about doing this?[/QUOTE]
 open up a terminal 

cd to the directory that has the file 

type 

sudo dpkg -i ymessenger_1.0.4_1_i386.deb

once finished 

back on the Desktop 

go 

Applications > Run Application > ymessenger 
hit enter. 

should be good. 

I do note however that when I have to use yahoo messenger, I find that setting up gaim to use yahoo is better, and alot more aggreeable than the dated Yahoo client that Yahoo themselves provide. you Should try that instead, Im thinking.

---

### Post by bob_c_b on 2005-09-09
[QUOTE=KingBahamut]
I do note however that when I have to use yahoo messenger, I find that setting up gaim to use yahoo is better, and alot more aggreeable than the dated Yahoo client that Yahoo themselves provide. you Should try that instead, Im thinking.[/QUOTE]

Agreed, I converse on Yahoo with a long time friend every week and we have both found GAIM to be far more usable than the dated Yahoo client. We also like the idea of supporting a true OSS project and hope that Yahoo sees enough people using other clients to make an impact, but alas, we can dream. ](*,)

---

### Post by rafakl on 2005-09-09
Yes, i think gaim is more stable than the dated client. Its better to support gaim than a bad client.

But gaim need a a little more improvement in usability....

---

### Post by leetran on 2005-09-09
i'm using Giam now...
but ma internet connection using Proxy
after finish adding yahoo acc and try to connect 
they come out with error message:" porxy connection error 502"
do u know what to do with this?

---

### Post by bonjun on 2005-09-10
[QUOTE=srinath]Debian Linux

   1. Save the file to your machine.
   2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.[/QUOTE]

I followed the instruction 1 &2, but this is what happen;

=====
root:/home/bonjun/Desktop # sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 60596 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
=====

this what came out with the terminal,,,
i don't know what to do?

---

### Post by jobezone on 2005-09-10
[QUOTE=bonjun]I followed the instruction 1 &2, but this is what happen;

=====
root:/home/bonjun/Desktop # sudo dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 60596 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
=====

this what came out with the terminal,,,
i don't know what to do?[/QUOTE]
 Still want to use yahoo messenger instead than gaim? Anyway, try running ```
sudo apt-get -f install
```.

---

### Post by bonjun on 2005-09-10
[QUOTE=jobezone]Still want to use yahoo messenger instead than gaim? Anyway, try running ```
sudo apt-get -f install
```.[/QUOTE]

geee,,, thanks, it works now,,
it is not that i don't want to use gaim, i'm a newbie to linux and i want to try different things especially in installing programs,,, thanks for your help, it works now... :)

---

### Post by srinath on 2005-09-10
[QUOTE=bonjun]geee,,, thanks, it works now,,
it is not that i don't want to use gaim, i'm a newbie to linux and i want to try different things especially in installing programs,,, thanks for your help, it works now... :)[/QUOTE]


I saw GAIM after I posted here. But like my friend here I am new to Linux and want to learn stuff!

---

### Post by Goffy on 2005-10-12
Who needs MSN, icq or Yahoo when we have GAIM? 
Damn, I just like UBUNTI better and better!!

---

### Post by BLTicklemonster on 2005-10-12
I like using Gaim, but we have our meetings on Yahoo, and I'm the one who instigates it. Meaning I invite all to a conference. I didn't see that option in gaim. 

I had no problem setting up ymessenger, except that it didn't make an automatic place to launch it in my applications. So I added it, /usr/bin/ymessenger and when I click on it, it tries to install it again.

What now?

---

