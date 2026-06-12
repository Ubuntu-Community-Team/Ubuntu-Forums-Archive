---
title: "Installing beryl on a Dell Dimension 2350"
date: 2009-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abansb on 2009-07-08
Hello 

I am new to the Linux world I am trying to install beryl on my Dell Dimension 2350 with the Integrated 82845g/gl Graphic controller I have searched and searched everything I try does not work. I am running Ubuntu 9.0.4 tried the newest version but could not get this fixed..

Here is what I am wanting to do wobbly windows, desktop cube I have also tried to turn on visual effects at first it said that it could not be enabled but now when I click it just shows the pointer and background seems to freeze up on me.   I have Compizconfig settings manager installed not for sure what else was needed to get this to work on this graphics controller if anyone could help me solve this problem it would be so appreciated very much I have seen videos on these effects and would love to have them on my linux machine..

Thanks to who ever can help to solve this or help me get this working..

abansb

---

### Post by abansb on 2009-07-08
Anyone ????? I have tried everything please someone help or give me a link to where I can find help 

Thanks 
abansb

---

### Post by andrea000 on 2009-07-08
your wanting compiz run compiz in the terminal
and post the output on here.
applications->accessories->terminal
command
compiz
Do you have hardware drivers installed?
systems>administration>hardware drivers

---

### Post by jualin on 2009-07-09
If when you run "compiz" on the command line gives you errors you may want to try this command instead > SKIP_CHECKS=yes compiz However, if compiz refuses to work is probably because the video card driver is unstable when compiz runs or because the video card driver has not been installed correctly. Good luck!

---

### Post by abansb on 2009-07-09
when I run compiz all I get is a mouse pointer and background image and it seems to hang there i have to cold boot to get it back 

I am not for sure I have the right video drivers I have the Intel Integrated 82845g/gl Graphics Controller.

When I go to systems>administration>hardware drivers there is nothing listed in there.

I have also tried SKIP_CHECKS=yes compiz 			 		still noting

I guess I am doing something wrong I don't know 

But Thanks for the replies and trying to help

---

### Post by andrea000 on 2009-07-09
just do the check it will tell you if it is blacklisted and
it's easy fix to unblacklist it you cant run compiz anyway.
no harm done one way or the other.your decision if you do
or not.most of the time you would skip check but you need
to know what the problem is.you have to have a driver you
just don't have a proprietary driver that compiz needs to
run.

---

### Post by abansb on 2009-07-09
I am not sure how or where to get these drivers from

 I ran the command compiz this is what I got back  

xxxxxx@xxxxxx-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/xfwm 
no /usr/bin/xfwm found, exiting


What else do I need to do?

---

### Post by andrea000 on 2009-07-09
> **abansb said:**
> I am not sure how or where to get these drivers from

 I ran the command compiz this is what I got back  

xxxxxx@xxxxxx-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/xfwm 
no /usr/bin/xfwm found, exiting


What else do I need to do?
your card is blacklisted that what i was thinking ok no
problem there 

Edit the compiz script file in the terminal

sudo gedit /usr/bin/compiz

Then go down and look for blacklist, then add the # to take your intel graphic out of the blacklist.

Then the script should look like this

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T=” 1002:5954 1002:5854 1002:5955&#8243; # ati rs480
#T=”$T 1002:4153&#8243; # ATI Rv350
#T=”$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12&#8243; # intel 965
#T=”$T 8086:2a02 ” # Intel GM965
#T=”$T 8086:3577 8086:2562 ” # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS=”$T”
unset T

Save, then restart
After reboot, go to System > Preferences > Appearance >Visual Effects
then tick on the middle or the last option.

---

### Post by theozzlives on 2009-07-09
I have a Dell Optiplex with the same chip. Worked fine in 8.04, had to tweak my xorg.conf in 8.10, had to buy a Nvidia card for 9.04.

EDIT: Bypassing the Blacklist don't work with that chip.

---

### Post by andrea000 on 2009-07-09
> **theozzlives said:**
> I have a Dell Optiplex with the same chip. Worked fine in 8.04, had to tweak my xorg.conf in 8.10, had to buy a Nvidia card for 9.04.

Hi just a quick question do you really get free
ubuntu stickers from the link in your signature
that is so cool.Have you got any from them?

---

### Post by abansb on 2009-07-09
> **andrea000 said:**
> your card is blacklisted that what i was thinking ok no
problem there 

Edit the compiz script file in the terminal

sudo gedit /usr/bin/compiz

Then go down and look for blacklist, then add the # to take your intel graphic out of the blacklist.

Then the script should look like this

# blacklist based on the pci ids
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T=” 1002:5954 1002:5854 1002:5955&#8243; # ati rs480
#T=”$T 1002:4153&#8243; # ATI Rv350
#T=”$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12&#8243; # intel 965
#T=”$T 8086:2a02 ” # Intel GM965
#T=”$T 8086:3577 8086:2562 ” # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS=”$T”
unset T

Save, then restart
After reboot, go to System > Preferences > Appearance >Visual Effects
then tick on the middle or the last option.

OK I did this and now all my panels are gone the top and the bottom when I rebooted my panels flickered then went away how can I get them back ?

Thanks

---

### Post by theozzlives on 2009-07-09
> **andrea000 said:**
> Hi just a quick question do you really get free
ubuntu stickers from the link in your signature
that is so cool.Have you got any from them?

yes 8 of them.

---

### Post by andrea000 on 2009-07-09
> **abansb said:**
> OK I did this and now all my panels are gone the top and the bottom when I rebooted my panels flickered then went away how can I get them back ?

Thanks

should not have done anything to your panals.Can you get
to the terminal?if so do a sudo synaptic and find ubuntu
desktop right click it and mark for installation or mark
for reinstallation if it is checked and reboot

---

### Post by abansb on 2009-07-09
I am using Xubuntu would that make a difference?

---

### Post by andrea000 on 2009-07-09
> **abansb said:**
> I am using Xubuntu would that make a difference?

i have never used Xubuntu before but it shouldn't
it is just a different interface still ubuntu linux
i just don't know if it would or not

---

### Post by andrea000 on 2009-07-09
go to the terminal if you can and do a sudo synaptic
and find your desktop

---

### Post by theozzlives on 2009-07-09
I TOLD you it won't work, now you're left with wallpaper and a cursor. If you want compiz to work with that card you gotta go 8.04!

---

### Post by abansb on 2009-07-09
Got them back after I reinstalled Xubuntu

Thank you

---

### Post by andrea000 on 2009-07-09
well it worked on mine

---

### Post by abansb on 2009-07-09
> **theozzlives said:**
> I TOLD you it won't work, now you're left with wallpaper and a cursor. If you want compiz to work with that card you gotta go 8.04!

So I will have to have to downgrade to 8.0.4 to get this to work

I really don't want to downgrade I think i will try to get this working on 9.0.4 if it don't work it don't work

---

### Post by andrea000 on 2009-07-09
is compiz working?

---

### Post by abansb on 2009-07-09
I can't find where to turn on the visual effects in Xubuntu

Edit: I think I found it

---

### Post by andrea000 on 2009-07-09
in ubuntu you just right click the desktop and change
desktop background then it's the last tab

---

### Post by abansb on 2009-07-09
I tried setting to wobbly windows but it isn't working 

Do I need try anything else to see if it is working?

---

### Post by theozzlives on 2009-07-09
> **abansb said:**
> So I will have to have to downgrade to 8.0.4 to get this to work

I really don't want to downgrade I think i will try to get this working on 9.0.4 if it don't work it don't work

I tried for weeks to get it to work, not to mention several threads here. I finally broke down and bought an old Nvidia 6000 series for about $30.00 incl. shipping off e-bay. Works great now.

---

### Post by andrea000 on 2009-07-09
did it take your visual effects setting?it should be working
if it didn't you may have to downgrade it worked on mine

---

### Post by abansb on 2009-07-09
It saved the setting but it's not working
[U][U]
[/U][/U]theozzlives to downgrade do I need to download **Ubuntu 8.04 LTS Desktop? I mean to get this to wor[B]k**
[/B]

---

### Post by andrea000 on 2009-07-09
go and do a sudo gedit /usr/bin/compiz and copy
the blacklisted based on pci and post it here
may be something in there you missed but i don't
think so and don't save anything when you exit it

---

### Post by andrea000 on 2009-07-09
best to go and download 8.04

---

### Post by abansb on 2009-07-09
Here is the sudo gedit /usr/bin/compiz

> # blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

---

### Post by andrea000 on 2009-07-09
ok here is what mine looks light

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2e02 " # Intel Eaglelake
**T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"
unset T

find your card and take the # out like mine in
the bold that may work

---

### Post by abansb on 2009-07-09
I tried that still not working 

Thanks again for trying to help me

---

### Post by andrea000 on 2009-07-09
I guess the only option at this point is downgrading
sorry it didn't work

---

### Post by abansb on 2009-07-09
We tried no big deal I will downgrade and try if I don't like the 8.0.4 I will just reinstall 9.0.4 I tried 9.10 it would not work at all either 

I am downloading the 8.0.4 now to test it 

I seen a video on the visual effects and thought it was cool the wobbly windows the desktop cube 

And Thanks again for your help

---

### Post by jualin on 2009-07-09
The last thing that I would try before installing 8.04 is trying the "proposed" intel drivers for your card. Go to Synaptic Package Manager and then enable the "proposed updates" repositories by going to "Settings" and then "Repositories". After this, reload the repositories and try installing the "xserver-xorg-video-intel" package. Then try running Compiz again with the Skip Checks command. Good luck!

---

### Post by abansb on 2009-07-09
Ok I checked synaptic Package manager and the xserver-xorg-video-intel is alreasy installed and when I do a search for just xserver-xorg-video there is a bunch installed s3, vesa, actually a buch I am not going to type them all here but do you think maybe they are conflicting with the Intel Drivers? looks like about 20 or so installed 


Again I want to thank all that is trying to help like I said I am new to linux I really love using linux I had used Windows for like 16 years or so this is a challenge for me

---

### Post by abansb on 2009-07-10
Ok I tried the drivers but did not work so I install ubuntu 8.0.4 and it is working

Ok now I have another problem I can't change the resolution when I try to change it the screen goes black and have to reboot to get it back

Also I noticed that my second hard drive is not showing up how can I access it or get it to show?


Thanks

---

### Post by abansb on 2009-07-10
I got the wobbly windows to work and the desktop cube but there us no sphere 

still can't find my other hard drive any help thanks

Edit: I finally got my hard drive to show up I used this sudo apt-get install pysdm just in case any one else has the same problem to run it sudo pysdm it will auto configure it to show up on boot

---

### Post by jualin on 2009-07-11
Glad to hear that everything worked out. Please mark your thread as solved.

---

### Post by abansb on 2009-07-11
how do I mark it solved ?

---

### Post by abansb on 2009-07-12
I am having another problem I went to reboot after installing 8.0.4 with compiz and all my windows have shifted to the top with no way to minimize, close or move all other windows are stuck to right side with no way of doing the same I removed compiz and reinstalled xubuntu thinking that was it anyone know how to correct this problem?


Thank you

---

### Post by abansb on 2009-07-12
I have searched and founds nothing how to fix this I was hoping to find a solution before reinstalling 8.04

---

### Post by abansb on 2009-07-13
Just wanted to update on what I have done 

I installed the compiz fusion icon and every once in awhile I have to change compiz option and turn loose bindings on then off to get things to work right as of right now the only thing that the top of the window is under my top panel is the terminal everything else works fine I can deal with have to change these settings every once in awhile

---

