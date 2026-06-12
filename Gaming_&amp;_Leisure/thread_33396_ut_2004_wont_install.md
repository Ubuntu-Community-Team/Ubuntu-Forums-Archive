---
title: "ut 2004 wont install"
date: 2005-05-10
forum: Gaming &amp; Leisure
---

### Post by tlaloczint on 2005-05-10
first hi to all
 I have been tring to install ut 2004 but I cant for some reason I have the cd version 
when I put the cd it open as folders then I click on the linux installer then a 
window open asking if I want to RUN IN TERMINAL, DISPLAY, CANCEL, RUN,
now when I click in run nothing happen if I click on RUN IN TERMINAL it open a terminal window for about half of second and desapear  
 
I dont know how to show al the media drives but I have to dvd writers 

I hope that someone can help me 

thanks you.

---

### Post by NeoChaosX on 2005-05-10
You're supposed to to run the installer as root. Open a terminal, browse to the CD (/media/cdrom0) and type in "sudo ./linux-installer.sh"

---

### Post by tlaloczint on 2005-05-10
I have the same thing or sorry If I am doing someting wrong here but I have this 


root@moony:/home/tlaloczint # cd /media/cdrom0
root@moony:/media/cdrom0 # sudo ./linux-installer.sh
sudo: unable to execute ./linux-installer.sh: Permission denied
root@moony:/media/cdrom0 #

I log in as root but still I don`t know what I am doing wrong...and 
if I do it in terminal I got the same result as before If I chose RUN IN TERMINAL 
just splash and its gone

---

### Post by crane on 2005-05-10
[QUOTE=tlaloczint]I have the same thing or sorry If I am doing someting wrong here but I have this 


root@moony:/home/tlaloczint # cd /media/cdrom0
root@moony:/media/cdrom0 # sudo ./linux-installer.sh
sudo: unable to execute ./linux-installer.sh: Permission denied
root@moony:/media/cdrom0 #

I log in as root but still I don`t know what I am doing wrong...and 
if I do it in terminal I got the same result as before If I chose RUN IN TERMINAL 
just splash and its gone[/QUOTE]

Try copying it to you home directory then running it. I didn't think you had to be root to install. Also try using sh in front of command. 
[color=blue]#sh /media/cdrom/linux-installer.sh[/color]
Just a thought.

---

### Post by tlaloczint on 2005-05-11
well finally it did install well I hope but when I try to play it it only show a splash screen 
and then this   

WARNING: ALC_EXT_capture is subject to change!


I really hope not go back to ms just to play ut lol!

---

### Post by crane on 2005-05-11
[QUOTE=tlaloczint]well finally it did install well I hope but when I try to play it it only show a splash screen 
and then this   

WARNING: ALC_EXT_capture is subject to change!


I really hope not go back to ms just to play ut lol![/QUOTE]

I don't know if you've seen the post before but, is your desktp res the same as the game res.? Try setting them the same and see if it will start.

---

### Post by tlaloczint on 2005-05-12
[QUOTE=crane]I don't know if you've seen the post before but, is your desktp res the same as the game res.? Try setting them the same and see if it will start.[/QUOTE]


well I have done all the posible things to it but still I got the same just the splash screen and its gone also I have the same thing  

WARNING: ALC_EXT_capture is subject to change! on all resolutions so I just give up I thing I just have to dual boot to xp  just to play it thats prety much what I use it for.

thank you very much guys... wait I may be able to install it with cedega i`ll try that

---

### Post by SWAT on 2005-05-13
Strange, I installed UT2004 without any problems. But you really need to run as root and then let the script do his thing. Did you update UT2004 with the newest patch? And do you have the newest 3D graphics drivers on your system?

UT2004 is Linux NATIVE, so you don't need Cedega. UT2004 isn't even supported by Cedega, because it works under Linux (no emulation needed)

---

### Post by crane on 2005-05-13
I agree with Swat. No need for cedega.
What vid card are you running? I have read where reinstalling vid drivers helped this problem.

I did a search as well. This is not just an UBuntu problem. I found the same post on mandrake, fedora, Suse and other forums. Maybe a serious google search would yield some answers!!

Oh is that the intire error or is there antthing after it that is relezant.

---

### Post by tlaloczint on 2005-05-13
QUOTE=crane]I agree with Swat. No need for cedega.
What vid card are you running? I have read where reinstalling vid drivers helped this problem.

I did a search as well. This is not just an UBuntu problem. I found the same post on mandrake, fedora, Suse and other forums. Maybe a serious google search would yield some answers!!

Oh is that the intire error or is there antthing after it that is relezant.[/QUOTE 


ok... well I was going to ask for help I installed suse  9.3 and I got the same thing 
so I think its my pc this is as shows

grafics
aiw 9800 pro 128 mb the chip say something about 350 some I not sure
motherboard
abit model # is av8 
athlon 64 3500+ 939 pin
monitor sansung synmaster 172n
power suply is 520w  12v
260 gb western digital hdd
120 maxtror hdd

i have the 260 as master in wich I have xp
the 120 is as slave in I install ubuntu in it
now I think that the problem lies in I cant enable 3d and the other thing ... opengls or something . I tried yesterday but screw the x window lol the install it suse same thing so now I am back to ubuntu to see if someone can help me how to configure my grafics card...

and well thank everybody for being patient and your support

---

### Post by SWAT on 2005-05-14
Okay, here it goes. I would REALLY check if you have the correct graphics drivers installed. I know that the newest ATI drivers fix a UT2004 onslaught performance problem, so I would use the newest drivers. Here's a small howto (it worked perfectly for me):

[I]1. Download official driver .rpm from the ATI website.
2. Remove fglrx packages using synaptic.
3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
4. cd to where you downloaded the driver rpm file.
5. sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig
Source: [http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)[/I]

Another howto which may REALLY be relevant is this one: 
[http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)

You can check if your performance increases by using "glxgears" (check output BEFORE and AFTER the driver install)

---

### Post by tlaloczint on 2005-05-15
[QUOTE=SWAT]Okay, here it goes. I would REALLY check if you have the correct graphics drivers installed. I know that the newest ATI drivers fix a UT2004 onslaught performance problem, so I would use the newest drivers. Here's a small howto (it worked perfectly for me):

[I]1. Download official driver .rpm from the ATI website.
2. Remove fglrx packages using synaptic.
3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
4. cd to where you downloaded the driver rpm file.
5. sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig
Source: [http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)[/I]

Another howto which may REALLY be relevant is this one: 
[http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)

You can check if your performance increases by using "glxgears" (check output BEFORE and AFTER the driver install)[/QUOTE]


 ](*,)  ohh men! I give up I can`t figure out  I start about  3:30 this afternoon and still cant make it to work I try step by step all post about how, but I just cant  make it to work... I mess it up five times now I did a fresh install dowload everything( twice)as in the how to, but still with out luck I just but ... I have to say ubuntu is better than the rest linux distros so far I got all my hardware working ok (printer, digital camera, scanner, something that I could`nt in other distros well... I`ll keep up reading and keep trying to see if there is something more easier later
in the how to.

I have to say the support is really good I am still waiting in the forums of suse 9.1 in how to enable the 3d and here was just super, thanks I going to keep using ubuntu as my favorite distro.    thanks for your great support \\:D/  :-)

now its about 11.30 pm I am tired and craby take a good sleep and tomorrow I`ll tried one more time \.

---

### Post by ZeroA4 on 2005-06-07
Have you try to run as root ?

Once i installed it as root and the last window of the installer shows a "Start" button. I pressed it and a .ut2004 dir was created in the home of my user but owned by the root! I rm the dir and started the game as a normal user and it re-created the dir but with the user as owner this time.

---

### Post by professor_chaos on 2005-06-08
Just to make sure, as I didn't see reference in the postings that the file is made executable. 
an "ls -l" should report x's on the owner and group categories. 
If the file is not executable it will report Permission denied when executing.

If not exectuable, type "sudo chmod 777 enterfilehere"
then ./filename

You probably did this, but reading the post I wasn't sure

---

### Post by RastaMahata on 2005-06-08
try sudo **sh** ./linux-insta... bla bla

---

### Post by chokfulla on 2005-07-18
[QUOTE=SWAT]Okay, here it goes. I would REALLY check if you have the correct graphics drivers installed. I know that the newest ATI drivers fix a UT2004 onslaught performance problem, so I would use the newest drivers. Here's a small howto (it worked perfectly for me):

[I]1. Download official driver .rpm from the ATI website.
2. Remove fglrx packages using synaptic.
3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
4. cd to where you downloaded the driver rpm file.
5. sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig
Source: [http://ubuntuforums.org/archive/index.php/t-24763.html](http://ubuntuforums.org/archive/index.php/t-24763.html)[/I]

Another howto which may REALLY be relevant is this one: 
[http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)

You can check if your performance increases by using "glxgears" (check output BEFORE and AFTER the driver install)[/QUOTE]

  I tried the instructions you posted here and step #7 gave me a problem.  It said that I needed a "command option"  or something.  I checked the man page for dpkg and played around a little and finally got it to work with:
dpkg --force-overwrite -i fglrx_6_8_0-8.10.19-1.i386.deb
  I had to add the -i between overwrite and fglrx...
 I don't know if it's different on other systems but that's how I got it to work.
  Also, I could never get step 9 (and beyond) to work right.  I'm not sure what I was missing.
  I was finally able to finish installing the driver by completing steps 1-7 here and then:
sudo apt-get install gcc
then:
followed the instructions posted by Jesus Franco "HowTo: Ati FGLRX 8.14.13" here:
[http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)
 My glxgears speed went from about 1800 fps to ~4000 fps  ---- Butta!!

AMD Athlon64 3500+
1 Gb Corsair XMS
MSI Neo 2 Platinum
ATI AIW 9800 Pro 128 Mb
WD 74 Gb Raptor
WD 250 Gb
Triple Boot: XP Pro - FC4 - Ubuntu (Hoary)

---

### Post by Benzima on 2005-10-04
Been banging my head onto the keyboard for 2 weeks now trying to figure out how to install. Moving the install file to /home/username did the trick.

Thanxxx !!!!

Any tips on installing patches and maps?

Once again, spoke too soon. Game won't run. Argh!!! Time for bed.

---

### Post by daejavu on 2005-10-07
Guyz .. heres a new situation for u .
ive read this whole thread and a problem occured in my installation as well 

i copied the linux-installer on me home directory and did a "sudo sh linu-installer"  on it .. the installer started asked for the serial ... and then after just a couple of seconds asked me to put in the ut2004 play CD ??:confused: 
now im using a DVD as the installation medium ... it shouldnt be asking me for the next CD but it does .. and if i say OK it ask me again and dosent continue .. 

im STUCK  on this step !!

---

### Post by bugmenot on 2005-10-07
This is pretty retarded. I just installed UT2K4 today and it worked.. for one session.. becasue after I turned my computer on again, and try playing, it just shows the splash screen for a split second and quits.. all I have to say is wow for Linux

---

