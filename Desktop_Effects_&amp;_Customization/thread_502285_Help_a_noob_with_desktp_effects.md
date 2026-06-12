---
title: "Help a noob with desktp effects"
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by ryudo423 on 2007-07-16
hi im new to linux and finally got my wireless card working after an extreme headache. but now i have a problem with the desktop effects. when i attempt to enable them the screen turns white and all i can see is the mouse. it then reverts back to the regular desktop after 30 seconds or so.. anyone know how i can fix this? any help would be much appreciated. oh yea my graphics card is: ATI MOBILITY RADEON Xpress 200 series...and im dual booting with vista preinstalled on my compaq presario laptop v5000 if that means anything..thanks again

---

### Post by tgoose on 2007-07-16
Not to discourage you, but if you wait till October all of this will (hopefully) be done for you, and work much better.

---

### Post by loserboy on 2007-07-16
I see that peope are gettting Beryl to work with that video card which is similar to the desktop effects program, so I know this can work.... I just can't find the right howto for it... if you want to search try googling or in this forum for something like "ATI Xpress 200 and desktop effects" or "ATI Xpress 200 and Beryl"

---

### Post by loserboy on 2007-07-16
ok I might have found something, go to a terminal and type
```

glxinfo | grep direct
```

then tell me the output

---

### Post by ryudo423 on 2007-07-16
this is all it said 

matt@matt-laptop:~$ glxinfo | grep direct
direct rendering: Yes
matt@matt-laptop:~$

---

### Post by loserboy on 2007-07-16
hmm, ok it's suppose to work if the output is "yes".... lemme see what I can dig up

---

### Post by ryudo423 on 2007-07-16
ok thanks man...

---

### Post by ryudo423 on 2007-07-16
well i think ive managed to install it...ive got the red diamond up top and can open the beryl manager..but how do i use the cube and stuff??

---

### Post by loserboy on 2007-07-16
I haven't used Beryl for a while, there is settings in the beryl manager just right-click the diamond... most effects are off be default if i remember right....just play around with it and let me know how it goes, are you sure it's running? wobbly windows should be on by default

---

### Post by ittiam on 2007-07-16
Make sure your window manager is set to beryl. Then visit this [http://wiki.beryl-project.org/wiki/Desktop_Cube](http://wiki.beryl-project.org/wiki/Desktop_Cube)
On the same page you will see how to enable and view all eye candies.

---

### Post by ryudo423 on 2007-07-16
ok now i right click on the gem and go to "select window manager" its on "Metacity" for default and when i choose beryl my screen blinks a few times b4 becomig normal. again than when i go to do it again.. it still has Metacity ( gnome window manager).. so idk if its not loading or what but please help! thanks

---

### Post by ittiam on 2007-07-16
You have got drivers installed for your video card?
Have you updated your xorg.conf?

Based upon your driver and whether you are using AIGLX/XGL you can find the tutorial here [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by loserboy on 2007-07-16
I don't think you have glx installed, it's the program that in some way controls composite desktops (e.g. beryl/compiz)

---

### Post by ittiam on 2007-07-16
Ok Sorry just saw your post saying direct rendering enabled, so guess you should have your drivers for the card. I think AIGLX comes automatically with ubuntu and you dont need to install it like XGL. that is why i guess many people prefer AIGLX or do they?

---

### Post by loserboy on 2007-07-16
> **ittiam said:**
> Ok Sorry just saw your post saying direct rendering enabled, so guess you should have your drivers for the card. I think AIGLX comes automatically with ubuntu and you dont need to install it like XGL. that is why i guess many people prefer AIGLX or do they?


well I've been doing alot of reading and it seems his card does not like AIGLX so for now the best would be xgl and this seems to be the best guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)
now that ittiam is here I'm sure we'll get this going for you although it might be beryl instead of the regular desktop effects (which is better IMO)

---

### Post by ryudo423 on 2007-07-16
yea ive got my card enabled in the restricted drivers manager....im givin up for a bit if i dont get this soon lol....

---

### Post by ryudo423 on 2007-07-16
ok thanks loserboy ima follow that guide now and keep u guys posted

---

### Post by ittiam on 2007-07-16
I would like to know something, what is the big difference between XGL and AIGLX? And what is the problem in running AIGLX with his video card?

---

### Post by loserboy on 2007-07-16
> **ittiam said:**
> I would like to know something, what is the big difference between XGL and AIGLX? And what is the problem in running AIGLX with his video card?

honestly I have no idea...  my specialty is keyword searches...  see my 700+ posts? after all that I have learned almost nothing except that I can find answers for just about anything without posting....   I'm a human search engine  :(

from what I can tell AIGLX is the prefered method, the problem is that it works on fewer cards so people revert to to the other.... I don't know why it's better, but I do know that you see alot less people posting problems with AIGLX


btw: this is another good howto: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by ryudo423 on 2007-07-16
well i got t about step 9 and when select it rhis is what terminal says:

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by loserboy on 2007-07-16
> **ryudo423 said:**
> well i got t about step 9 and when select it rhis is what terminal says:

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

let the hair pulling out begin.... jk

is this after you did: sudo apt-get install xserver-xgl   and the following steps?

it seems it's still trying to run in AIGLX instead of xgl.

did you get to log into the xgl session?

---

### Post by ryudo423 on 2007-07-16
idk man but im done for  a bit ima try again later tonight maybe...thanx 4 al you help

---

### Post by loserboy on 2007-07-16
k I'll leave you alone, but just so you know, you need to do the alternate method labeled: "Alternate method: Using closed source FGLRX drivers from ATI."  just beneath the steps that you did...you're really close to being done :)

when you are ready, just follow the 3 undo steps they have there and bring your system back to where it was, then follow the alternate I was talking about... my apologies, when I read through the howto I thought it was all one piece I didn't know they had 2 different ones there.

---

