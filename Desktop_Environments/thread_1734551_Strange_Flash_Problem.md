---
title: "Strange Flash Problem"
date: 2011-04-20
forum: Desktop Environments
---

### Post by arafu on 2011-04-20
Hi I am a new user of Ubuntu..so far it has been really great, using this OS. As a new user...I was browsing through synaptic manager & found many flash related installers, like flash alternative, flash extras etc..with a huge interest I installed some of them.. I had no problem playing flash in youtube n etc. before installing them. But after installing those, no matter how I tried I could not make my flash work. It is always saying "Adobe Flash has crashed"

Recently I have discovered another thing, if I keep the ZSNES Emulator running & browse through Youtube-like websites..My flash is working so perfectly..

Please somebody help me..I believe there's a workaround of my situation..I cant figure out what I did or what I should do.I don't want to run ZSNES emulator every time before visiting youtube. :( 

Thanks in advance =)

---

### Post by Frogs Hair on 2011-04-20
Hi and Welcome 

Could you tell us what version of Ubuntu  you are using and find out the exact name of the packages you installed . I can't seem to find those packages in Ubuntu 10.10 .

---

### Post by arafu on 2011-04-21
ok..i am using Ubuntu Desktop 10.10...& I am not exactly sure of all the packages i have installed... I can remember these tho : 

1. flashplugin-nonfree

2. flashplugin-installer

3. flashplugin-nonfree-extrasound

4. Gnash

5. i cant exactly remember how i got but i have found an Flash plugin in my home folder named..flash-alternative.so

I think if i could completely remove everything related to flash..i may fix my PC :) btw thanks for ur help :D I really love ubuntu community..very active

---

### Post by Frogs Hair on 2011-04-21
Open the Synaptic Package Manager , right click and mark the last three for complete removal . Gnash is an open source flash player and you don't need it if you are already have Adobe installed unless you prefer to use it instead of Adobe. The third package you have listed , I am unable to find in 10.10. Be sure you have the name correct on the third plug-in because I don't want you to remove something you need.

---

### Post by arafu on 2011-04-21
here comes another problem..I have deleted some of the flashplugin&watso ever.so files from my system manually... Removed completely all the packages from synaptic manager & then installed adobe flash plugin from synaptic manager again... no use :( & the 3rd one i am attaching a screenshot for it...

Right now i have only adobe flash installed on my system according to my Synaptic manager... Btw i have tried Adobe flash 11 in the meantime..& manually deleted the .so file...I really have no idea how i messed my flash on my ubuntu...I dont wanna lose my system or reinstall it now... I really appreciate ur help btw :) thank you much for helping me 

Edit: btw i have Ubuntu-Restricted-extras installed too... 

[IMG]http://i53.tinypic.com/25a3sqw.png[/IMG]

---

### Post by TenPlus1 on 2011-04-21
Try going back into Synaptic and removing all of these (if installed):

adobe-flashplugin
flashplugin-installer
flashplugin-nonfree
flashplugin-nonfree-extrasound

...then close Synaptic, go into your home folder and show hidden files and delete the '.adobe' directory, now re-open Synaptic...

search for 'flash' and mark the 'flashplugin-installer' for install, this will download the latest version of flash from adobe and install it where Firefox and any other browser will find it...

---

### Post by arafu on 2011-04-22
Thank you so much... i have followed every direction u have given... I am downloading flashplugin-installer now... I'll let you know if it works for my browsers :) again thank you so much

---

### Post by arafu on 2011-04-22
Installed flashplgin-installer..rebooted my machine...still Did not work :( I think i have to re install my ubuntu/keep zsnes emulator running :(

[IMG]http://i52.tinypic.com/zmebzn.png[/IMG]

---

### Post by Frogs Hair on 2011-04-22
If you are running 64 bit and Firefox try this add-on  [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by arafu on 2011-07-06
sorry i wasn't around .. I have tried that addon too..No use.. after upgrading to ubuntu 11.04.. I have found that the ZSNES trick to play flash on my bowser does not work anymore either.. though sometimes out of some luck, Firefox play the flash animations..  I have not figured out the problem yet.. so what I have do now is, I have installed a video downloader plugin in Firefox & I have to download them first..to watch them.. It's little painful but that is all i can do rite now.. I can't miss youtube :(

---

### Post by wildmanne39 on 2011-07-07
> **arafu said:**
> sorry i wasn't around .. I have tried that addon too..No use.. after upgrading to ubuntu 11.04.. I have found that the ZSNES trick to play flash on my bowser does not work anymore either.. though sometimes out of some luck, Firefox play the flash animations..  I have not figured out the problem yet.. so what I have do now is, I have installed a video downloader plugin in Firefox & I have to download them first..to watch them.. It's little painful but that is all i can do rite now.. I can't miss youtube :(
Hi,open firefox and install the flashaid addon, then follow the directions it usually fixes all flash problems.

---

