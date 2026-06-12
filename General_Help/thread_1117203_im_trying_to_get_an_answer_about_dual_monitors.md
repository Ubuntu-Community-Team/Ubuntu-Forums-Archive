---
title: "im trying to get an answer about dual monitors"
date: 2009-04-05
forum: General Help
---

### Post by parkadodge on 2009-04-05
ive posted this everywhere and cant seem to find an answer. im trying to a different monitor and keyboard than the one on my laptop in other words im trying to run my laptop as a pc with a larger screen and whatnot. the backlight is out on the laptop witch initiated this mission. i dont care if the screen on the laptop works cuz it doesnt anyway i have the new monitor all hooked up and ready to go but it says no signal how can i use the other monitor. i really need a reply ive got the screen on the laptop working with two lamps behind the screen witch reminds me of calling batman with the light its really annoying please help

---

### Post by The_R on 2009-04-05
I'm having a similar problem. I have the nVidia GeForce 8800 GTX with two monitors attached (actually a Samsung HDTV and a clunky old CRT with an adapter). When I activate the proprietary driver, only one monitor works at a time. If I deactivate the driver, both monitors work, but the awesomeness of my video card is unutilized.
Is there any way to get both screens to work with the accelerated graphics drivers? I don't care if it's mirrored or extended desktop style.

---

### Post by parkadodge on 2009-04-05
well how did you get that far man ive been trying to get the nvidia using the command line and something in my code is wrong id love to just have one of my screens working i just want it to be the external one. im really green to linux and havent the foggiest idea of what to do. im using an ibm thinkpad g40, ubuntu 8.10 the monitor im trying to attatch is some cheapy envision ive never heard of it either haha. so can you give me a step by step to get where you are?

---

### Post by |Porsche on 2009-04-05
> **The_R said:**
> I'm having a similar problem. I have the nVidia GeForce 8800 GTX with two monitors attached (actually a Samsung HDTV and a clunky old CRT with an adapter). When I activate the proprietary driver, only one monitor works at a time. If I deactivate the driver, both monitors work, but the awesomeness of my video card is unutilized.
Is there any way to get both screens to work with the accelerated graphics drivers? I don't care if it's mirrored or extended desktop style.

Hey man, what driver are you using? I have no problems with 180.44. I have same video card.

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> well how did you get that far man ive been trying to get the nvidia using the command line and something in my code is wrong id love to just have one of my screens working i just want it to be the external one. im really green to linux and havent the foggiest idea of what to do. im using an ibm thinkpad g40, ubuntu 8.10 the monitor im trying to attatch is some cheapy envision ive never heard of it either haha. so can you give me a step by step to get where you are?

You should go here and download the drivers from nvidia. They have pretty good isntructions. [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by The_R on 2009-04-05
I'm not exactly an expert on ubuntu myself, but you might try activating/deactivating the proprietary driver.
Go to System/Administration/Hardware Drivers and change the setting on one of the drivers (if it's activated, deactivate it or vice versa).
For my set up, if I want to switch screens with the driver activated, I have to disconnect the one I don't want and connect the one I do want. I don't know how you could do that with your laptop. Is there a button on your keyboard that allows you to switch between monitors? It would be like a little picture of a computer.

---

### Post by parkadodge on 2009-04-05
so as i said before haha i suck. i went to the site you gave me and found the exact thing you have and downloaded it. it now sits in my download box i cant double click it it does nothing sorry still trying not to think as a windows user then it told me to type "sh NVIDIA-Linux-x86-180.44-pkg1.run" im assuming in the the terminal i did that and nothing happens either it just says "cant run sh NVIDIA-Linux-x86-180.44-pkg1.run"

---

### Post by parkadodge on 2009-04-05
went through the drivers and it says i have no proprietary drivers i also dont have a picture of a computer this thing is old.

---

### Post by |Porsche on 2009-04-05
ok remember where you downloaded the file to. 
Press Ctrl+Alt+F1 and this should take you to the terminal. 
type ```
/etc/init.dgdm stop
``` to stop the X server.
run the file that you download it by typing ```
sh <filepath/filename>
```
Read the screen and answer the questions accordingly.
When you are done type
```
/etc/init.d/gdm start
``` to start the X server back up.
That should take you to the login window.

Let me know how it goes.

---

### Post by The_R on 2009-04-05
Try looking for the drivers in the synaptic package manager. I just typed nvidia and a bunch of stuff came up. Do you know what kind of video card your laptop has?

System/Adminitration/Synaptic Package Manager
All you have to do is right click on an item and select "Mark for installation." If the box is green, then it is already installed.

---

### Post by parkadodge on 2009-04-05
first off how do i know where i downloaded it to. second alt f1 doesnt do a thing 3rd when i do bring up the terminal and type the first thing you said starting /etc it says no such file or directory

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> first off how do i know where i downloaded it to. second alt f1 doesnt do a thing 3rd when i do bring up the terminal and type the first thing you said starting /etc it says no such file or directory

Are you using Ubuntu?

---

### Post by stim on 2009-04-05
@The_R

activate the proprietary drivers, or install from the .sh script, then do this:

open a terminal and type
```
sudo nvidia-settings
```

you will be prompted for your password, enter it.  then you will be presented with a window titled "NVIDIA X Server Settings"

under the second section "X server display configuration" you will see your monitors, one is probably grayed out, so you will need to click on it

there is an options screen that comes up, which should allow you to select from 3 radio buttons 

-Disabled
-Seperate X screen (Requires X restart)
-Twinview <-- probably the one you want

After enabling the previously disabled screen you will be able to change color options, position etc

Alt-f1 doesnt take me to the terminal either.
You can find it under applications -> accessories.

---

### Post by The_R on 2009-04-05
> **stim said:**
> @The_R

activate the proprietary drivers, or install from the .sh script, then do this:

open a terminal and type
```
sudo nvidia-settings
```

you will be prompted for your password, enter it.  then you will be presented with a window titled "NVIDIA X Server Settings"

under the second section "X server display configuration" you will see your monitors, one is probably grayed out, so you will need to click on it

there is an options screen that comes up, which should allow you to select from 3 radio buttons 

-Disabled
-Seperate X screen (Requires X restart)
-Twinview <-- probably the one you want

After enabling the previously disabled screen you will be able to change color options, position etc

That did it! Thanks.
This is so much better than MicroSodoff tech support.

---

### Post by parkadodge on 2009-04-05
i just got this computer from my dad ive had it about two months but hes had it for years i asked him if he knew the video card and he doesnt so its what ever came with it out of the box

---

### Post by parkadodge on 2009-04-05
to the above two replys first its saved on my desktop 2nd alt f1 didnt work and when i did open the command line and type /etc/whatever you said above is says no such file or directory and last i havent got a clue what video card im using just whatever came out of the box when my dad bought this oh so many years ago

---

### Post by parkadodge on 2009-04-05
sorry bout last reply i didnt see the others. yes im using ubuntu8.10

---

### Post by parkadodge on 2009-04-05
sorry about all this guys it would be easier to do all this with a backlight but then i guess i wouldnt need to. Stim told me to activate the proprietary drivers or install in .sh i cant figure out how to do either

---

### Post by |Porsche on 2009-04-05
I aplogize, its not Alt+F1 its Ctrl+Alt+F1. Sometimes I have to do it twice for the terminal to come up.

---

### Post by parkadodge on 2009-04-05
okay i got cntrl alt f1 to work and come up you said to type sh filepath/filename i dont know what to put there i can tell you what im being told is to type sh NVIDIA-Linux-x86.180.44.pkg1.run does that seem right

---

### Post by parkadodge on 2009-04-05
never mind the last thing i said i fanally can see im using the net on my phone. ok so when i hit thos three buttons a big black screen comes up and asks me to login. so i do then i type /etc/init.dgdm stop as directed and it says no such file or directory now that i can see what im doing i should get a better grasp

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> never mind the last thing i said i fanally can see im using the net on my phone. ok so when i hit thos three buttons a big black screen comes up and asks me to login. so i do then i type /etc/init.dgdm stop as directed and it says no such file or directory now that i can see what im doing i should get a better grasp]
Login with your username and password then  you fill go to the shell. You type the commands in the shell after you have sucesfully logged in. Oh and you have to be root to do those commands.

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> okay i got cntrl alt f1 to work and come up you said to type sh filepath/filename i dont know what to put there i can tell you what im being told is to type sh NVIDIA-Linux-x86.180.44.pkg1.run does that seem right

That is right, IF you download NVIDIA-Linux-x86.180.44.pkg1.run to your home. A quick way to determine this is to do a ```
ls ~ | grep NV
```
If that commands returns something that includes NVIDIA-Linux-x86.180.44.pkg1.run then you are in luck.

---

### Post by parkadodge on 2009-04-05
so just check my steps cuz im missing big peices.
step 1 download nvidia (using the link on page 1 of replies)
step 2 hit cntrl alt f1
step 3 when black screen comes up login (yes i am root)
step 4 type sh NVIDIA-Linux-x86-180.44-pkg1.run

so when doing these things in that order it says file not found it wasnt downloaded to home it was to my desktop if i could just get a hey dummy watch thatd be cool cuz ive got nothing

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> so just check my steps cuz im missing big peices.
step 1 download nvidia (using the link on page 1 of replies)
step 2 hit cntrl alt f1
step 3 when black screen comes up login (yes i am root)
step 4 type sh NVIDIA-Linux-x86-180.44-pkg1.run

so when doing these things in that order it says file not found it wasnt downloaded to home it was to my desktop if i could just get a hey dummy watch thatd be cool cuz ive got nothing

step3.5 sudo /etc/init.d/gdm stop

if your drivers are in desktop then type```
 sh /home/YOURUSERNAME/Desktop/NVIDIA-Linux-x86-180.44-pkg1.run

```
dont forget to change YOURUSERNAME to your real pc  username.

---

### Post by parkadodge on 2009-04-05
well that was bad *** but it gave me two warnings first was that it appears i dont have NVIDIA GPU??? then it also says i need to exit x. i at least know what that means just not how to do it

---

### Post by parkadodge on 2009-04-05
yay its installing once i get it done its compiling a kernal now. then what do i do to get the new screen as default and whatnot

---

### Post by parkadodge on 2009-04-05
failure to install it said unable to load kernal module 'nvidia.ko'

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> well that was bad *** but it gave me two warnings first was that it appears i dont have NVIDIA GPU??? then it also says i need to exit x. i at least know what that means just not how to do it

That is what sudo /etc/init.d/gdm stop does.

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> well that was bad *** but it gave me two warnings first was that it appears i dont have NVIDIA GPU??? then it also says i need to exit x. i at least know what that means just not how to do it

```
sudo apt-get install nvidia-settings
```
To configure your card.

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> well that was bad *** but it gave me two warnings first was that it appears i dont have NVIDIA GPU??? then it also says i need to exit x. i at least know what that means just not how to do it

post the output of the following command:
```

lspci
```

---

### Post by parkadodge on 2009-04-05
what do you mean by output

---

### Post by sailthesea on 2009-04-05
post the output of the following command:
Code:

lspci


Run that in terminal and and paste the results in your next post
 You are almost done All you need are you config settings

---

### Post by parkadodge on 2009-04-05
syntax error near unexpected token '('

---

### Post by sailthesea on 2009-04-05
Oh C@:{ Your still running in the Kernel 
 You should very careful! And make sure you have a clean shutdown;)

---

### Post by parkadodge on 2009-04-05
ok im so im shutting down now. so where do i need to run this im sorry im not sure if youve read all the way up but im really new to this and i can bareley see my screen i really just need steps in as plane of english as possible the jump to linux is still screwin with my mind i know it shouldnt cuz this is by far easier when you understand but i dont

---

### Post by parkadodge on 2009-04-05
i had a clean shut down and all is good. as far as i know these are my steps

step 1.  download        CHECK
step 2.  hit cntrl alt f1       CHECK
step 3.  login               CHECK
step 4.  exit x by hitting sudo /etc/init.d/gdm stop         CHECK
step 5.  install by hitting sudo sh /home/username/Desktop/NVIDIA-Linux-x86-180.44-pkg1.run            NOT CHECK (where and how do i put in the input for lspci)

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> i had a clean shut down and all is good. as far as i know these are my steps

step 1.  download        CHECK
step 2.  hit cntrl alt f1       CHECK
step 3.  login               CHECK
step 4.  exit x by hitting sudo /etc/init.d/gdm stop         CHECK
step 5.  install by hitting sudo sh /home/username/Desktop/NVIDIA-Linux-x86-180.44-pkg1.run            NOT CHECK (where and how do i put in the input for lspci)

No...the output of lspci is just to see if the system is recognizing your video card. You said that you were getting a message about your card not being an nvidia GPU. The lspci has nothing to do with that.

---

### Post by parkadodge on 2009-04-05
then what do i need to look for in lspci its a big bunch of confusion

---

### Post by parkadodge on 2009-04-05
can i copy paste so you can see what im looking at

---

### Post by |Porsche on 2009-04-05
> **parkadodge said:**
> can i copy paste so you can see what im looking at

Yes that is what I mean by pasting the output of the command.

---

### Post by parkadodge on 2009-04-05
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5901 100Base-TX (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)

---

### Post by parkadodge on 2009-04-05
yes i understand i have a crappy computer before you start laughing at me. its just a way to learn linux in the safest way if i blow this thing up im out 10 dollars

---

### Post by |Porsche on 2009-04-05
I dont see a nvidia card. Are you sure you have one?

---

### Post by parkadodge on 2009-04-05
no thats the problem it wont install because of it hold on and ill post the exact warning

---

### Post by parkadodge on 2009-04-05
WARNING: You do not appear to have an NVIDIA GPU supported by the 180.44 NVIDIA Linux graphics dirber installed in this system. for further details please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the read me available on the linux driver download page at [www.nvidia.com](www.nvidia.com)
now it does let me continue but i fail at the next spot

---

### Post by parkadodge on 2009-04-05
after i read that message i can still continue agree to the license then this pops up

No precompiled kernal interface was found to match your kernal; would you like the installer to attempt to download a kernal interface for your kernal from the NVIDIA ftp site ([ftp://download.nvidia.com](ftp://download.nvidia.com))

naturally i hit yes and this comes up

no matching precompiled kernal interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernal interface for your computer

and again hit ok the get this

building kernal module with a bar and it goes to 100% i think great and get this

Error: unable to load the kernal module 'nvidia.ko'. this happens most frequently when this kernal module was built with a version of gcc that differs from theone used to build the target krnal, or if a driver such as rivafb/nvidiafb is present and prebents the NVIDIA graghics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux grapghics driver release.

i hit ok

Please see the log entries rivafb/nvidiafb for details you may find suggestions on fixing installation problems in the README available on the linux driver download page at [www.nvidia.com](www.nvidia.com)

---

### Post by |Porsche on 2009-04-05
from looking at the output of lspci it doesnt appear you have nvidia card, or if you do the system is not recognizing it. You can make sure it is there, and or reseat it.

---

### Post by parkadodge on 2009-04-06
thanx for all your help i think im just going to deal with the see threw screen i understand why it wasnt working but not how to fix it. you were right i dont have an nvidia gpu as a matter of fact i cant figure out what kind of card it has there is no info any where. ive looked in the ibm thinkpad g40 manual and cant find it there either.

---

### Post by |Porsche on 2009-04-06
> **parkadodge said:**
> thanx for all your help i think im just going to deal with the see threw screen i understand why it wasnt working but not how to fix it. you were right i dont have an nvidia gpu as a matter of fact i cant figure out what kind of card it has there is no info any where. ive looked in the ibm thinkpad g40 manual and cant find it there either.

From your lspci output you have this video card
[http://www.intel.com/support/graphics/intel852gm/](http://www.intel.com/support/graphics/intel852gm/)

---

### Post by parkadodge on 2009-04-06
and using that can i get the dual screen there has to be a way i know it works with windows without any configuration so there has to be way using linux

---

### Post by |Porsche on 2009-04-06
Hey have you tried to go to Main Menu/System/Preferences/Screen Resolution

?

---

### Post by parkadodge on 2009-04-06
no i hadnt but just did and it says laptop 15inch my options are i can flip screen upside down but thats about it i hit detect display and nothing happens same with show displays in panel but i figure they dont mean what they sound like they do

---

### Post by |Porsche on 2009-04-06
Is your other monitor ON and plugged in?

---

### Post by parkadodge on 2009-04-06
haha i knew thatd be the next question and yea

---

### Post by parkadodge on 2009-04-06
and they are connected blue to blue

---

### Post by |Porsche on 2009-04-06
I am out of ideas.

---

