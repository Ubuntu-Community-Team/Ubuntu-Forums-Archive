---
title: "changing date format"
date: 2011-10-03
forum: Desktop Environments
---

### Post by hasfar on 2011-10-03
REALLY  need help!!!
im trying to change my date format. several links point to this page as a guide
[http://ccollins.wordpress.com/2009/01/06/how-to-change-date-formats-on-ubuntu/](http://ccollins.wordpress.com/2009/01/06/how-to-change-date-formats-on-ubuntu/)

im using these commands:
1)cd /usr/share/i18n/locales
2)sudo cp en_US custom
3)sudo gedit custom
3) i then change the string using unix code to get a d/m/y format and save the file on the text editor.
4)then in the same terminal window i enter 
sudo localedef -f UTF-8 -i custom custom.UTF-8

then the page tells me this:

5)[SIZE=2][I]Do this by editing the file /etc/environment (sudo gedit /etc/environment) and adding (or modifying) the line: LC_TIME="custom.UTF-8"

[/I][FONT=Arial][SIZE=2]**when i put in **[/SIZE][/FONT][/SIZE][SIZE=2]*sudo gedit /etc/environment **i get a text editor page which shows me this:  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"***[/SIZE][SIZE=2][FONT=Arial][SIZE=2]    what should i do.where should i put in the '[/SIZE][/FONT][/SIZE][SIZE=2]*LC_TIME="custom.UTF-8' command that step 5 tells me to *[/SIZE]
[SIZE=2][I][FONT=Arial][SIZE=2]
Could someone help me with step 5 in detail.where do i put in the commands etc[/SIZE][/FONT][/I][/SIZE]

---

### Post by Frogs Hair on 2011-10-03
One way to change regional formats , such as date and denominations is to open Language Support > Regional Formats . Choose the region you want and apply system wide .

---

### Post by Krytarik on 2011-10-03
> **hasfar said:**
> [SIZE=2][FONT=Arial][SIZE=2]**when i put in **[/SIZE][/FONT][/SIZE][SIZE=2]*sudo gedit /etc/environment **i get a text editor page which shows me this:  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"***[/SIZE][SIZE=2][FONT=Arial][SIZE=2]    what should i do.where should i put in the '[/SIZE][/FONT][/SIZE][SIZE=2]*LC_TIME="custom.UTF-8' command that step 5 tells me to *[/SIZE]
How about right below of that line, like this!?:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LC_TIME="custom.UTF-8"
```Hope that works!

---

### Post by hasfar on 2011-10-04
> **Krytarik said:**
> How about right below of that line, like this!?:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LC_TIME="custom.UTF-8"
```Hope that works!



@krytarik.   yes i did that and it didnt work at first. i had been trying all of this for 4 hours. then all of a sudden the settings just applied. ive started using ubuntu/lubuntu/ xubuntu  3 months ago. and in my experience its an extremely bugridden and user unfriendly piece of software.ubuntu wont go mainstream until the guys who program  it realize that 95% of computer users are not tech gurus. they should hold off on new releases and make sure that the one they r going to release is properly tested and bug free.

@krytarik and @ frogs hair  :   thank u both for your help. i really appreciate that you replied

---

### Post by Krytarik on 2011-10-04
> **hasfar said:**
> yes i did that and it didnt work at first. i had been trying all of this for 4 hours. then all of a sudden the settings just applied. ive started using ubuntu/lubuntu/ xubuntu  3 months ago. and in my experience its an extremely bugridden and user unfriendly piece of software.ubuntu wont go mainstream until the guys who program  it realize that 95% of computer users are not tech gurus. they should hold off on new releases and make sure that the one they r going to release is properly tested and bug free.
Actually? Maybe you should have rebooted after adding those setting - which is, btw., the ubiquitous habit if you are using Windows! Most people don't really get that they don't need to do so in Linux most of the time, especially if they are new to Linux, but sometimes that's needed here, too. ;-)

And talking about "properly tested and bug free" operating systems; if you are that happy and convinced of the 'quality' of Windows, why did you start using Ubuntu in the first place!? :-k

Greetings.

---

### Post by hasfar on 2011-10-04
> **Krytarik said:**
> Actually? Maybe you should have rebooted after adding those setting - which is, btw., the ubiquitous habit if you are using Windows! Most people don't really get that they don't need to do so in Linux most of the time, especially if they are new to Linux, but sometimes that's needed here, too. ;-)

And talking about "properly tested and bug free" operating systems; if you are that happy and convinced of the 'quality' of Windows, why did you start using Ubuntu in the first place!? :-k

Greetings.

i think i didnt make myself clear. i rebooted like 20 times man. secondly windows has its problems but it is a lot more user friendly.how many times have u had to put in ms dos- like commands. for a new guy to ubuntu/linux how will he know which command to put in. it seems like for extremely simple tasks im on the internet browsing forums on how to do a simple task or what terminal garbage i have to enter.pls dont get me wrong i luv ubuntu. but at this point i feel like the guy who bought a really cool car against conventional wisdom and then realised that other people didnt buy it for a good reason

anyway i hope im wrong.im lookinf forward to ubuntu 11.10. cheers :)

---

### Post by Krytarik on 2011-10-04
> **hasfar said:**
> it seems like for extremely simple tasks im on the internet browsing forums on how to do a simple task or what terminal garbage i have to enter.
Well, I want to point out that my retired mom is using Ubuntu, too, alone! And she's loving it, way over Windows, which I installed her first when I bought her the computer. Of course, I need to do some administrative tasks every couple of months; and yeah, she doesn't try changing things like the date format in a way no-one else does. ;-) But once it's set up, Ubuntu runs like a tank, and updates every parts of it automatically - meaning including the installed apps; which you can't say at all from Windows, you've got to admit. In contrast, you have to put a lot of work into a Windows installation only to keep it nearly at the same level when you set it up, not to mention all the malware stuff. User friendly, really!?

The same is true for the installation of apps; in Ubuntu you can use the Software Center or Synaptic, and yeah, also the command line to easily install apps that are in the repositories, and all most common and even lesser common apps are included in them; in Windows you don't even have repos, you have to download and install every app on your own. Again, user friendly!?

---

