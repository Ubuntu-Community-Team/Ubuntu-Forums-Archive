---
title: "Change ubuntu desktop look &amp; feel"
date: 2008-06-28
forum: Desktop Environments
---

### Post by franky_88 on 2008-06-28
Hello Everyone,


I know that some of you might not like the idea, but I am trying to change my ubuntu desktop so that it looks and feels like Mac OS X. I downloaded Mac4Lin and followed the document that came with it. Some things works but I still have some problems. I just can`t change the upper panel so that it looks like the mac one. The sounds don`t work too. I copied them as root into the sounds folder but it does not seem to work.I also wondered if it was possible to change the boot image, the one with the ubuntu logo and ubuntu written in big black font with a loading line that is yellow. Is it possible to put the dock permanently so that when ubuntu loads I have it there without having to go start Avant-window navigator. I can`t seem to change the icon images such as the folder images and other application images. I know that I have a lot of questions but any help would be greatly appreciated.


Thank you,

Frank

---

### Post by saidinesh5 on 2008-06-28
> **franky_88 said:**
> Hello Everyone,


I know that some of you might not like the idea, but I am trying to change my ubuntu desktop so that it looks and feels like Mac OS X. I downloaded Mac4Lin and followed the document that came with it. Some things works but I still have some problems. I just can`t change the upper panel so that it looks like the mac one. The sounds don`t work too. I copied them as root into the sounds folder but it does not seem to work.I also wondered if it was possible to change the boot image, the one with the ubuntu logo and ubuntu written in big black font with a loading line that is yellow. Is it possible to put the dock permanently so that when ubuntu loads I have it there without having to go start Avant-window navigator. I can`t seem to change the icon images such as the folder images and other application images. I know that I have a lot of questions but any help would be greatly appreciated.




hey thats okay...actually i tried it out too, infact the look is pretty good..
well here is where i got my info from:

linuxondesktop.blogspot.com

there was a step by step for everything out there...so just check what went wrong...

dunno about the sounds thing..

n yes you can simply add the Avant-Window navigator to the startup items..
and well once visit this blog page, if that doesnt help you, then temme what exactly went wrong step by step..i will try my best

all the best

---

### Post by linuxisevolution on 2008-06-28
> **franky_88 said:**
> Hello Everyone,


I know that some of you might not like the idea, but I am trying to change my ubuntu desktop so that it looks and feels like Mac OS X. I downloaded Mac4Lin and followed the document that came with it. Some things works but I still have some problems. I just can`t change the upper panel so that it looks like the mac one. The sounds don`t work too. I copied them as root into the sounds folder but it does not seem to work.I also wondered if it was possible to change the boot image, the one with the ubuntu logo and ubuntu written in big black font with a loading line that is yellow. Is it possible to put the dock permanently so that when ubuntu loads I have it there without having to go start Avant-window navigator. I can`t seem to change the icon images such as the folder images and other application images. I know that I have a lot of questions but any help would be greatly appreciated.


Thank you,

Frank
to start applications auto-maticly on start-up click system>prefrences>sessions. then type the command for avant.

right click the upper pannel and click properties. then click backround tab and select "use system theme".

to manage sounds click system>prefrences>sound. then sounds tab. copy the sounds to your home folder then select them in the sounds tab for each event.

to change boot image click applications>add/remove>startup-manager ( or sudo apt-get install startup-manager ) after it installs click system>admin.>startup-manager.click appearance and then "manage usplash themes".. you will have to download the splash screen you want. 

for the icons right-click desktop. click "change desktopbackround" then click the theme tab. that is where you install and manage themes. click customize and then the icons tab to manage icon themes.

thats all you asked. through them at me :) hehe its 2:03 A.M here so you better be greatful... :) good luck. im 14 so i like spreading knowledge. ;)

---

### Post by franky_88 on 2008-06-28
Okay so I checked out the link on the blog that you gave me. The theme looks perfect now. There is only two little problems left, the sounds and th usplash screen. I installed startup manager and got 2 .so files that came with Mac4Lin and Mac OS X ultimate from gnome-look.org. The problem is that when I choose either one of them and then close the startup manager it gives me this message: configuring post(...) task. Then I go back to see if everything is alright and it changed to the ubuntu splash screen automatically. I followed the guide to put sounds in the /usr/share/sounds folder but still it doesn`t work.


Thank you for your help,


Frank

---

