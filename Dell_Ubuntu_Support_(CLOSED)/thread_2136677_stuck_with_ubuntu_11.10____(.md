---
title: "stuck with ubuntu 11.10    :("
date: 2013-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abdorefky on 2013-04-18
[B]hi 
i bought a dell latptop from egypt . dell inspiron 5520  core i3 third generation
the laptop came with ubuntu , but with ubuntu 11.10  
ofc all drivers work , even i have dell recovery too on the ubuntu . as u can see on the middle [/B]

[IMG][[IMG]http://img14.imageshack.us/img14/585/dellrecovery.png[/IMG]]("http://imageshack.us/photo/my-images/14/dellrecovery.png/") 

[B]now  i want to upgrade to ubuntu 12.4 or 12.10 . or even 13.4 
sooner or later the support will stop ...
this is my hard disk [/B]

 [IMG][[IMG]http://img90.imageshack.us/img90/8581/screenshotat20130415135.png[/IMG]]("http://imageshack.us/photo/my-images/90/screenshotat20130415135.png/") 

[B][SIZE=3]my q[SIZE=3]ues[SIZE=3]tion[SIZE=3]s : [/SIZE][/SIZE][/SIZE]
1: how to upgrade ubuntu   and keep the dell recovery and the drivers ofc[SIZE=3]?[/SIZE]
2: should i be worried that ubuntu drivers update's miss with original drivers ? 
3: can i install new fresh install and make the dell recovery on the new install ? [/SIZE][/B]
[B][SIZE=3]4: where is the power setting like windows 7 :(  ?
5: where is touchpad setting like windows 7 ?
TY.

[/SIZE][/B]

---

### Post by abdorefky on 2013-04-18
i can\t even find power setting !! 
high performance , powersaver ...etc

---

### Post by abdorefky on 2013-04-18
as u can see the touchpad setting 

MG][[IMG]http://img805.imageshack.us/img805/2179/screenshotat20130418162.png[/IMG]]("http://imageshack.us/photo/my-images/805/screenshotat20130418162.png/") 

**[SIZE=4]now here is the joke [/SIZE]**
 [IMG][[IMG]http://img706.imageshack.us/img706/2179/screenshotat20130418162.png[/IMG]]("http://imageshack.us/photo/my-images/706/screenshotat20130418162.png/") 

[B][SIZE=5]forget about the touchpad i will search for [SIZE=5]linux driver [/SIZE]
i need the power options[/SIZE][/B]

---

### Post by abdorefky on 2013-04-18
[http://www.dell.com/support/drivers/us/en/19/ServiceTag/3ctlhv1](http://www.dell.com/support/drivers/us/en/19/ServiceTag/3ctlhv1)

[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

that might help ?

---

### Post by abdorefky on 2013-04-21
i think this problem happend after i made some ubuntu update's 
btw, this edition i customized by dell .. i allready tried to upgrade it and no way ..
what is this now .. the battery is full as u can see .. 

[http://ubuntuforums.org/showthread.php?t=2137570&p=12612302#post12612302](http://ubuntuforums.org/showthread.php?t=2137570&p=12612302#post12612302)

---

### Post by abdorefky on 2013-04-21
plz move this post to dell ubuntu support section

---

### Post by abdorefky on 2013-04-22
this version wont upgrade to higher version too 

[IMG][[IMG]http://imageshack.us/a/img9/5258/screenshotat20130418191.th.png[/IMG]]("http://imageshack.us/photo/my-images/9/screenshotat20130418191.png/")
[/IMG]

---

### Post by ibjsb4 on 2013-04-22
> **abdorefky said:**
> this version wont upgrade to higher version too 

Do you have your software sources set to do a release upgrade?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

A release upgrade can also be done in terminal.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

---

### Post by abdorefky on 2013-04-22
those terminal commands for ubuntu server ? or bother server and desktop or laptop

---

### Post by ibjsb4 on 2013-04-22
Terminal commands are for all the buntu's.

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by abdorefky on 2013-04-22
allright .. but i can't check the update setting because i am waiting for another post ;/ 
[http://ubuntuforums.org/showthread.php?t=2137897](http://ubuntuforums.org/showthread.php?t=2137897)
so i will wait some one answer me and check the setting u told me

---

### Post by abdorefky on 2013-04-22
1: i have 5 questions on the top of this post , u told me how to upgrade . but will this upgrade remove the dell recovery .

the size of this OS 1.5 GB and normal ubuntu 11.10 is 700 MB . so i am too much worried that upgrading ( even updating ) may remove some of dell factory setting and add normal setting that could harm the laptop or make it work in insufficient way ( like we hear all the time " fan on max load ...etc " ) , 

i dont know if the ubuntu update's could get near the " dell customized kernel system or the ubuntu system " or could not 

2 : what dell added to this ubuntu ? 

i have marked the question by 1 and 2 
there are some more question on the top of the post ;/ 

if u have some info about what dell added to ubuntu  i will be glad that u tell me .

---

### Post by ibjsb4 on 2013-04-22
I cannot say with any certainty what a release upgrade will do to your system.  In theory, you should end up with a working system and all the latest and greatest improvements.  This includes kernel upgrade.  But the bottom line is there are no guarantees.

A release upgrade should only affect the ubuntu partition and not your dell recovery partition.  And before you ask :) I have no idea what that recovery partition does.

You have multiple questions going on.  I think you need to decide on a course of action.  Repair of 11.10 seems futile to me, since its reaching EOL.

I currently have a dell testbox and a dell laptop that I treat no different from my IBM.  They are all older units so maybe thats why they give me no problems.  So I have no dell pacific info for you.

---

### Post by abdorefky on 2013-04-22
u miss understod me , i know that ext4 have nothing to do with dell partitions's 
i mean the dell installed setting " factory installed setting on ubuntu  etx4 partition "  which the setting that imported from the " ubuntu customized source on the dell partition " to ext4 during the  install 
i am worried to change those setting on the ext4 .. after update or upgrade .. 
and the only way to get those setting back is to use the recovery 

the recovery will set the laptop as the first time it started .. on the begain of the install .
my dell came with ubuntu label on it :) and when press power u are in the install :) ... 

i just made the recovey because of stupid programe called jupiter which missed with dell power setting , and set his own setting even after i close it .. or uninstall it :O

---

### Post by ibjsb4 on 2013-04-22
Sorry, my old Dells do not come with any such factory settings.  I cannot help you with this.

---

### Post by abdorefky on 2013-04-23
great i found the box  for notfiy me of new ubuntu verions , unchecked .. which mean i can upgrade 

ty very much .

---

### Post by abdorefky on 2013-04-30
abdo@abdo-Inspiron-5520:~$ do-release-upgrade
Checking for a new ubuntu release
No new release found
abdo@abdo-Inspiron-5520:~$

---

### Post by abdorefky on 2013-04-30
looks like i read wrong . u said " before u ask :D " on post 13 
and i read it as "like u ask"
that's why i said " u miss understood me " on post 14 
sorry **ibjsb4 **i am the one who read wrong and miss understand .

---

### Post by abdorefky on 2013-05-07
finally i got the upgrade notification and i upgraded to it . 

thx for all who help me

---

