---
title: "Just Got Unbuntu - Compiz?????"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by KudoKid on 2007-12-03
One of the reasons i wanted to get ubuntu was for compiz, however i now have ubuntu, and am clueless on how to get compiz. please help! Thanks tons!

---

### Post by edm1 on 2007-12-03
Thats not a great reason for coming to ubuntu. Anyway, what graphics card do you have? If you dont know, open a terminal and post the result of 

```
lspci
```

---

### Post by daimaru on 2007-12-03
if you have gutsy (ubuntu 7.10) compiz is already installed.
to get desktop effects going

1. install your restricted drivers (hope you have a nvidia or at least ati card) system->admin->restricted driver manger
2. install advanced desktop effects settings (from terminal)
```
sudo apt-get install compizconfig-settings-manager 
```3. go to system->pref->advanced desktop effects settings 
select all the goodies you want.

---

### Post by icechen1 on 2007-12-03
What graphic card are you using?

You can try install [HTML]compizconfig-settings-manager[/HTML] in synaptics in system->administration.

---

### Post by KudoKid on 2007-12-03
Daimaru, Thank you very much, and BTW thats just one reason i switched, the other include that i wanted a more secure open platform OS and heard ubuntu was fantastic. =) thanks!!! I <3 Ubuntu! =D

---

### Post by KudoKid on 2007-12-03
NEW ADDITION TO QUESTION!!!!

How do i see or set the shortcuts for the effects? Thanks again! =)

---

### Post by erfahren on 2007-12-03
> **KudoKid said:**
> One of the reasons i wanted to get ubuntu was for compiz, however i now have ubuntu, and am clueless on how to get compiz. please help! Thanks tons!
ahem...
[Google search - gutsy installing compiz site:ubuntuforums.org](http://www.google.com/search?hl=en&q=gutsy+installing+compiz+site%3Aubuntuforums.org&btnG=Search)

---

### Post by daimaru on 2007-12-03
[@KudoKid]("http://ubuntuforums.org/member.php?u=445997")
i think its perfectly ok to even just switch for the 3d effects. as long as people realize that there are other OS's than windows I'm friggin happy :) 

so to your question about shortcuts. 
you can click any of the effects under "advanced desktop effects settings" 
for example clicking "rotate cube" you get 2 tabs (general and actions) under actions you can expand the triangle thing and see the predefined shortcuts or change them.

some defaults to try:
ctrl+alt+cursor keys left right --> rotates desktop cube
middle mouse button click on desktop also rotes cube
ctrl+alt+left mouse button same thing again (rotate cube)

windows key (super key) + tab does a window shuffles thingi .,. just try and see ( you may have to enable it under the preferences i think it was  "ring switcher" under window management ) 

other cool things are to enable the "put" option under window management then you can use your Numpad keys (1-9) to direct windows into the appropriate corners ( upper left , right center etc ) very usefull. 

hope it helps mate and have fun experimenting.

---

### Post by Therion on 2007-12-03
[Setting Up Compiz Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

---

### Post by erfahren on 2007-12-03
[http://www.google.com/search?hl=en&q=configuring+compiz-fusion&btnG=Google+Search](http://www.google.com/search?hl=en&q=configuring+compiz-fusion&btnG=Google+Search)
[http://www.google.com/search?hl=en&q=compiz-fusion+keyboard+shortcuts&btnG=Search](http://www.google.com/search?hl=en&q=compiz-fusion+keyboard+shortcuts&btnG=Search)

[HOWTO: Functional eyecandy for GNOME with Compiz Fusion](http://ubuntuforums.org/showthread.php?t=491676)

[Getting the Best Help on Linux Forums](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

-- just a reminder
welcome to Ubuntu! have fun! :)

---

### Post by alwiap on 2007-12-03
> **Therion said:**
> [Setting Up Compiz Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

this link is amazing, try doing that, it has another page to customize and configure stuff like the desktop cube.  highly recommended~

---

### Post by Phiber_tek on 2007-12-03
> **daimaru said:**
> if you have gutsy (ubuntu 7.10) compiz is already installed.
to get desktop effects going

1. install your restricted drivers (hope you have a nvidia or at least ati card) system->admin->restricted driver manger
2. install advanced desktop effects settings (from terminal)
```
sudo apt-get install compizconfig-settings-manager 
```3. go to system->pref->advanced desktop effects settings 
select all the goodies you want.

I attempted step 2. But terminal told me that it couldn't find the files or something, I havent gotten the Internet to work on it yet so I guess that could be part of the problem; or do you have to have the liveCD in when you do this; by liveCD I mean the install cd

---

### Post by erfahren on 2007-12-03
> **Phiber_tek said:**
> I attempted step 2. But terminal told me that it couldn't find the files or something, I havent gotten the Internet to work on it yet so I guess that could be part of the problem; or do you have to have the liveCD in when you do this; by liveCD I mean the install cd
yes, you'll need internet connected. sometimes you may get prompted for the CD as well so something doesn't have to be downloaded. (you can ensure that the LiveCD is added as a source in the Software Sources -- (that's the same as the repositories in Synaptic)

Anyway, once you get internet you'll need to enable those. see: [http://ubuntuforums.org/showthread.php?t=630715](http://ubuntuforums.org/showthread.php?t=630715)

---

### Post by Phiber_tek on 2007-12-04
Alright so I'm on Gutsy Gibbon and I tried putting this into terminal:


Code:

sudo apt-get install compizconfig-settings-manager



I also went to:  [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) and tried to use that but when it says for Gutsy-Gibbon users to click the link to install the settings manager it says: "Cannot find Compizconfig settings manager" and it just tells me to press OK and I do and it just closes. So... what should I do?

---

### Post by erfahren on 2007-12-04
you may not have the repository you need enabled. redo your sources.list
see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
(btw: sometimes its difficult to get directly to the section on that wiki. The "How to add extra repositories" is just a little way down in the main contents.)

Anyway, do what it says under the "Manual Method". make sure you do the part where it says to add the key for Mediubuntu.

once you do that do:
```

sudo apt-get update

```
and try getting it again

---

### Post by Phiber_tek on 2007-12-04
lright I'll try this 3rd hour in cad and reply then I'll have to wait until work to do any more on this, thanks for all your patience and help thus far!

---

### Post by Phiber_tek on 2007-12-04
> **erfahren said:**
> you may not have the repository you need enabled. redo your sources.list
see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
(btw: sometimes its difficult to get directly to the section on that wiki. The "How to add extra repositories" is just a little way down in the main contents.)

Anyway, do what it says under the "Manual Method". make sure you do the part where it says to add the key for Mediubuntu.

once you do that do:
```

sudo apt-get update

```
and try getting it again

Alright I think I've got it all now, it's downloading updates and packages as I type, on my desktop right now I found a "cube" although it is just a 2 sided thing that lets me flip (like flipping a piece of paper) but once the downloads finish I'll try again to see if it gets fixed...thanks again!

---

### Post by daimaru on 2007-12-04
@phiber_tek
your 2 sided cube is 2 sided because you have to increase your workspaces to 4 to get a cube that has 4 sides. it is explained in **Therion** 's link.  				 				[I][Setting Up Compiz Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

all you have to do is rightclick your workspaces select preferences and increase the number to from 2 to 4.
[/I]

---

### Post by Phiber_tek on 2007-12-04
Yah I finally figured it out and now its all running beautifully, all I really want now is a good GUI, I've seen alot of Vista-like creations, but I haven't seen any where to get them, also I was looking for a good Dock which I found one of from something called desklets, but I don't like it that much and I'm looking for a nicer looking one...if any of you guys know of either of these I'd really appreciate it, thanks...

---

### Post by daimaru on 2007-12-04
you may want to install the emerald theme manager, which manages the themes used for your vista or other looking windows. When i installed compiz emerald was not available in the repositories, so i downloaded the feisty emerald and emerald-themes from the ubuntu website as a .deb file and installed them. 

maybe there's some better way. if so please someone post it so i can change mine too. :)

EDIT: just found this post by [[IMG]http://ubuntuforums.org/customavatars/avatar925_2.gif[/IMG]]("http://ubuntuforums.org/member.php?u=925")                                                                                     [Ptero-4]("http://ubuntuforums.org/member.php?u=925")

> Maybe you can apply another theme (I don't actually use emerald, I use the gtk decorator which allows me to use metacity themes on compiz-fusion).

i'm going to give this a try, because i always wanted to have my metacity themes used in compiz ( there are way prettier ones than the emerald stuff IMHO ) .

---

### Post by Phiber_tek on 2007-12-04
> **daimaru said:**
> you may want to install the emerald theme manager, which manages the themes used for your vista or other looking windows. When i installed compiz emerald was not available in the repositories, so i downloaded the feisty emerald and emerald-themes from the ubuntu website as a .deb file and installed them. 

maybe there's some better way. if so please someone post it so i can change mine too. :)

EDIT: just found this post by [[IMG]http://ubuntuforums.org/customavatars/avatar925_2.gif[/IMG]]("http://ubuntuforums.org/member.php?u=925")                                                                                     [Ptero-4]("http://ubuntuforums.org/member.php?u=925")



i'm going to give this a try, because i always wanted to have my metacity themes used in compiz ( there are way prettier ones than the emerald stuff IMHO ) .


Is 'the ubuntu website' just the Ubuntu.com? Or is there another because I'm not sure where to go at Ubuntu.com to find the downloads and such for the system...do you have a direct link for it?  Sorry for the trouble and thanks

---

### Post by daimaru on 2007-12-04
[http://archive.ubuntu.com/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb)

EDIT: thats just the themes . you still have to install emerald

```
sudo apt-get install emerald
```

---

### Post by Phiber_tek on 2007-12-04
Sweet thanks, but is emerald part of beryl and if yes I thought that beryl was no longer compatible with 7.10? I don't know I could easily be mistaken but I'm just making sure before I go off destroying something lol...

---

### Post by daimaru on 2007-12-04
> **Phiber_tek said:**
> Sweet thanks, but is emerald part of beryl and if yes I thought that beryl was no longer compatible with 7.10? I don't know I could easily be mistaken but I'm just making sure before I go off destroying something lol...

I use it and it has not broken anything for me, but i m no expert so if someone knows how to get different themes to work with compiz i would like to know how. 
sadly i never tried just applying a different metacity theme to my desktop and see if i still have all the wobblie effects, before i installed emerald. so if you want metacity themes and they work with compiz do that if you really want the emerald stuff like vista looking etc i guess you have to install emerald. 

it did not break anything for me, but as i said i m no expert. give it a try and deinstall if your not happy with it.

---

### Post by Phiber_tek on 2007-12-04
Alright well I've got it installed but how do I install or use one of the themes, when I go to System>Preferences>Emerald Theme Manager, the first screen it shows me has a long list of all the themes, I found the one that I want but all I can do is pick it up and drag it around...So I have no idea what to do with that 'description box' of the theme I want...

---

### Post by PeterJS on 2007-12-04
> **Phiber_tek said:**
> Sweet thanks, but is emerald part of beryl and if yes I thought that beryl was no longer compatible with 7.10? I don't know I could easily be mistaken but I'm just making sure before I go off destroying something lol...

There are 4 programs in the Compiz family. The first one is xcompmgr, it was written by Xorg and is pretty much a glorified demo of using the composite extension. Compiz (the old one) was written based on xcompmgr and it was a big improvement, after a couple of versions beryl branched off to add some really radical features. Beryl added new features and became immensely popular, as was originally planned after beryl got to a stable point and was merged back in to compiz. The new combined compiz and beryl project is actually called Compiz Fusion, but most people call it compiz, because it's shorter, nobody's heard of the old compiz, and the program itself is named compiz.

To answer the question at hand, emerald is one of the components of beryl that got moved in to the new compiz. So emerald is the window decorator for both beryl and (the new) compiz.

---

### Post by daimaru on 2007-12-04
> **Phiber_tek said:**
> Alright well I've got it installed but how do I install or use one of the themes, when I go to System>Preferences>Emerald Theme Manager, the first screen it shows me has a long list of all the themes, I found the one that I want but all I can do is pick it up and drag it around...So I have no idea what to do with that 'description box' of the theme I want...

normally selecting a theme (clicking it) should change the appearance of all your windows to that theme. if not either logout and back in (umm dont really know if that will do anything :) ) or you may have to issue command

```
emerald --replace
```

---

### Post by Phiber_tek on 2007-12-04
I tried both, they didn't work...but, I'm not sure if I did the command properly, once in Terminal: what exactly would be the command I would give...I want to use Fayal in Emerald since that will probably help...

---

### Post by daimaru on 2007-12-04
sry phiber i have no way to reconstruct it now that i have it running, maybe someone else can help. 

but what i do remember from install is that my stuff only worked after i did a reboot. then my emerald themer was running right away, without me having to start it again. 

other thread that i might have used said also execute compiz --replace

no idea if that will help.

---

### Post by Phiber_tek on 2007-12-05
> **daimaru said:**
> sry phiber i have no way to reconstruct it now that i have it running, maybe someone else can help. 

but what i do remember from install is that my stuff only worked after i did a reboot. then my emerald themer was running right away, without me having to start it again. 

other thread that i might have used said also execute compiz --replace

no idea if that will help.

Yup, that worked all I had to do is reboot and it came up beautifully, but is there a way to get the panels to do that? Also do you by chance use a dock? and if so what type and how did you get it?

Thanks!

---

### Post by daimaru on 2007-12-06
what do you mean my getting the panels to do that? the panels are the one on top with the menu and the one on the bottom with the windows and desktop switcher thing. did you mean those? and what should the panels do if you mean those. 

as to dock i guess you mean stuff like kiba dock or avant window navigator right? i use the avant window navigator right now, but quite frankly it looks ok, but it has trouble sometimes hiding behind maximised windows or video, so i'm not sure if i'll keep it. probably going to go back to the normal setup with the panel at the bottom. 

AVN you can get either through the website (but then you have to compile it). compiling didn't work for me i used a .deb file for the avn and the extra plugins or whatever it was called. There's loads of threads here on the forum talking about installing "Avant Window Navigator", so just follow one of them.

---

