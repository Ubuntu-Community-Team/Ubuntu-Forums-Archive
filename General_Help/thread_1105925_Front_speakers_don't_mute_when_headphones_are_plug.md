---
title: "Front speakers don't mute when headphones are pluged in"
date: 2009-03-25
forum: General Help
---

### Post by cayt on 2009-03-25
Hi everyone,

I have switched to Ubuntu the day before from vista and I got my first problem:) When I plug my 2.1 speakers in the headphone output of my laptop, the front speakers on the laptop don't mute. In other words, I have sound from both laptop speakers and 2.1 speakers.

I tried the headphone switch in the volume control but doesn't work. When I uncheck the headphone switch box the 2.1 speakers don't work as expected. However, when I check it both speakers work.

I hope one of you have the answer.

Thanks.

---

### Post by KCG102282 on 2009-03-25
Mute the sound from the front speaers when you have your headphines pluged in

---

### Post by cayt on 2009-03-25
> **KCG102282 said:**
> Mute the sound from the front speaers when you have your headphines pluged in

It is very wise but I am looking for a technical answer if there is any. In vista it mutes the front speakers automatically when the user plugs extra speakers in. I am sure and I hope ubuntu has the same property.

---

### Post by Lunx on 2009-03-25
I have exactly the same problem on my machine (desktop pc). I get sound from both headphones and speakers and no muting/activating any setting will sort it out. For example, if I mute **Front**, then my headphones also stop working. The only other setting that does anything is PCM-2 and that simply turns off headphones and has sound still coming from main speakers. I posted a thread on this a while back but sadly no-one responded.

[http://ubuntuforums.org/showthread.php?t=1052116](http://ubuntuforums.org/showthread.php?t=1052116)

---

### Post by minimec on 2009-03-25
Hi

Starting with Ubuntu Hardy Heron, the pulseaudio server is used to manage all the sound, coming from your different applications. So in gstreamer-properties and in gnome-volume-control, the settings are on 'default' or 'pulseaudio'. 

You're talking about the 'Jack Sense' option. You can normally activate that function in the alsa settings of your soundcard.

In your case, open the gnome-volume-control. Then change the device to "YOURSOUNDCARD (Alsa Mixer)" (Menu File >Change Device for Hardy Heron). In my case that would be "SB Live 5.1 (Alsa Mixer)" If you are lucky, you should now have a 'Jack Sense' Option in the subfolder 'Switches'. If there is nothing like that go to the >Edit >Preferences Menu and activate it. 

Having done that, change the device back to the settings you had before (probably something with pulseaudio). 

Having done that verify that you have pavucontrol installed. 'sudo apt-get install pavucontrol'. With pavucontrol you can handle all outgoing traffic (sound) and route it to the speakers you want. I mean, it's a server... :) You could even route it to your girlfriends computer if she has a OS with activated pulseadio server...

That should be it...

Minimec

---

### Post by perhaps_cz on 2009-03-25
i also have a same problem. Dont know how to solve it:(

---

### Post by perhaps_cz on 2009-03-25
2minimec: your post didnt help.

---

### Post by minimec on 2009-03-25
@perhaps_cz

Ok. I verified my post above with my laptop. If the card is recognized correctly, then the 'Jack Sense' in the alsa settings is working.

As you checked that too, I would verify that your card is installed correctly.

Do the following:

in a Terminal: 

dmesg | grep audio    # See the results


What kind of card/chip do I have?

lspci | grep audio   # Gives you Infos about PCI Cards and some SoundChips

In my case:
02:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

>> Google: Creative Labs SB Live! EMU10k1 (rev 07) ubuntu

Some internal chips are recognized as USB Device, so...

               lsusb   # Check your devices with google

In my case:
Bus 002 Device 002: ID 0d8c:0201 C-Media Electronics, Inc.

>> Google: 0d8c:0201 C-Media Electronics ubuntu


Cheers Minimec

---

### Post by cayt on 2009-03-25
@ minimec

As I have Ubuntu 8.10 your first suggestion didn't work. I guess the menus are different. To open the gnome-volume-control I double click the "volume item" in the panel and the "switch" tab only has "headphone" option, which doesn't work.

About your 2nd suggestion; I wrote the code in terminal, however I didn't get any result or information about my sound card. I guess our suggestions only work for ubuntu 8.04. If you have any idea about 8.10 that would be great:)

Cheers

---

### Post by minimec on 2009-03-26
@ cayt

Unfortunately I have no other ideas. I guess that the alsa version in Ubuntu 8.10 (my laptop is on 8.10 too) is not working correctly with your soundchip. So it's probably a bug in alsa with some soundchips.

As this 'bug' is very annoying for you (I guess), I would try a Jaunty Jackalope (9.04) Live-CD and see, if the problem persists. If it works, that would give you the possibility to upgrade to 9.04 in a few weeks, or even now (9.04 beta is arriving soon). 
Link: [http://www.ubuntu.com/testing/jaunty/alpha6]("http://www.ubuntu.com/testing/jaunty/alpha6")


Next step would be the Ubuntu 8.04 LTS Live-CD. Unfortunately that would mean a clean install, if you had to replace 8.10, as an distro-downgrade is not possible.

---

### Post by Lunx on 2009-03-31
> **minimec said:**
> @ cayt

Unfortunately I have no other ideas. I guess that the alsa version in Ubuntu 8.10 (my laptop is on 8.10 too) is not working correctly with your soundchip. So it's probably a bug in alsa with some soundchips.

As this 'bug' is very annoying for you (I guess), I would try a Jaunty Jackalope (9.04) Live-CD and see, if the problem persists. If it works, that would give you the possibility to upgrade to 9.04 in a few weeks, or even now (9.04 beta is arriving soon). 

I can confirm that problem persists in 9.04 :(

Your suggestion of a bug in alsa with certain chips seems to be on the money, judging by a particular paragraph I read in the Tutorials and Tips forum earlier today

> []b]Hardware[/b]
At the bottom is the hardware, usually a sound chip on the motherboard. While only a few basic chips are generally used, OEMs have great latitude in configuring them. both physically and in the software/firmware that interfaces the chip to the operating system. For example, some manufacturers decide to have two microphone jacks on their machines, one in front, one in back, others reconfigure the input and output ports. so maybe the line in becomes the side or lfe output for surround sound. Sometimes they do this within the same model of a computer. 
Needless to say, this has created widespread confusion among users and the driver writing community.
Quoted paragraph came from this thread

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

My machine is OEM so could well be cause of my dramas (not for too much longer I hope, planning on building myself a new box in very near future).

---

### Post by minimec on 2009-03-31
Hi Lunx

>I can confirm that problem persists in 9.04
Well this is bad news for you I guess.

But at least I can propose you a solution to get around your problem. There is a nifty piece of hardware called "Premium Notebook Headset" by Logitech [http://www.logitech.com/index.cfm/notebook_products/pc_headsets/devices/223&cl=au,en"](). The interesting thing with that baby is, that you can plug it with an USB-Adaptor, or with the 'normal' 3mm headphone jack. When you plug it with the USB-adaptor, the headset is recognized by Ubuntu as a 2nd soundcard, and that enables you to switch devices with 'pavucontrol', as all the sound of your machine is probably handled by pulseaudio. So you would be able to redirect the sound directly to the 'headset-soundcard', bypassing the notebook soundchip. I guess you now what I mean. In fact, the only thing you need is this Analog-to-USB Adaptor. I guess other manufactors have such kind of adaptors too.

This would be my solution (as I am a proud owner of one of these headsets and a Logitech geek).


Cheers minimec

---

### Post by ron_o on 2009-04-27
I solved the problem on my computer. YMMV. 

On my mixer I have only MASTER, PCM and SURROUND showing and under 'switches' I have headphones shown and checkmarked. I got sound on my speakers too until I muted SURROUND fully, with a click and a red checkmark through it showing. Even when I reduced the SURROUND bars to its lowest setting I still got sound out of my external speakers until I muted it. 

On this computer SURROUND has always controlled my externel speakers. That's where your situation will be different I am sure. Just make sure you mute what controls your external speakers.

BTW, I got some things really screwed up. Don't know how, but after trying several different mixers and combinations, everything got so messed up I just restarted my entire computer, but an x restart probably would have done. 

I'm using Xubuntu 9.04 with gnome applets on my panel through xfapplet, an applet that allows me to use gnome applets on my panel. Xubuntu no longer has one for instant volume control. Go figure. 2 steps forward, 1 step back. :/

Ron.

---

