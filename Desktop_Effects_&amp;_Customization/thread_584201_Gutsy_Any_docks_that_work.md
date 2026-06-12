---
title: "Gutsy: Any docks that work?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by WoodyXP on 2007-10-20
Hello everybody.. I upgraded to Gutsy a couple days ago and had great success.  My only problem is that I can't get AWN to work with it.  Is it just not compatible?  

Can anyone recommend a good dock to go with Gutsy?  Thank you all.

---

### Post by Quickdood on 2007-10-20
Kibadock which in my opinion is a better dock than awn works perfectly!

---

### Post by LavianoTS386 on 2007-10-20
Add these sources to your sources.list:
> deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

Run the rest in your terminal:
> wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

> sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

And you should be set with AWN

---

### Post by azurelight1337 on 2007-10-20
> **LavianoTS386 said:**
> And you should be set with AWN

alland@allan-desktop:~$ deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
bash: deb: command not found

---

### Post by pieisgood4589 on 2007-10-20
a REALLY easy dock to configure would be a G-Desklets dock. Go to [http://www.gdesklets.de/](http://www.gdesklets.de/) and click on  "get desklets." From there, go to "Toolbars and Launchers" and download Genesis. Restart the comp, (I had to... no idea why) and click on the file with the puzzle pieces all over it, locate genesis, (it should be in the toolbars and launchers section) and double click it. Voila! It's there. To add programs, I believe you click and drag the program while holding control directly into the dock. Good luck! :popcorn:

---

### Post by joshuachad on 2007-10-20
azure the part with the sources are not commands. You have to add those lines to your source.list file.

---

### Post by WoodyXP on 2007-10-21
Awesome.. thanks everybody!  I'm gonna these out when I get some spare time.

---

### Post by noefear on 2007-10-21
I updated my source.list and followed the above directions...all worked well until the last command. (notice below...broken packages).
I dont show AWN in my accessories.

nf@nf-linux:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libwnck18 (>= 2.15.90) but it is not installable
                              Depends: libawn-bzr (= 0.1.2-bzr78-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libawn-bzr but it is not going to be installed
E: Broken packages
nf@nf-linux:~$

---

### Post by breakerr on 2007-10-22
_**[LavianoTS386]("http://ubuntuforums.org/member.php?u=344027")  wrote:**_
[SIZE="1"]
Add these sources to your sources.list:

Quote:
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
Run the rest in your terminal:

Quote:
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

Quote:
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
And you should be set with AWN[/SIZE]
__________________________________________________________
I want a dock that works and so far **AVANT** worked way better while I had Feisty than** kiba-dock** which always got weird black background that I tried to solve with some fixes found on the net and after a while it turned black again. so now I just tried to add that again to my third party repositories list and I got this: 
[B]
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181[/B] what dock manager should I get or how can I fix this ???? so far the desklet for docks is not so cool or stable.

---

### Post by tynen on 2007-10-22
> **WoodyXP said:**
> Hello everybody.. I upgraded to Gutsy a couple days ago and had great success.  My only problem is that I can't get AWN to work with it.  Is it just not compatible?  

Can anyone recommend a good dock to go with Gutsy?  Thank you all.

I was able to get AWN working perfectly in ubuntu 7.10 Maybe you're doing something wrong? But it is possible, I've been using AWN for a couple days now.

---

### Post by Shabbro on 2007-10-22
Hello,
I am a new Ubuntu user (7.10) and I was wondering how to update your sources.list? I have installed software using the terminal  before, but I've yet to update my sources. 

Thanks,

*EDIT* Sorry... with some snooping I found where to configure your sources, and I added those listed.  Thanks*

---

### Post by Mr Greencastle on 2007-10-22
For those having trouble:

Try copying the commands one at a time into the terminal.

PS. If someone could just make a quick script that would be great! I don't need it myself, but it would make life a lot easier for the other people.

Mr Green

---

### Post by Yuzem on 2007-10-23
Here there is a deb>
[http://www.getdeb.net/app.php?name=Avant+Window+Navigator](http://www.getdeb.net/app.php?name=Avant+Window+Navigator)

---

### Post by d3mon on 2007-10-23
I followed LavianoTS386 instructions for AWN installation on Gutsy..the AWN installed without any errors as far as i saw..i get the AWN manager icon under System > Preferences > ( AWN manager ) but when i click it nothing happens..so i am still without the dock.. :confused: anyone with this problem??? should i supposed to do anything else or this installation should work in gutsy??

---

### Post by hopelessone on 2007-10-23
i found out that if you upgrade from 7.04 -> 7.10 it won't work...

a fresh install is needed...

---

### Post by d3mon on 2007-10-23
i didn't upgrade from 7.04...i have fresh install..:(

---

### Post by d3mon on 2007-10-23
one n00b question...how to remove install made with LavianoTS386 instructions??? if i wanna try installing with deb package that Yuzem posted i get this error:

dpkg: regarding .../avant-window-navigator_0.2-1~getdeb1_i386.deb containing avant-window-navigator:
 avant-window-navigator-bzr conflicts with avant-window-navigator
  avant-window-navigator (version 0.2-1¬getdeb1) is to be installed.
dpkg: error processing home/XXX/Desktop/avant-window-navigator_0.2-1~getdeb1_i386.deb (--install):
 conflicting packages - not installing avant-window-navigator

---

### Post by d3mon on 2007-10-23
oh yeah...i am using compiz if this is any help...

---

### Post by hopelessone on 2007-10-23
d3mon - AWN curves worked great !!!

try [http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

HTH..

also try reboot applications >> Accessories>> AWN

worked for me had the same problem...

---

### Post by d3mon on 2007-10-23
:lolflag: man i'm such a fool...this solved my problem.  i didn't try to restart it from apllications...i have only been trying to run awn-menager from system... it works great now. thanks man.

---

### Post by d3mon on 2007-10-23
sorry...one more question... will AWN dock appear always or will i have to run it every time i boot??

---

### Post by breakerr on 2007-10-23
> **d3mon said:**
> sorry...one more question... will AWN dock appear always or will i have to run it every time i boot??

If your looking to have AWN running as soonest you restart or turn on your Pc you just need to add 

**name**:  avant

**command**:   avant-window-navigator

to your _System - Preferences - Sessions - Start Up programs tabs_
_____________________________________________________________________ .. ..
> **hopelessone said:**
> d3mon -[SIZE="1"] AWN curves worked great !!!

try [http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019)

HTH..

also try reboot applications >> Accessories>> AWN

worked for me had the same proble[/SIZE]m...  

RELATED TO GETTING AWN CURVE STYLE I FIND THATS TO MUCH WORK TO ADD A SIMPLE CURVE.

---

### Post by mattgaunt on 2007-10-24
breaker i think your messages doesn't mean u can't install awn - just try the rest of the instructions.

I think your error is just to say that u dont hav a key to identify the server - all its saying is that u install programs from that repo at your own risk

Matt

---

### Post by WoodyXP on 2007-10-25
> **LavianoTS386 said:**
> Add these sources to your sources.list:And you should be set with AWN

Thanks alot, bro.  This worked after I did a fresh install.  I think not uninstalling the Feisty version before upgrading screwed me over.

---

### Post by breakerr on 2007-10-25
> **mattgaunt said:**
> breaker i think your messages doesn't mean u can't install awn - just try the rest of the instructions.

I think your error is just to say that u dont hav a key to identify the server - all its saying is that u install programs from that repo at your own risk

Matt

Thanks a lot for the help man, I already got it...it was just that I was installing the repo for Feisty instead Gutsy.Me stupid :p  THANKS

---

### Post by RavanH on 2007-10-25
Try out the latest release of Cairo Dock! It is absolutely awesome! Light, fast, beautiful and terribly configurable...

Version 1.3.8 out today: [http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

I've even gotten it to run on an AMD64 system with ATI graphics :)

---

### Post by rapsball4 on 2007-10-25
Which would most people here say is overall the best?  I've been trying to get Kiba to work but hitting errors, and I got AWN but wasn't overly impressed - nice, but nothing too special.

Edit:  I had it working in its basic form.  I tried again to get curves and got errors.

---

### Post by breakerr on 2007-10-26
> **RavanH said:**
> Try out the latest release of Cairo Dock! It is absolutely awesome! Light, fast, beautiful and terribly configurable...

Version 1.3.8 out today: [http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

I've even gotten it to run on an AMD64 system with ATI graphics :)

Thanks a lot for the suggestion, Ill try it for sure......

---

### Post by rapsball4 on 2007-10-26
Alright, I'm sick of trying to get kiba to actually work.  Going to try Cairo next at the suggestion, but the first step: where are the installation instructions (from source since I'm running 64-bit)?

---

### Post by santiagoward2000 on 2007-10-26
> **rapsball4 said:**
> Alright, I'm sick of trying to get kiba to actually work.  Going to try Cairo next at the suggestion, but the first step: where are the installation instructions (from source since I'm running 64-bit)?

Hi!
I heard many people complai about getting kiba to work. Maybe I'm just lucky, but I had no problems!
It works great (and doesn't look bad either :KS ) in my Xubuntu Gusty.

---

### Post by breakerr on 2007-10-26
> **santiagoward2000 said:**
> Hi!
I heard many people complai about getting kiba to work. Maybe I'm just lucky, but I had no problems!
It works great (and doesn't look bad either :KS ) in my Xubuntu Gusty.

I must have to say YES....**.kiba-dock** is kinda messy and unreliable/unstable ......Im doing great with **AWN - Avant Window Navigator** no black background and no nothing after upgrading to GUTSY, best wishes with Cairo.

---

### Post by ÜbuntuMensch on 2007-10-26
> **rapsball4 said:**
> Alright, I'm sick of trying to get kiba to actually work.  Going to try Cairo next at the suggestion, but the first step: where are the installation instructions (from source since I'm running 64-bit)?

there is a guide!

Works like a charm, although perhaps that charm is an evil monkey foot. Not sure yet. Install went fine in about 15 minutes. This beats my AWN install by...a lot. It opens, I'm configuring now, btw, I;m running 64 bit with no apparent issues with Cairo-dock.


[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by ÜbuntuMensch on 2007-10-26
Shockingly simple install, looks great, highly configurable: cairo-dock is it.

---

### Post by rapsball4 on 2007-10-27
I can't seem to download the .tar.bz2 - I'm guessing its just down for a bit and I'll have to try later?

---

### Post by mattgaunt on 2007-10-30
I made i guide for kiba-dock

Worth giving it a go if u still want to try and get it to work

[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")

Im currently using awn would people recommend gnome-dock over awn?? what little features does it have that awn doesnt??

Matt

---

### Post by k0rfain on 2007-10-30
[didnt read all the post's]
You can also install kiba-dock from this script: [http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0) (this is the one I used)

or this one: [http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.0)

---

### Post by rapsball4 on 2007-10-30
I didn't end up trying gnome-dock, but after the problems with kiba, the quick and easy install and setup of AWN was pretty good for me.  I'm probably going to stick with it for a while.

---

### Post by RavanH on 2007-11-01
> **ÜbuntuMensch said:**
> there is a guide!

Works like a charm, although perhaps that charm is an evil monkey foot. Not sure yet. Install went fine in about 15 minutes. This beats my AWN install by...a lot. It opens, I'm configuring now, btw, I;m running 64 bit with no apparent issues with Cairo-dock.


[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Ok, for anybody that is on a AMD64 system, in short:

1. Download and install Getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
2. Download and install (with sudo dpkg -i --force-architecture *.deb) the latest cairo-dock 32bit packages (now both cairo-dock and plugins version 1.3.8 ) from [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724) 
3. run getlibs on the cairo-dock installation to solve any dep issues: [http://ubuntuforums.org/showthread.php?p=3683109#post3683109](http://ubuntuforums.org/showthread.php?p=3683109#post3683109)
4. run cairo-dock in terminal to test an if it is to you liking (try some themes and put new launchers on it) then... 
5. put a cairo-dock entry in your Sessions list to make it run automatically at login :)

--ravan

P.S. Any questions about the dock (installation/configuration/theme-writing) can be posted on [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724)

---

