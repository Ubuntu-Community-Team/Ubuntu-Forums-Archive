---
title: "Vostro 1400 Hardy"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jasonlfunk on 2008-04-25
Congratulations Ubuntu Team. For the first time since I started using Ubuntu a few years ago, I installed Hardy and everything just worked. The video worked flawlessly, as well as the sound. The wireless worked with the Restricted Drivers manager using the bwf-cutter program, I did have to be connected via ethernet in order to download the right firmware.

I was very excited. Way to go ubuntu.

---

### Post by ayu on 2008-04-25
Hi. That's good news to hear. May I ask if you performed a clean install or an upgrade, 32bit or 64bit, and Gnome or KDE? Also, what video card and wireless do you have? Any problems with the audio or microphone? Does hibernate and suspend work (100% of the time)? Thanks,

---

### Post by kamaboko on 2008-04-25
> **jasonlfunk said:**
> Congratulations Ubuntu Team. For the first time since I started using Ubuntu a few years ago, I installed Hardy and everything just worked. The video worked flawlessly, as well as the sound. The wireless worked with the Restricted Drivers manager using the bwf-cutter program, I did have to be connected via ethernet in order to download the right firmware.

I was very excited. Way to go ubuntu.

Can you list the specs of your Vostro?

---

### Post by floyd4one on 2008-04-26
Hey all, 

I've been running 32bit Xubuntu Hardy (dual boot with XP Pro) on my Vostro 1400 since RC4 and everything important works great. My specs are

-Intel Core2 Duo T7500
-2GB RAM, 160GB 7200rpm HDD
-nVidia 8400GS 128MB, WXGA+ 1440x900
-Intel 4965 AGN Wireless
-Webcam (which works if you compile and install the uvcvideo module)
-Bluetooth (haven't tried), 8-in-1 Media Card Reader (haven't gotten to work yet)

I've installed the proprietary nvidia driver and have successfully run Compiz Fusion (though it was too groggy for my taste) without any problems. As was previously mentioned, the video works flawlessly with the open source driver as well and I am not running any other proprietary drivers (WiFi worked straight away IRC).

Also, the volume/mute keys work fine, but the media keys do not (no surprise there). And watch out for the Media Center key, it tends to cause problems if you have dual-boot XP (perpetual BSOD on boot, but pressing the Media Key again seems to fix itself).

Overall, I'm pretty pleased.

---

### Post by masum_habib on 2008-04-27
I have installed a clean Kubuntu Hardy on my Vostro 1400. It appears that the audio is not working. Can anyone please help me?

---

### Post by masum_habib on 2008-04-27
> **masum_habib said:**
> I have installed a clean Kubuntu Hardy on my Vostro 1400. It appears that the audio is not working. Can anyone please help me?

Hi,
I am glad to inform that I have got my audio card wording. I only added the following line at the end of my */etc/modprobe.d/alsa-base* file and reboot. 
**options snd-hda-intel model=dell-3stack**

For more information: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972)

---

### Post by crazyyguy on 2008-04-27
Hi all I am new to Ubuntu can any one tell me how to connect to wireless.What should I do to connect to wireless internet.

---

### Post by empty_tank on 2008-05-10
i have upgraded my vostro 1400n to hardy 2 weeks ago (from gutsy to hardy rc to final release 8.04) and I am very much satisfied with the results.

Except for a few tweaks (configuring pulse audio and making wifi indicator light up during connection), almost everything works:
the most significant improvement over gutsy is that the video card (intel 965) is no longer blacklisted; I can now use compiz, cairo-dock and screenlets.

I never had any problems with gutsy regarding:
- sound and volume control keys; use of 2 headphone jacks; use of external microphone
- brightness controls thru keyboard
- media card reader.  

The hardy upgrade however created some minor irritants:
- use of the 2nd headphone jack mutes the internal speakers. ( In gutsy, using the 2nd headphone jack did not mute the internal speakers but allow both the headphone and internal speakers to work - which is as it should be)
- the brightness controls thru the keyboard allows only for 3 settings. (During gutsy, I think it allowed for 6 more settings).

Overall, the hardy upgrade went well.  I am very pleased.  Congratulations to the ubuntu team for a job well done.  Thanks a lot!
 
I wonder what's in store for the next ubuntu 8.10 upgrade.  I can't wait!

---

### Post by leopinzon on 2008-06-07
> **empty_tank said:**
> i have upgraded my vostro 1400n to hardy 2 weeks ago (from gutsy to hardy rc to final release 8.04) and I am very much satisfied with the results.

Except for a few tweaks (configuring pulse audio and making wifi indicator light up during connection), almost everything works:
the most significant improvement over gutsy is that the video card (intel 965) is no longer blacklisted; I can now use compiz, cairo-dock and screenlets.

I never had any problems with gutsy regarding:
- sound and volume control keys; use of 2 headphone jacks; use of external microphone
- brightness controls thru keyboard
- media card reader.  

The hardy upgrade however created some minor irritants:
- use of the 2nd headphone jack mutes the internal speakers. ( In gutsy, using the 2nd headphone jack did not mute the internal speakers but allow both the headphone and internal speakers to work - which is as it should be)
- the brightness controls thru the keyboard allows only for 3 settings. (During gutsy, I think it allowed for 6 more settings).

Overall, the hardy upgrade went well.  I am very pleased.  Congratulations to the ubuntu team for a job well done.  Thanks a lot!
 
I wonder what's in store for the next ubuntu 8.10 upgrade.  I can't wait!

I have exactly the same problem. When I updated my Ubuntu from gutsy to Hardy, brightness keyboard control only work for 3 brightness level. Making a debug of the .sh that are called when de fn key+up/down interruption, it seems to be being called twice every time.

I have a Dell vostro 1400; video card: INTEL GMA X3100

---

### Post by amber_474 on 2008-06-08
> **masum_habib said:**
> Hi,
I am glad to inform that I have got my audio card wording. I only added the following line at the end of my */etc/modprobe.d/alsa-base* file and reboot. 
**options snd-hda-intel model=dell-3stack**

For more information: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972)

I upgraded from gutsy to hardy and sound wasn't working. The above solution worked for me. I am using a vostro 1400 with intel HDA/Sigmatel device. Thanks to Masum Habib.

---

### Post by jaxxa85 on 2008-06-10
> **floyd4one said:**
> Hey all, 

I've been running 32bit Xubuntu Hardy (dual boot with XP Pro) on my Vostro 1400 since RC4 and everything important works great. My specs are

-Intel Core2 Duo T7500
-2GB RAM, 160GB 7200rpm HDD
-nVidia 8400GS 128MB, WXGA+ 1440x900
-Intel 4965 AGN Wireless
-Webcam (which works if you compile and install the uvcvideo module)
-Bluetooth (haven't tried), 8-in-1 Media Card Reader (haven't gotten to work yet)

I've installed the proprietary nvidia driver and have successfully run Compiz Fusion (though it was too groggy for my taste) without any problems. As was previously mentioned, the video works flawlessly with the open source driver as well and I am not running any other proprietary drivers (WiFi worked straight away IRC).

Also, the volume/mute keys work fine, but the media keys do not (no surprise there). And watch out for the Media Center key, it tends to cause problems if you have dual-boot XP (perpetual BSOD on boot, but pressing the Media Key again seems to fix itself).

Overall, I'm pretty pleased.

Hi,

I am running exactly the same hardware specs and Vista. I'm having issues installing the nVidia proprietary drivers and getting the WiFi to work. I want to try the Compiz thing as well.
As you might've guessed I am completely new to Linux.
Any help would be appreciated.

Thanks

---

### Post by amber_474 on 2008-06-12
For nVidia drivers the easy way is 
to use envy. Please take a look at:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

And for WiFi, taking a look at Dell's Linux support might help. 

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

try 'lspci' command from a terminal and see whether the 
WiFi card is listed there.

Sorry, I am not good at other issues. Hope somebody helps with those.

---

### Post by jaxxa85 on 2008-06-13
Hi,
Thanks a million. I think I've figured out the graphics card drivers but I have a sound card problem now. There's no sound and the wireless isn't working.

---

### Post by amber_474 on 2008-06-14
For sound add the following line to the end of the
file: /etc/modprobe.d/alsa-base

options snd-hda-intel model=dell-3stack

---

### Post by spyder0080 on 2008-06-22
I'm having suspend problems. Sometimes when I come out of suspend, I get a blank white screen. I can move my mouse but there is nothing else I can do, so I am forced to log out by pressing ctrl+alt+backspace. I think the same thing happens when I come out of hibernation as well. Any ideas on what's going on and how to fix it? Thanks!

---

### Post by HydroModeler on 2008-06-22
spyder0080, when you get your white screen, just type your password and hit enter and it should log you back in.  i guess the log in screen is there but not showing (??).  still trying to really fix it my self but that works for me.

---

### Post by spyder0080 on 2008-06-22
> **HydroModeler said:**
> spyder0080, when you get your white screen, just type your password and hit enter and it should log you back in.  i guess the log in screen is there but not showing (??).  still trying to really fix it my self but that works for me.

Thanks, that works for me also! Until we get a proper fix then this will do. Thanks again!

---

### Post by piage on 2008-09-28
I have a Vostro 1400.... I installed Kubuntu Hardy. Sound didn't work, but I think the problem isn't driver or libs... I don't know why but every time I installed Kubuntu (3 times), when I open for the first time the audio mixer (not alsa mixer), front speaker was mute.

That's why sound doesn't work. I think when you add the line of alsa base, something put front speaker "not mute". But it's useless... just put "not mute" using audio mixer without changhing anything!

---

### Post by MiroNL on 2008-11-01
Total newbie here, switching over from Windows to Ubuntu forever.
I have Hardy Heron installed on my Vostro 1400 and this is a problem i have:
When i run Rythmbox music player everything is fine, sound works.
But, then i can't hear any sound when i want to watch something on Youtube.
I have to restart. Then the youtube video works with sound, but THEN my music players (Rythmbox, VLC, Audacious) don't work - they freeze up and i can't hear anything anymore after that.
I have to restart every time I want to listen to music.

SPECS:
Vostro 1400
CPU Intel T7100 duocore
2GB 667MHz DDR2 SDRAM
128 MB NVIDIA GeForce*8400M GS
Intel® Pro Wireless 3945 802.11a/b/g Mini-PCI Card EUR
Hard Drive 120GB Serial ATA (5400RPM)
Fixed Internal 8X DVD+/-RW Drive
2.0 MP cam

BTW: how can i use my webcam? how come Pidgin has no option for that?
Thanks in advance

M

---

