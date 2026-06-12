---
title: "ubuntu desktop effects, not nvidia/ati."
date: 2009-03-23
forum: Desktop Environments
---

### Post by hoboboot on 2009-03-23
i have a s3 unichrome pro. intrepid ibex,  and my video card, when glxinfo is listed, says it supports direct rendering =yes,

so what i want to know, is this... i dont have a nvidia, or ati, obviously im using a via s3 unichrome pro igp and ...

i've read about the whitelist for compiz, never got it going though, im wondering, is it possible for me to do 3d desktop and or any other cool desktop effects in ubuntu? if so, can you please list them, so i can look into them, and if you have any form of "how to, with a shittier video card-that does support direct rendering" articles, please post them too... 

THANKS ALOT!

---

### Post by Aflack on 2009-03-23
What happens exactly when you try to do compiz effects

---

### Post by milesukaoma on 2009-03-23
try this
wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check

Afterwards, you have to make it executable:
chmod +x compiz-check

And finally run it like this:
./compiz-check

this got mine running. remember to run the first line in your root terminal and the rest your normal terminal. hope this helps post the results of the second line back if it dosent and i will see if i can help you furthur if it ask you to run it but your missing something just put Y for yes if one of the checks says yes then you can most likley run compiz but it might not be as smooth as you would like. minehas 4/5 and runs perfect

---

### Post by milesukaoma on 2009-03-23
i know the first one looks like alink it is a command you use in a terminal

---

### Post by hoboboot on 2009-03-23
ok i ran it, with sudo, and the second command, the chmod one i had to sudo because, well, here, look at the results and if you can help me any further, that would be awesome:


hobo@metaverse:~$ sudo wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check
[sudo] password for hobo: 
--2009-03-23 23:33:35--  [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download)
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/octet-stream]
Saving to: `compiz-check'

    [   <=>                                 ] 28,360      50.6K/s   in 0.5s    

2009-03-23 23:33:36 (50.6 KB/s) - `compiz-check' saved [28360]

hobo@metaverse:~$ chmod +x compiz-check
chmod: changing permissions of `compiz-check': Operation not permitted
hobo@metaverse:~$ sudo chmod +x compiz-check
hobo@metaverse:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 

hobo@metaverse:~$ 





so, its using openchrome? i did not know that... see, in 8.04, it was vesa, and could not do direct rendering, glxgears was like, well, it went from 23 fps to 850 fps when i went from hardy heron, to intrepid ibex, by default with what the video card detected as in each... now...
in ibex, i figured, i should be able to run compiz because, it says i CAN do direct rendering... is this the case? or ... im not sure personally, i'd love it to be able to get that stuff running, even just some, any better than basic desktop effects going i'd be really happy but, the cube, and that stuff, its awesome. i have it on my xp, but, god knows its meant for linux...and thats what i want it for... once i get it kicking i'd like to trash my windoze for good.
thanks in advance for any help you can provide!

---

### Post by inobe on 2009-03-24
if you can get that going it would be great...

i have tried for more than a month and said the heck with it and purchased a cheap nvidia card to fill the empty pci-e slot.

---

### Post by hoboboot on 2009-03-24
yeah it'd be nice if i could do that. i would. but this is my laptop im on, and i just want a couple good effects on but... not having much much luck so far.

---

### Post by inobe on 2009-03-24
it was a biostar p4m900 m4 [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138079](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138079)


i went here [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150) and i can see your driver, it is not openchrome !


here's the problem, if you sport any of the newer ubuntu releases' this driver won't work, though possible it won't be easy.

these drivers won't work with the newest xorg and the openchrome driver is "slow 3d"

if your good' you may be able to get it going in debian, the deb os needs lots of building just to install that driver.

none the less keep track of xorg and the hardware vendors, the vendors need to produce a better driver when xorg is updated.

apparently via hasn't been

---

### Post by hoboboot on 2009-03-24
well see, thats funny. because i had like, 7.10 it was ******, then 8.04 i got it to at least the right resolution, but then i couldnt get even the openchrome to work for that, and then... basically when i put 8.10 in it had the video card glxgears running so fast and direct rendering=yes, so i was quite excited...

as for the via drivers, your right, in 8.04 i couldnt get them to work, it just crapped out when i tried.... and i believe that i had to shut down and turn it back on to get any display after that, for some reason it didnt do a default timeout after so many seconds or whatever... so...
that really sucks... 

i wonder if osx86 could be made to work on this laptop... 
im doubting it. my gateway mx3210 here is a POS. the cpu is rated for 20 degrees hotter than what my dads gateway's cpu is rated to run at... they're from the same year, i got a 14 inch and he got a little big bigger... bigger was better... this thing, i cant even run it on a glass table for fear the glass will crack from the heat, it gets hot enough to burn your hand if you give it a full 2 seconds, most people cant hold their skin to it for very long.. haha. oh well, sound, and **** is running... i'm going to try quake3 with this shitty openchrome driver i guess... eventually when i get around to it... and then if that works, i'll probably still scrap winblowz.


 one thing i want to know, is java a part of my ubuntu by default? i know that, flash has a few problems, however i just got an update for that with a bunch of other ones, so maybe its better now, but,
is that why the page i was going to didnt work? all i can think is, it needed java and doesnt have it? 

i'll have to go test it out i guess because, if i cant surf the same. im not going to like it.... i've gotta get that fixed... my heavily modded winxp is... well... i've stripped everything bad out of it.. and its practically os9 stylez. with the cube though babyyyy oh yeah...
[CENTER]
[img]http://i9.photobucket.com/albums/a70/bentside/cubedesktop.jpg[/img]
[IMG]http://i9.photobucket.com/albums/a70/bentside/desk2.jpg[/IMG]
[IMG]http://i9.photobucket.com/albums/a70/bentside/ubuntz.jpg[/IMG][/CENTER]

but still, its windoze...i wish to have the sweetest desktop effects god damnit. oh well i guess,

---

### Post by inobe on 2009-03-24
so that's installed in windows using "wubi" ?

[http://wubi-installer.org/screenshots.php](http://wubi-installer.org/screenshots.php)

---

### Post by hoboboot on 2009-03-27
hell no. 
i have never used wubi.

its not installed in windows

its on a seperate drive with a seperate bootloader, when connected, the computer boots ubuntu. when not, 

my modded xp boots yo...

who the hellz said i used wubi. hell nahz.

---

