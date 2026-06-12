---
title: "How do I get rig of Unity."
date: 2011-10-26
forum: Desktop Environments
---

### Post by shanta on 2011-10-26
Come to the last straw with unity. Faunt colours have changed to the point that it is real hard to read the screen. After searching the Ubuntu site and internal docs I can find no way to change them. 

finding programs is also a bear if you don't remember the actual name of the application.

I want to switch back to the old gnome shell.

I installed gnome shell but the start up screen no longer has a list o installed choices of gui when loging in.

How can I add the choice of GUI at log in or just plain trash out Unity for the a more usable desktop?

gone it seems the good old days of switch GUI's on the run. 

Thanks
Shanta

---

### Post by Hylas de Niall on 2011-10-26
> **shanta said:**
> Come to the last straw with unity. Faunt colours have changed to the point that it is real hard to read the screen. After searching the Ubuntu site and internal docs I can find no way to change them. 

finding programs is also a bear if you don't remember the actual name of the application.
Not sure what's up with your font colours, sorry.

> **shanta said:**
> I want to switch back to the old gnome shell.

I installed gnome shell but the start up screen no longer has a list o installed choices of gui when loging in.

How can I add the choice of GUI at log in or just plain trash out Unity for the a more usable desktop?

gone it seems the good old days of switch GUI's on the run. 

Thanks
Shanta

Click the small 'cog/gear' icon to the right of your name at the log-in screen. All installed DE's will be listed and you can choose which you prefer.
You should have Unity, Unity2D, and if you installed Gnome Shell that will be there too, as well as a couple(?) of fall-back versions of Gnome.
(I'm assuming you're running 11.10)

---

### Post by proxy.qtz on 2011-10-26
If you would prefer KDE, try sudo apt-get install kubuntu-desktop

---

### Post by unyalli on 2011-10-26
Like wise I assume....

sudo passwd root

su -

apt-get install gnome

for gnome.

This unity is worse than windows vista/7. What are they thinking.

---

### Post by unyalli on 2011-10-26
> **Hylas de Niall said:**
> Not sure what's up with your font colours, sorry.



Click the small 'cog/gear' icon to the right of your name at the log-in screen. All installed DE's will be listed and you can choose which you prefer.
You should have Unity, Unity2D, and if you installed Gnome Shell that will be there too, as well as a couple(?) of fall-back versions of Gnome.
(I'm assuming you're running 11.10)

Si I installed gnome and rebooted and clicked the "cog gear" and gnome is not there. What next please, how do I get rid of ubuntu/7 and go back to ubuntu/XP?

Thanks, Jeff

---

### Post by john geary on 2011-10-26
try this it seems to be the normal way to go sudo apt-get install gnome-session-fallback and ALT right CLICK instead of right CLICK.I only had to go to SYSTEM-LOGIN and changed to GNOME Session.HopE this helps

---

### Post by linuxonbute on 2011-10-26
I tried various suggestions to get to running gnome instead of Unity but without success. In the end I started up a terminal and ran synaptic ( had to install it first sudo apt-get install synaptic )

Then i selected everything i could find relating to unity and selected remove completely.

BEFORE i said apply I searched for everything relating to gnome and selected install.
Then i applied it all. Once it was all done I closed synaptic and from the prompt ran 
sudo shutdown -r and it worked. Thank goodness. However there were still some things i didn't like and maybe i will be able to sort them out

---

### Post by unyalli on 2011-10-26
> **john geary said:**
> try this it seems to be the normal way to go sudo apt-get install gnome-session-fallback and ALT right CLICK instead of right CLICK.I only had to go to SYSTEM-LOGIN and changed to GNOME Session.HopE this helps

Hey thanks John, now I have another problem. No idea how to do an alt right click in a vmware esxi console. My ubu machine is a virtual machine. Anyway to do this from terminal?

---

### Post by shanta on 2011-10-26
I installed gdm could not see any changes

checked the gear It showed three gnome s

Gnme
Gnome classic 
Gnome classic with out ani

all took me to the GDM but with no menue

Installed KDM it changed the boot screen  but it showed the same set and no KDE 

It seems that we are not supposed to have choices.

I installed several skins but only one shows in the list in Unity appearances but fortunately it uses different colours so I at least can now read the text.

Still would like to go back to the old menu list that worked well after years of organization.

---

### Post by john geary on 2011-10-26
> **unyalli said:**
> Hey thanks John, now I have another problem. No idea how to do an alt right click in a vmware esxi console. My ubu machine is a virtual machine. Anyway to do this from terminal?

Sorry,I'm also a newbie,I also wanted to change to the old desktop,I searched the forums as I have just got a netbook and am running easypeasy!!!!! (funny name) which works well.Someone will know the answer,good luck.

---

### Post by unyalli on 2011-10-27
looks like the only way is to whack the machine and install 10.04.2 LTS.

---

### Post by socref on 2011-10-27
> **unyalli said:**
> Like wise I assume....

sudo passwd root

su -

apt-get install gnome

for gnome.

This unity is worse than windows vista/7. What are they thinking.

My daughter just updated to 11.10 and is stuck with this Unity. She desperately wants back to the old desktop environment she had. But we cannot find a terminal to try the above suggestion. Where the heck is the terminal? All we can find are a few (huge) icons on the left side of the screen.

Thx for your help. 
socref

---

### Post by socref on 2011-10-27
Sorry, we found the terminal and installed gnome.

Now she can log into a gnome desktop.

Looking for the Synaptic package manager and don't see it. Has that gone away? Sorry, but my experience with Ubuntu was quite some time ago (v 9.04).

We see a GDebi Package Installer, but clicking on that open a box on screen but we're at a loss to understand how to use it to do any installations or uninstalls.

Again, sorry to be asking what must be incredibly basic questions, but this install of 11.10 has really thrown her for a loop. She wants her old Ubuntu back.  

socref

---

### Post by dFlyer on 2011-10-27
> **socref said:**
> Sorry, we found the terminal and installed gnome.

Now she can log into a gnome desktop.

Looking for the Synaptic package manager and don't see it. Has that gone away? Sorry, but I'm not an Ubuntu user.

We see a GDebi Package Installer, but clicking on that open a box on screen but we're at a loss to understand how to use it to do any installations or uninstalls.

Again, sorry to be asking what must be incredibly basic questions, but this install of 11.10 has really thrown her for a loop. She wants her old Ubuntu back.  

socref

No longer install with the default system. open a terminal and run the following commands:

sudo apt-get update
sudo apt-get install synaptic

---

### Post by socref on 2011-10-27
> **dFlyer said:**
> No longer install with the default system. open a terminal and run the following commands:

sudo apt-get update
sudo apt-get install synaptic

Thank you, thank you, thank you!  Having now "found" Synaptic all is still not perfect with the world, but she's no longer in full blown panic. :D

Really appreciate the help.

When she did the upgrade to 11.10 was all of this explained (i.e., gnome not automatically installed; synaptic not automatically installed, etc.)? Did she just miss these crucial bits of information?
Thx
socref

---

### Post by shanta on 2011-10-28
it seems they just what to downgrade our systems synatic is the best for installing. the software centre not easy to use and misses a lot.

as for Unity I have now resorted to high contrast and sometimes to read text I have to high lithe I have also lost the display on the lap top itself and only can use a monitor which the system dose not actually detect.

System has slowed down dramatically.

Still cant see any of the desktop I have installed Ie KDE and Gnome shell. Gnome comes up without any menu. 

Get rid of Unity It caused more problems than it is worth Give us our choice of desktops back. And access to functions to change the display. And Give us a help system that actually tells one how to do it not just a minor rewording of what is in the program.

---

### Post by typhoon_tip on 2011-10-28
> **shanta said:**
> it seems they just what to downgrade our systems synatic is the best for installing. the software centre not easy to use and misses a lot.

as for Unity I have now resorted to high contrast and sometimes to read text I have to high lithe I have also lost the display on the lap top itself and only can use a monitor which the system dose not actually detect.

System has slowed down dramatically.

Still cant see any of the desktop I have installed Ie KDE and Gnome shell. Gnome comes up without any menu. 

Get rid of Unity It caused more problems than it is worth Give us our choice of desktops back. And access to functions to change the display. And Give us a help system that actually tells one how to do it not just a minor rewording of what is in the program.

I think the direction is to create a Desktop experience for normal users. Whether is questionable if ones like Unity or not, it is unquestionable that takes very little skills to take back Synaptic, tweaks, customizations, compiz and so on, but having to deal with a great number of users, I think newest Ubuntu is more in line with the concept "Linux for all" (apart from a few bugs... :P that will be fixed anyway !)

---

### Post by shanta on 2011-10-28
> **typhoon_tip said:**
> I think the direction is to create a Desktop experience for normal users. Whether is questionable if ones like Unity or not, it is unquestionable that takes very little skills to take back Synaptic, tweaks, customizations, compiz and so on, but having to deal with a great number of users, I think newest Ubuntu is more in line with the concept "Linux for all" (apart from a few bugs... :P that will be fixed anyway !)

well Its not easyser for the experiance Linux user therefor how could it posibley eayer for the new bee. 

My problems with Unity are with this upgrade to 10.10 I have lost the video drivers I had installed and working. That is an upgrade error and should not have happened.

Reinstalling them has not given me control of the colour and there is nothing in the help to change the colours. How is this eayier? Newbee or old man. The easy part comes with the fact that newbees don't know what they are missing therefore don’t' know that things were better and easier. 

There is no utility to or information on how to install other desktops nor do they show up on the options list of desktops. Using synaptic or apt-get. The default installer takes so long to work one never even gets to the point of know if it even has any desktops into install. That sucked with stench of Msoft all over it form the day it was introduced.

The only default Desktop that works is unity. Now only unity 2d. 

Gnome comes up with no menu and the ability to add apps to the panel are gone so you can actually use the supposed 'choice'. One must use unity or you don't use Linux.

The only part of Unity that makes sense is the search option for programs you don't use much. The rest use more horsepower don't give me a logical list of programs I use routinely. And so far impossible to customize to readability.

Hard enough on the eyes to want to trash Ubunto and go back to Debian or Red hat. 

So What is needed here is.

Clear instruction on how to get choice back into our desktop options.

one How do users install an alternative desktop and get to it. If the installer will not give us the new desktop in the list how dose one add it.

Two How do we change the appearance of Unity.

As the existing system setup/appearance will not do it and it should. We need an alternative. method of doing so.

three The above solutions and others should be in the help system so we don't have to go to our peers for answers to these vary basic questions.

Now that simpler for all.

---

### Post by kurt18947 on 2011-10-28
> **shanta said:**
> well Its not easyser for the experiance Linux user therefor how could it posibley eayer for the new bee. 

[COLOR=Blue]I wouldn't be surprised if it's easier for a newby.  They don't "know how things are supposed to work" so they just figure it out for themselves[/COLOR]

My problems with Unity are with this upgrade to 10.10 I have lost the video drivers I had installed and working. That is an upgrade error and should not have happened.

Reinstalling them has not given me control of the colour and there is nothing in the help to change the colours. How is this eayier? Newbee or old man. The easy part comes with the fact that newbees don't know what they are missing therefore don’t' know that things were better and easier. 

[COLOR=Blue]Which is why upgrades are oftentimes not a good idea.[/COLOR] [COLOR=Blue]Especially one that makes as many big changes as 10.04 -> 11.10/Gnome 2 -> Gnome 3 have made.  A fresh install may produce fewer problems.[/COLOR]

There is no utility to or information on how to install other desktops nor do they show up on the options list of desktops. Using synaptic or apt-get. The default installer takes so long to work one never even gets to the point of know if it even has any desktops into install. That sucked with stench of Msoft all over it form the day it was introduced.

The only default Desktop that works is unity. Now only unity 2d. 

Gnome comes up with no menu and the ability to add apps to the panel are gone so you can actually use the supposed 'choice'. One must use unity or you don't use Linux.

The only part of Unity that makes sense is the search option for programs you don't use much. The rest use more horsepower don't give me a logical list of programs I use routinely. And so far impossible to customize to readability.

Hard enough on the eyes to want to trash Ubunto and go back to Debian or Red hat. 

So What is needed here is.

Clear instruction on how to get choice back into our desktop options.

one How do users install an alternative desktop and get to it. If the installer will not give us the new desktop in the list how dose one add it.

Two How do we change the appearance of Unity.

As the existing system setup/appearance will not do it and it should. We need an alternative. method of doing so.

three The above solutions and others should be in the help system so we don't have to go to our peers for answers to these vary basic questions.

Now that simpler for all.
[COLOR=Blue]
There aren't many easily found materials that document the new interfaces that I know of. I always keep one functioning installation and anything new goes on a LiveCD or LiveUSB.  If hardware works and  I'm generally happy I install the new O.S. in its own partition.  That way I have a normally functioning system to do what I want or need to do while I become familiar with the new software.  I'd also recommend checking out Xubuntu or Lubuntu.  Those interfaces are more "traditional", panels & menus and less demanding of hardware.  I installed Xfce-desktop from the repos along with gnome-shell and gnome-session-fallback.  Xfce4 should feel pretty familiar to Gnome 2 users and by installing onto Ubuntu you keep the Gnome apps like Libre Office.  Xubuntu installs Abi Word, I think Gnumeric and other lighter less familiar apps.  [/COLOR]  

[COLOR=Blue]There are choices.  I hope you can find one that works for you.[/COLOR]

---

### Post by shanta on 2011-10-28
A new bee will just think that it is the way it is supposed to be and not do anything.

Also they are not the normal user. We are the ones that have been supporting Linux for years. If we can't make it work for us how is a new user.

They will not even be able to change a font colour!!! In fact they will not even consider that they could. There fore for the help writers there is no need for instructions so yes support is easier.

so to figure it out for them selves I don't buy it.

Also why has the ability to change managers be dropped?

Why Is there no menu in Gnome only in Unity?

all in all this upgrade has been the worst for Linux users since I started with Debian back when I left windows 98 way back when oh ya that would be 1998.

Over the last few years Ubuntu has been adopting the Ford adage 'You can have any colour you want as long as it is black"!

I am going to open 2 new threads

One for getting our choice in desktops back!

Add one for fixing the colours in Unity!

This one has dropped to newbees are the normal users and the old users are not welcome.

---

