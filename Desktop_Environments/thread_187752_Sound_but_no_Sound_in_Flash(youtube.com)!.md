---
title: "Sound but no Sound in Flash(youtube.com)?!"
date: 2006-06-03
forum: Desktop Environments
---

### Post by dragi on 2006-06-03
Hello,

I´m new to Linux and installed yesterday kubuntu 6.06. It´s absolutely cool but I have a big Problem:
I love to watch videos on youtube.com but I don´t have sound in that videos?!

After the normal installation of kubuntu I installed firefox with Adept. Then I installed Flashplayer from the macromedia homepage. I have sound in KDE and the example Videos and Sounds from kubuntu work also. Only videos with Flash, like the youtube ones have no Sound.

Is there a way to fix this? Can someone please help me?

Thank you

dragi

---

### Post by brownrl on 2006-06-03
Best thing for me was running easyubuntu


[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Installs so many cool and needed things like codecs, rar, fonts, + more


R

---

### Post by Horizon on 2006-06-03
Also make sure you have no other sound app(or anything that relys on sound) open before going to youtube and watching the video. And closing the program and reloading the youtube page won't help. You'll need to close the browser and open it again if you had a sound app open the first time >.>

---

### Post by BoyOfDestiny on 2006-06-03
[QUOTE=Horizon]Also make sure you have no other sound app(or anything that relys on sound) open before going to youtube and watching the video. And closing the program and reloading the youtube page won't help. You'll need to close the browser and open it again if you had a sound app open the first time >.>[/QUOTE]

Here is why (at least for regular Ubuntu, not sure about Kubuntu):

[http://ubuntuforums.org/showpost.php?p=1085341&postcount=8](http://ubuntuforums.org/showpost.php?p=1085341&postcount=8)

ESD is going to cause problems for a lot of users... I really hope it is phased out...

Please either way, add comments to this bug report

[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)

---

### Post by Corvillus on 2006-06-03
The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.

---

### Post by moclippa on 2006-06-03
I had the same problem and just fixed it without EasyUbuntu (couldn't get it to work)

Command line solution:

$sudo apt-get update
$sudo apt-get install libflash-mozplugin

Alternatively you can just do it in your OS
System->Administrator->Synaptic Package Manager -- And search for libflash-mozplugin

If you don't find it, then you need to change your source.list... check out the forums for recommended repositories

---

### Post by BoneyOne on 2006-06-03
Sadly enough, none of the things listed here worked for me.

---

### Post by moclippa on 2006-06-04
Did you try installing Automatix?

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Let it update all the firefox scripts and plugins for you, as well as get you some extra codecs you may be missing....

Weird thing is, I thought I had the sound fixed in my Firefox, but after a restrart it was back to the way it was before... I'm using Automatix to update everything I may have missed now...

---

### Post by kayrune on 2006-06-04
sudo apt-get install alsa-oss

---

### Post by InsaneBeast on 2006-06-13
Thanks Corvillus that fix worked great!

---

### Post by sugonaut on 2006-06-14
I had the same problem when I upgraded to 6.06.  Flash worked great, but without sound.  I did the following...

1. I installed the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox.

Hope this helps.

Oh, and some other details - I had previously installed 'flashplugin-nonfree'.  I'm not using the 'libflash-mozplugin' package.

---

### Post by pkunal on 2006-06-15
[QUOTE=sugonaut]I had the same problem when I upgraded to 6.06.  Flash worked great, but without sound.  I did the following...

1. I installed the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox.

Hope this helps.

Oh, and some other details - I had previously installed 'flashplugin-nonfree'.  I'm not using the 'libflash-mozplugin' package.[/QUOTE]

This works perfectly !!!! Just installing alsa-oss is not enough have to change the firefoxrc file.

However after doing this I have a new annoyance. On a site if there is Flash as well as Realplayer videos. This causes my Realplayer to go to MUTE everytime I try to watch a new video. It happened on CBS News site.

If anyone has a solution please help.

pkunal.

---

### Post by Nda on 2006-06-29
[quote=Corvillus]The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
``` to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.[/quote] 
Many thanks, Corvillus.  This worked perfectly for me.

Nda

---

### Post by Tristan9669 on 2006-07-01
[QUOTE=Corvillus]The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.[/QUOTE]
thanks! :)

---

### Post by apocalypso on 2006-07-02
[QUOTE=Corvillus][SIZE="1"]The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.[/SIZE][/QUOTE]
You're the hax0r! \\:D/ 

No, really, thanks for the help, this problem was starting to really annoy me, as it took me a while when I first installed Ubuntu to make it work only to find out it had stopped working after installing the Xubuntu-Desktop... [-( 

I applied this little hack and it worked just fine, the way it should! Thanks again...

---

### Post by mtpadilla on 2006-07-03
[QUOTE=Corvillus]The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.[/QUOTE]


Corvillus, thanks a mill ;)  Incidentally, I was having a lack of sound problem not only with flash pages, but also real player feeds (ala BBC). Both now seem to produce sound consistently...cheers.

---

### Post by Miki01 on 2006-07-04
Corvillus and sugonaut's methods don't work for me? Why? T_T

---

### Post by spaceghoti on 2006-07-06
Oddly enough, Flash was working fine for me until I installed Swiftfox.  Now I can't make sound in flash work no matter what I try, although sound on the rest of my system works fine.

---

### Post by strabes on 2006-07-06
yay easybuntu works great!!! I had the same problem with youtube and I just installed easybuntu and restarted firefox and it works!!!

---

### Post by Miki01 on 2006-07-06
[QUOTE=strabes]yay easybuntu works great!!! I had the same problem with youtube and I just installed easybuntu and restarted firefox and it works!!![/QUOTE]
:o EasyUbuntu made everything worse for me x_x

---

### Post by poekie on 2006-07-23
> **Corvillus said:**
> The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.

I may sound very stupid, but how to apply this in kubuntu? System Settings does not have a preferences, I did find a sessions tab but that didn't let me enter any 'run on startup' things, other than those that were found by the system?

---

### Post by mockjules on 2006-07-24
Sad to say, Corvillus fix did not work for me. But kayrune's fix did! Some fixes seem to help others and some don't. What is even weirder, before the fixes there was no volume control on the videos. Now there is!

---

### Post by poekie on 2006-07-25
> **poekie said:**
> I may sound very stupid, but how to apply this in kubuntu? System Settings does not have a preferences, I did find a sessions tab but that didn't let me enter any 'run on startup' things, other than those that were found by the system?
Hmm.. I tried making a *.sh of the code you wrote, put it in ~/.kde/Autostart/ and made it executable, but that didn't work as well as I'd hoped to. I'm probably missing some commands for that to work or something?

---

### Post by poekie on 2006-07-25
Ok, maybe I was defeated too soon: it works. I used both kayrunes soultion and Corvillus's, and making an executable .sh file of the command works. Or something.
So I'm not really sure what did it but it worked, something of the above :P

---

### Post by lantuin on 2006-08-01
> **sugonaut said:**
> I had the same problem when I upgraded to 6.06.  Flash worked great, but without sound.  I did the following...

1. I installed the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox.

Hope this helps.

Oh, and some other details - I had previously installed 'flashplugin-nonfree'.  I'm not using the 'libflash-mozplugin' package.

This is perfect!!!

---

### Post by spiffytech on 2006-08-02
> . I installed the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox

This worked perfectly for me, but now Firefox is unstable. It frequently locks up if I go to another window and then back to Firefox.

---

### Post by sugonaut on 2006-08-02
> **spiffytech said:**
> This worked perfectly for me, but now Firefox is unstable. It frequently locks up if I go to another window and then back to Firefox.

What do you mean by, "go to another window"?  Another application window?  Is it only unstable when you view flash?  Or is it randomly unstable viewing plain 'ole HTML too?  Is it only when other application windows are open?

What is your Firefox version?  What version of Ubuntu?

---

### Post by spiffytech on 2006-08-03
> **sugonaut said:**
> What do you mean by, "go to another window"?  Another application window?  Is it only unstable when you view flash?  Or is it randomly unstable viewing plain 'ole HTML too?  Is it only when other application windows are open?

What is your Firefox version?  What version of Ubuntu?


I mean when I switch application windows. The only website that I have thusfar been able to associate with the lockup is meebo.com. I never had a problem with that site before making this change, though. I have not yet tested whether or not it happens with Firefox is the only program running.

I'm running Kubuntu 6.06.

---

### Post by sugonaut on 2006-08-03
> **spiffytech said:**
> I mean when I switch application windows. The only website that I have thusfar been able to associate with the lockup is meebo.com. I never had a problem with that site before making this change, though. I have not yet tested whether or not it happens with Firefox is the only program running.

I'm running Kubuntu 6.06.

Hey, cool site!

I dunno...I have my suspicions.  I'll spend some time at meebo and see if I get similar behavior.  I wonder if it's the flash code behind the chat client ditzin' out on you?  That thing is very "chatty".  Perhaps it's hogging some Firefox resources to do its job too.

Did meebo work fine prior to my rc hack?  Also - It looks like you can turn off the sound.  Does that make a difference in stability?  I'm just trying to narrow down the possibilities.

---

### Post by spiffytech on 2006-08-04
Yesterday, I used Firefox as the only program running for about fifteen minutes, and had Meebo active with the sound on, and had no problems. Today, I am running Firefox, among other programs, and I have Meebo sound turned off with no stability problems.

Meebo worked before I implemented your hack, but the sound didn't work. Neither did the sound in Flash either.

---

### Post by iced_cooly on 2006-08-06
thanks Corvillus, that worked perfectly for me, too!

---

### Post by cantormath on 2006-08-14
> **Corvillus said:**
> The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.

I just reinstalled flash, using automatix in fact, and the sound came back.

---

### Post by k9brand on 2006-09-02
> **sugonaut said:**
> I had the same problem when I upgraded to 6.06.  Flash worked great, but without sound.  I did the following...

1. I installed the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox.

Hope this helps.

Oh, and some other details - I had previously installed 'flashplugin-nonfree'.  I'm not using the 'libflash-mozplugin' package.

thank you! this worked for me

---

### Post by Dinerty on 2006-09-03
> **sugonaut said:**
> I had the same problem when I upgraded to 6.06.  Flash worked great, but without sound.  I did the following...

1. I installed the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox.

Hope this helps.

Oh, and some other details - I had previously installed 'flashplugin-nonfree'.  I'm not using the 'libflash-mozplugin' package.

Thanks mate worked great for me

---

### Post by cvmostert on 2006-09-04
> **BoneyOne said:**
> Sadly enough, none of the things listed here worked for me.

try these commands:
> 
:~$ sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
Password:
:~$ sudo mkdir -p /tmp/.esd/
~$ sudo touch /tmp/.esd/socket


it did the job for me...

---

### Post by vierranet on 2006-09-04
Dapper will at times drop the sound from Firefox & Flash, as always you need to search the forums before freaking out as someone has more than likely already experienced the problem and discovered a solution. 

this worked for me.

sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”aoss”

---

### Post by Miki01 on 2006-09-04
Sorry everyone. Unfortunately, none of the solutions in this whole thread worked for me...

---

### Post by kwilliam on 2006-09-04
Wow!  I was getting worried, as I kept trying all of these hacks mentioned here and none were working. I'd tried all but installing automatix, I think. But finally after applying the last one mentioned, it worked! I'll try applying the hacks in reverse order on my Kubuntu installation and see if I can figure out which one did it.

@ Miki01.  Do you have sound working in Ubuntu at all?  Meaning, can you play audio files in other programs, and therefore know your problem is limited to Firefox?

Edit: Ah, well, I tried applying the hacks in reverse order in Kubuntu and nothing worked. 
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket
sudo apt-get install alsa-oss
sudo kate /etc/firefox/firefoxrc
# Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss"
sudo ln -s /tmp/.esd-1000 /tmp/.esd
# Tried EasyUbuntu
``` Grr.
I can't wait till Adobe releases Flash 9 for linux. It's supposed to use ALSA instead of OSS. Maybe then we won't have all this trouble. I've love to be able to hear Google Video/You Tube in Kubuntu. But at least I've got it in Ubuntu now.

---

### Post by Malta Soron on 2006-09-07
> **strabes said:**
> yay easybuntu works great!!! I had the same problem with youtube and I just installed easybuntu and restarted firefox and it works!!!

Same for me :D

---

### Post by leader303 on 2007-11-14
none of these tips worked for me.
i remember sound worked in flash and firefox, when i used my onboard soundchip, but since compiling alsa drivers for my usb interface, it's over.
...any more ideas anyone?

edit:
one day later it (whatever this mysterious -it- has been) worked out. thanks to the originator of -it-.

---

