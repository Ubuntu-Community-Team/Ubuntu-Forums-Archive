---
title: "Script for install beryl&amp;XGL on dapper"
date: 2007-01-09
forum: Desktop Environments
---

### Post by ZipoTe on 2007-01-09
Hi ubuntu fans!! specially xgl&beryl ones :P

As lots of people are runnig ubuntu 6.06, this xmas i've been working into a script that should install xgl and beryl in your wonderful ubuntu dapper.

I did it reading this post:
[http://ubuntuforums.org/showthread.php?t=268036&highlight=beryl+dapper]("http://ubuntuforums.org/showthread.php?t=268036&highlight=beryl+dapper")

The script modifies xorg.conf so you don't have to do anything ^^


(ok, i commented the "keys" as they were causing little troubles)


Here it is:

```
#!/bin/bash

OP=zipote
clear





if [ ! -w /var/lib/dpkg/lock ];
then

echo YOU ARE NOT ROOT
echo 
echo please, execute sudo ./beryl
sleep 2

else
clear
echo "#########################"
echo INSTALLING NVIDIA DRIVERS
echo "#########################"
echo
echo
apt-get install nvidia-kernel-common nvidia-glx --yes
sleep 2
clear

echo "#########################################"
echo 'WARNING! "xorg.conf" and "gdm.conf-custom" are going to be changed'
echo "#########################################"
echo
echo
echo "A file named rename is going to be made in your home folder" 
echo "In case of X error type on a terminal       sudo ~/./rename"
echo "When typing this, all changes made by this script will be erased"
echo
echo
echo
echo 

rm ~/rename
touch ~/rename

echo "#!/bin/bash" >> ~/rename
echo "mv /etc/gdm/gdm.conf-custom2 /etc/gdm/gdm.conf-custom" >> ~/rename

echo "mv /etc/apt/sources.backup /etc/apt/sources.list" >> ~/rename

echo "mv /etc/X11/xorg2.conf /etc/X11/xorg.conf" >> ~/rename

echo "exit" >> ~/rename

chmod a+x ~/./rename


echo
echo PRESS ENTER AFTER READING ALL THE WARNINGS
echo IF YOU ARE NOT SURE CLOSE THIS WINDOW OR PRESS   cntrl+c

read KEY




clear
sleep 0.5
echo "#############################"
echo configuring nVidia drivers...
echo "#############################"

cp /etc/X11/xorg.conf /etc/X11/xorg2.conf



cat /etc/X11/xorg.conf | sed -e "/Glcore/s/Load/#Load/" > /etc/X11/xorgback.conf 
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf

cat /etc/X11/xorg.conf | sed -e "/dri/s/Load/#Load/" > /etc/X11/xorgback.conf
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf

cat /etc/X11/xorg.conf | sed -e "/glx/s/Load/#Load/" > /etc/X11/xorgback.conf 
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf

cat /etc/X11/xorg.conf | sed -e '/Module/a\    Load           "glx"' > /etc/X11/xorgback.conf
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf



echo
echo FINALIZING...
sleep 1
clear
sleep 0.5


echo "setting up XGL&Beryl..." 
cp /etc/apt/sources.list /etc/apt/sources.backup
echo "#################################" >> /etc/apt/sources.list
echo "##XGL&Beryl REPOS" >> /etc/apt/sources.list
echo "#################################" >> /etc/apt/sources.list
echo    >> /etc/apt/sources.list
echo "deb http://www.beerorkid.com/compiz dapper main aiglx" >> /etc/apt/sources.list
#echo "deb http://media.blutkind.org/xgl/ dapper main aiglx" >> /etc/apt/sources.list
echo

##keys
#wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
#wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
##
apt-get update
apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes --yes

sleep 1
echo FINALIZING...


cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom2
echo
echo "0=Xgl" >> /etc/gdm/gdm.conf-custom
echo "[server-Xgl]" >> /etc/gdm/gdm.conf-custom
echo "name=Xgl server" >> /etc/gdm/gdm.conf-custom
echo "command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo" >> /etc/gdm/gdm.conf-custom
echo "flexible=true" >> /etc/gdm/gdm.conf-custom



clear
echo INSTALATION COMPLETE
sleep 2
clear
echo reboot your computer 
echo

echo
echo
echo
echo
echo
echo press enter
read INTRO

fi

exit
```


add beryl-manager to startup sessions

copy the code and save it as beryl

open a terminal, go where you saved the script and type:

chmod a+x ./beryl

and now you can execute it typing:

sudo ./beryl

--------------

**EDIT**:

**WARNING!!!!** read this----> IF YOUR INSTALATION DOES NOT WORK AND YOU WANT TO TRY IT A SECOND TIME, FIRST DO:

sudo ~/./rename

this will erase all changes done by the script, ok?

--------------

**EDIT**:

If you reboot your system after runnig the script, and when loading gnome you get a blue screen telling some X error... don't worry,this is because in your xorg.conf, the Section "Device" loads "nv" driver instead of the "nvidia" one. just type this: 

sudo nano /etc/X11/xorg.conf

look for Section "Device" and change driver "nv" for "nvidia"

note: it didn't happen to me but a friend of mine had to do it so :P better if you get addvised. In a few days the script will check for the "nvidia" driver automatically so you don't need to do anything ^^

--------------

write suggestions ^^

**note**: this is only for nvidia, lookin' for ATI? check this: [http://ubuntuforums.org/showthread.php?t=338771&highlight=script]("http://ubuntuforums.org/showthread.php?t=338771&highlight=script") (only for edgy)

---

### Post by Grog140 on 2007-01-09
Didn't work for me, though I found where it is messing up I think.

First of all, there needs to be one more pound sign in what you add to the sources.list file (in front of the "XGL&Beryl REPOS" part. And then you need to include the key to the added repos.

---

### Post by ZipoTe on 2007-01-10
Thanks for trying it :P and for your suggestion.

In a few hours i'll change it, now... i must lunch :)




bye!

---

### Post by ZipoTe on 2007-01-10
ok, i've changed few things that i forgot (first i did it in spanish and when doing the translation i did little changes and missed a "#" :P)

check it now


**NOTE:** if the script doesn't work again tell me exactly what is wrong and i'll take a look :D

---

### Post by Grog140 on 2007-01-10
I like it, the only thing I had to do to make it work for me was 

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
```

I am not sure if you have to add this after you add the repositories to the sources.list, but I had to when I did it.

Its really nice, aside from having to do that one thing it worked like a charm.

---

### Post by ZipoTe on 2007-01-10
**EDIT**

well i added the keys you give **before** the apt-get update.

anyone has tried it??

---

### Post by konungursvia on 2007-01-10
Yes I tried it but I don't know if it worked yet. There were several file not found errors, repositories that were not read. Does it matter?

---

### Post by konungursvia on 2007-01-10
Okay, I ran the script and logged in again but < blush > can't tell if beryl installed. How do I know? How do I run it?

---

### Post by ZipoTe on 2007-01-11
mmm did you add Beryl-Manager to startup sessions?? As Grog140 said, the only problem i found was the keys... 

tell me if you have beryl-manager at the startup

---

### Post by Waappu on 2007-01-11
Hi

I haven't test scrip, but it looks nice. One thing for maybe more user frendly option is that you can do ~/rename file also script file. So if something goes wrong user just type sudo ~/rename.
How this sounds ??

---

### Post by ZipoTe on 2007-01-11
Aham. i understand. Yes it's a good idea i didn't think about it i will add this to the script. Maybe I can do a menu with two options: "Install xgl&beryl" or "Remove instalation". This second option would change the xorg.conf file in case of error and also the gdm-custom ^^

Or well... i can also only tell the script to make another script named "rename" independent to the first...

what do you prefer? :D

---

### Post by Waappu on 2007-01-11
Hi
Maybe you do first simple rename script and take care other problems if any. Then add fancy features =)

As simple as it can go is better for user point of view =) I think.
One command for install and another for reverse. But these are just things cross my mind when looking that script. It's great already, but if something goes wrong it could be superb for new users that there is simple escape.

---

### Post by ZipoTe on 2007-01-11
Ok, i'll add this feature. If something goes wrong you only have to type sudo ~/./rename and it will change your xorg.conf ^^

---

### Post by Waappu on 2007-01-11
Hi

Thats good =)
As I say I didn't test that script, but if I can read it correctly it might generate problems if some one run it twice e.g. duplicate entrys on /etc/apt/sources.list file. Correct me if I'm wrong. If that is case maybe add some warning or prevent that.

---

### Post by ZipoTe on 2007-01-11
bufff i thought it would be easy :P

well, now the script does another script that removes all the changes ^^

if you tipe sudo ~/./rename all changes are removed :D

---

### Post by Grog140 on 2007-01-11
I think I might know why I had to add the keys manually 

When I tried the script with the missing "#" it gave me a wacky error. So I manually went into the file and commented it.

I then tried the script again which brought the same error because I forgot to edit your script so it would put the comments in. So I though you might have excluded the keys so I ran the command to get those. I also fixed the comment myself at that point.

So when I ran it again it worked not because I added the keys manually but because I added the extra comment to the actual script.

My fault, sorry. Its still a great script though.

---

### Post by ZipoTe on 2007-01-12
Oh don't worry, now the script works great ^^ and well... keys are not a problem if they are or not they don't affect (i think :P)

I would like to know if someone else has tried it yet

If some users run this script and they like it, i will work into another more friendly one (with menus to select "new installation" "re-install" "restore configuration" and things like that)

---

### Post by digilink on 2007-01-12
Nice looking script, I would like to give this a try. I have tried many many times in the past to get Beryl working under 6.06 without success. 

One question on the Nvidia driver install, could I safely delete that section in the script if I already have the binary drivers from Nvidia loaded?

---

### Post by ZipoTe on 2007-01-12
you mean this?

> apt-get install nvidia-kernel-common nvidia-glx --yes


yes you can ;)

if you have problems with the keys remove them also :P

---

### Post by digilink on 2007-01-12
> **ZipoTe said:**
> you mean this?




yes you can ;)

if you have problems with the keys remove them also :P

Very good! I'll try it later tonight and post my results, hopefully this will work out to my satisfaction.......

---

### Post by ZipoTe on 2007-01-12
all right

remember, if you have any trouble:

sudo ~/./rename

i'll be waiting for your post :D

---

### Post by digilink on 2007-01-12
One other question, what is this variable for in the script?

```
OP=zipote
```

And after looking at this just for clarification, is this section of the script to create the rename script?

```

rm ~/rename
touch ~/rename

echo "#!/bin/bash" >> ~/rename
echo "mv /etc/gdm/gdm.conf-custom2 /etc/gdm/gdm.conf-custom" >> ~/rename

echo "mv /etc/apt/sources.backup /etc/apt/sources.list" >> ~/rename

echo "mv /etc/X11/xorg2.conf /etc/X11/xorg.conf" >> ~/rename

echo "exit" >> ~/rename

chmod a+x ~/./rename

```

I also edited out the nvidia driver section, just want to make sure my syntax is correct:
```

#!/bin/bash

OP=zipote
clear





if [ ! -w /var/lib/dpkg/lock ];
then

echo YOU ARE NOT ROOT
echo
echo please, execute sudo ./beryl
sleep 2

else
clear
echo "#########################################"
echo 'WARNING! "xorg.conf" and "gdm.conf-custom" are going to be changed'
echo "#########################################"
echo
echo
echo "A file named rename is going to be made in your home folder"
echo "In case of X error type on a terminal       sudo ~/./rename"
echo "When typing this, all changes made by this script will be erased"
echo
echo
echo
echo

```

thanks......

---

### Post by ZipoTe on 2007-01-12
OP=zipote doen't do anything :p it's just a value i used in the past but now it has no sense



> rm ~/rename
touch ~/rename

echo "#!/bin/bash" >> ~/rename
echo "mv /etc/gdm/gdm.conf-custom2 /etc/gdm/gdm.conf-custom" >> ~/rename

echo "mv /etc/apt/sources.backup /etc/apt/sources.list" >> ~/rename

echo "mv /etc/X11/xorg2.conf /etc/X11/xorg.conf" >> ~/rename

echo "exit" >> ~/rename

chmod a+x ~/./rename

Yes, this is the part that creates rename script





> if [ ! -w /var/lib/dpkg/lock ];
then

echo YOU ARE NOT ROOT
echo
echo please, execute sudo ./beryl
sleep 2

else
clear
echo "#########################################"
echo 'WARNING! "xorg.conf" and "gdm.conf-custom" are going to be changed'
echo "#########################################"
echo
echo
echo "A file named rename is going to be made in your home folder"
echo "In case of X error type on a terminal       sudo ~/./rename"
echo "When typing this, all changes made by this script will be erased"
echo
echo
echo
echo

do not change this, because the script need this "if"
instead of that, comment the lines you don't need ^^

---

### Post by digilink on 2007-01-12
> do not change this, because the script need this "if" instead of that, comment the lines you don't need ^^

I was going to do that initially, but feared it would break it so I just cut out all the Nvidia driver stuff and left the if, then, else statement in there, will it still work like that? Or would it be best to just comment it out? 

What lines do I need to comment if so for it to work properly?

I'm at work at the moment and won't be able to try any of this until I get home, but at least I can have the script ready :D

---

### Post by ZipoTe on 2007-01-12
just delete or comment the apt-get nvidia... you know all this stuff

and another thing, it didn't happen to me but look at your xorg.conf and be sure it loads the "nvidia" driver not the "nv" or "vesa" or something strange :P


bye!!

---

### Post by digilink on 2007-01-12
I got the script ran, I did have to wrestle with the keys a bit, and I also noticed that there was a newer version of the Nvidia driver versus what I was running, so I went ahead and downloaded it and installed it and commented out the key adds in the script. 

Everything appears to have installed, I get the Beryl splash screen when beryl-manager starts, but for some reason the window borders flicker? Not sure what to make of that, it seems like also I remember seeing a connection refused to one of the repositories, so I'm not 100% sure I even have everything installed correctly?

---

### Post by ZipoTe on 2007-01-13
Flickering windows... try adding "emerald" to the startup programs.

I remember reading something about it and adding emerald was the solution

---

### Post by henriquemaia on 2007-01-14
Hi,

I get this error:

[http://media.blutkind.org/xgl/dists/dapper/Release.gpg:](http://media.blutkind.org/xgl/dists/dapper/Release.gpg:) Could not connect to media.blutkind.org:80 (216.55.142.216). - connect (111 Connection refused)
[http://media.blutkind.org/xgl/dists/dapper/main/i18n/Translation-en_US.bz2:](http://media.blutkind.org/xgl/dists/dapper/main/i18n/Translation-en_US.bz2:) Could not connect to media.blutkind.org:80 (216.55.142.216). - connect (111 Connection refused)
[http://media.blutkind.org/xgl/dists/dapper/aiglx/i18n/Translation-en_US.bz2:](http://media.blutkind.org/xgl/dists/dapper/aiglx/i18n/Translation-en_US.bz2:) Could not connect to media.blutkind.org:80 (216.55.142.216). - connect (111 Connection refused)

and beryl can't be installed.

---

### Post by ZipoTe on 2007-01-14
Yes, i noticed media.blutkind.org does not work... so i'll comment it

please, run sudo ~/./rename and try installing it another time with the lines that contains "media.blutkind.org" commented

(i'll do now on the script here posted)

If it doesn't work at all please, tell me. I want my script working great, so your help is needed :D

thanks and sorry for any trouble

---

### Post by henriquemaia on 2007-01-14
Hi,

Thanks for your reply. If the repository [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx is commented out, the result is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
Note, selecting libgl1-mesa-glx instead of libgl1-mesa
libgl1-mesa-glx is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
E: Couldn't find package beryl

---

### Post by ZipoTe on 2007-01-14
Hi!

so the only package that it doesn't find is beryl?? i'm feeling bad :P

i don't understand, reading this --> [http://www.beerorkid.com/compiz]("http://www.beerorkid.com/compiz") i understood with one "repo" it should be done :S

maybe adding one of the repositories in this web can help...

please, try and let me know. If this works i'll do few changes on the script

---

### Post by ZipoTe on 2007-01-14
answer to myself:

I tryed only with deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main and it works

I uninstalled beryl and installed it again with this only "repo" so, if it didn't work for you i don't really now why ](*,)

REMEMBER: after changing the sources.list you must do:
sudo apt-get update

maybe this is the clue

---

### Post by henriquemaia on 2007-01-14
Hi,

I think I know why. I'm running Edgy amd64 version. I googled around and found this repository:

[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

and now beryl is installed. I just have to figure out why beryl is not working - there is something messed up in my home configurations, because I have tried starting a session with a different user and beryl starts ok.

---

### Post by ZipoTe on 2007-01-14
ouch!

this script is for dapper :p so... this is the reason it doesn't work on edgy ^^

thanks for trying it :D

---

### Post by henriquemaia on 2007-01-14
** 	Script for install beryl&XGL on dapper  **

Duh!

Well, but apart from that repository glitch, it worked. Thanks anyway for all your help.

---

### Post by ZipoTe on 2007-01-15
yeah, don't worry

by the way, digilink, did you try what i told you?

---

### Post by emtjr928 on 2007-01-31
ZipoTe, I ran the script as I have attached below. My command line skills faded over the years from using M$. Did I miss something? Beryl settings manager seems to be there as does Emerald themes manager and I added Beryl-Manager to the startup. Don't see any listing in config editor for beryl or compiz. Any help would be appreciated.

#!/bin/bash

OP=zipote
clear





if [ ! -w /var/lib/dpkg/lock ];
then

echo YOU ARE NOT ROOT
echo 
echo please, execute sudo ./beryl
sleep 2

else
clear
echo "#########################"
echo INSTALLING NVIDIA DRIVERS
echo "#########################"
echo
echo
#apt-get install nvidia-kernel-common nvidia-glx --yes
sleep 2
clear

echo "#########################################"
echo 'WARNING! "xorg.conf" and "gdm.conf-custom" are going to be changed'
echo "#########################################"
echo
echo
echo "A file named rename is going to be made in your home folder" 
echo "In case of X error type on a terminal       sudo ~/./rename"
echo "When typing this, all changes made by this script will be erased"
echo
echo
echo
echo 

rm ~/rename
touch ~/rename

echo "#!/bin/bash" >> ~/rename
echo "mv /etc/gdm/gdm.conf-custom2 /etc/gdm/gdm.conf-custom" >> ~/rename

echo "mv /etc/apt/sources.backup /etc/apt/sources.list" >> ~/rename

echo "mv /etc/X11/xorg2.conf /etc/X11/xorg.conf" >> ~/rename

echo "exit" >> ~/rename

chmod a+x ~/./rename


echo
echo PRESS ENTER AFTER READING ALL THE WARNINGS
echo IF YOU ARE NOT SURE CLOSE THIS WINDOW OR PRESS   cntrl+c

read KEY




clear
sleep 0.5
echo "#############################"
echo configuring nVidia drivers...
echo "#############################"

cp /etc/X11/xorg.conf /etc/X11/xorg2.conf



cat /etc/X11/xorg.conf | sed -e "/Glcore/s/Load/#Load/" > /etc/X11/xorgback.conf 
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf

cat /etc/X11/xorg.conf | sed -e "/dri/s/Load/#Load/" > /etc/X11/xorgback.conf
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf

cat /etc/X11/xorg.conf | sed -e "/glx/s/Load/#Load/" > /etc/X11/xorgback.conf 
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf

cat /etc/X11/xorg.conf | sed -e '/Module/a\    Load           "glx"' > /etc/X11/xorgback.conf
mv /etc/X11/xorgback.conf /etc/X11/xorg.conf



echo
echo FINALIZING...
sleep 1
clear
sleep 0.5


echo "setting up XGL&Beryl..." 
cp /etc/apt/sources.list /etc/apt/sources.backup
echo "#################################" >> /etc/apt/sources.list
echo "##XGL&Beryl REPOS" >> /etc/apt/sources.list
echo "#################################" >> /etc/apt/sources.list
echo    >> /etc/apt/sources.list
echo "deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx" >> /etc/apt/sources.list
#echo "deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx" >> /etc/apt/sources.list
echo

##keys
#wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
#wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
##
apt-get update
apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes --yes

sleep 1
echo FINALIZING...


cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom2
echo
echo "0=Xgl" >> /etc/gdm/gdm.conf-custom
echo "[server-Xgl]" >> /etc/gdm/gdm.conf-custom
echo "name=Xgl server" >> /etc/gdm/gdm.conf-custom
echo "command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo" >> /etc/gdm/gdm.conf-custom
echo "flexible=true" >> /etc/gdm/gdm.conf-custom



clear
echo INSTALATION COMPLETE
sleep 2
clear
echo reboot your computer 
echo

echo
echo
echo
echo
echo
echo press enter
read INTRO

fi

exit

---

### Post by ZipoTe on 2007-01-31
wow! i thought this post was dead lol

ok, so the problem is... beryl does not start or what?

did you try starting beryl-manager manually?

explain me what's exactly the problem and be sure i'll help you :D


thank you!!

---

### Post by emtjr928 on 2007-01-31
Thanks, I can start Beryl-Manager from terminal, but won't start from entry in start up programs. Only shows one work space. I do get some window animations and color. Some title bars and min ,restore and close icons will be missing.Some times with a window open I cannot get back to the top panel.Not sure where to look.

---

### Post by ZipoTe on 2007-01-31
sometimes? so it's random... :-? that's ugly...

ok, now i don't know the answer for your problem, but i'll do some research :p if you solve this issue before i give you an answer post it ^^

and if someone has the answer... post it also :D

bye!

---

### Post by ZipoTe on 2007-01-31
ok, be sure you have emerald, beryl and beryl-manager properly installed

try running emerald or emerald --replace from terminal


also post here what shows when typing beryl from terminal ^^

---

### Post by emtjr928 on 2007-01-31
Ok, Typed both from term. and got nothing. Used your script to remove changes, uninstalled all beryl components with pkg. manager. Ran you script again this time letting it get and configure the nvidia drivers.(I had previously used "envy" to get and install the latest and greatest.
Only glitch I saw while the script was running was "failed to fetch ubuntu.compiz.net dist/dapper yada yada.
On reboot GDM was broken. Got to terminal and recovered to pre install.
Whew, Not sure what is going on. I'm new at this.
Ed

---

### Post by ZipoTe on 2007-02-01
Ok... buff do sudo ~/./rename again and let my script finish. Before rebooting your system go to /etc/X11/ and send me a copy of the xorg.conf. Then, go to /etc/gdm/ and send me another copy of the gdm.conf-custom. I'll have a look at them, maybe there is some option missing.

---

### Post by PartisanEntity on 2007-02-01
Hello thanks for the script, I am going to give this a try today, just as soon as I print out this entire thread and have something to eat first :)

Are these working: ?

> deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

One other question, my graphics card is an Nvidia GeForce Go 6200 with TurboCache, is XGL compatible with TurboCache cards or do I need AIGLX?

---

### Post by PartisanEntity on 2007-02-01
It worked, but before running the script I had to do:

> wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -

However the window borders are blinking strangeley so I have to find out why.

Thanks very much for this script! :)

---

### Post by ZipoTe on 2007-02-01
Hi!!

Yes, you can do this but it should work without the keys :P. the repositorie [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) was down, but the beerorkid works perfectly ;)

The issue of the windows... some people have this problem, i don't know why. Sometimes adding emerald to the startup programs solves the problem... i don't really know much about beryl. What you can do is looking at beryl-project forums or send me a private message with your xorg.conf. I'll take a look at it. Maybe there is some option missing or something like that... ^^

---

### Post by PartisanEntity on 2007-02-01
Thanks for the info, concerning the blinking window borders this solved it:
[http://www.ubuntuforums.org/showpost.php?p=1731016&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1731016&postcount=4)

Everything seems to be working, im really impressed with your script, nice work and thank you again :)

---

### Post by emtjr928 on 2007-02-01
Been busy but did do some research and found this from nvidia. My card is the geforce 6600le.
> There are several tutorials and HOWTOs available on the web that cover building and installing compiz, so I will not cover that here. Please note however, that when following these guides, any steps regarding the installation of Mesa OpenGL libraries, the DRI, or Xgl should be skipped. The NVIDIA driver contains built-in support for GLX_EXT_texture_from_pixmap, so these extra layers are not necessary, and may in fact cause problems (
Could this be part of the problem?
Ed

---

### Post by ZipoTe on 2007-02-02
Hi!!

well, it can be, but normally this kind of errors occur when xorg.conf is not well configured, so probably the best thing we can do is having a look at your xorg.conf ^^

---

### Post by emtjr928 on 2007-02-02
I may try again. Since I have the newest stable nvidia drivers installed 1.0-9746 should I comment out the driver reference in the script?

---

### Post by ZipoTe on 2007-02-02
first do a sudo ~/./rename, then you should comment out:

apt-get install nvidia-kernel-common nvidia-glx --yes      (this installs nvidia drivers using apt-get)

i think you have tu uninstall the repositories drivers before installing the nvidia ones. after that run my script :D

---

### Post by emtjr928 on 2007-02-02
Here are attached my before and after xorg.conf files. The only change I can see is to not load dri which my card supports.
before:
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe
After:

Section "Module"
    Load           "glx"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	#Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"

My after GDM custom:
[servers]
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

have not restarted x or rebooted yet.
My card has dri, so why make it go away?

---

### Post by ZipoTe on 2007-02-02
Well i don't really know why, my script only automates the process for you. I read some how to and in most of them dri has to be away. My work is only to make the process easy, i don't know much about why the process has to be like this.

By the way, please post the Section Device ;)

---

### Post by emtjr928 on 2007-02-02
Ok Both are the same:
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600LE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

Also found this from the same nvidia I posted earlier although it applies to compiz:

You will need to ensure X is properly configured. The following bits should be in your X configuration file:

Code:

# Enable the composite extension 
Section "Extensions"
 Option "Composite" "Enable"
 EndSection 
Section "Screen"
 ... # Enable 32-bit ARGB GLX Visuals 
Option "AddARGBGLXVisuals" "True" 
# If you are using an older version of compiz that 
# does not support rendering into the Composite 
# Overlay Window, you will need to disable clipping
 # of GLX rendering to the X Root window with this 
# option, or you will get a blank screen after
 # starting compiz:
 Option "DisableGLXRootClipping" "True"
 EndSection

Ed

---

### Post by ZipoTe on 2007-02-02
Hi!!

add this at the end of your Section device, just like this:

```
Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600LE]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "RenderAccel" "true"[/COLOR]

```

after running my script if this line does not appear add it ^^ i'll change my script to make sure it is.

---

### Post by cprofitt on 2007-03-24
Is there a script like this for edgy -- and Nvidia cards?

I have an nvidia 6800 and have to use the vesa workaround to just load the OS.

Thanks.

---

### Post by ZipoTe on 2007-03-31
I don't really know, I'm a dapper/etch user so... :-? look for something here in the forums, i'm sure you'll have the answer :)

---

### Post by dgrafix on 2007-04-01
Hi, I tried it but when i initialise it (ie. run beryl-manager) it works, gomes up with the wobbly berlyl logo then goes totally white.

However, i can tell its working because I can see the cube with the logos on top and bottom but is not rendering the desktops. I can also see empty light grey boxes of windows that are popping up when i click around.

---

### Post by ZipoTe on 2007-04-02
I'm not a beryl user, i have a teapot as a computer :) so some issues i'm not sure why they happen. You can look for the answer here:

**[http://forum.beryl-project.org/]("http://forum.beryl-project.org/")**

If your problem disappears post here the answer or the link of the answer if you find it.

In any case, i'll look for something too ^^

---

