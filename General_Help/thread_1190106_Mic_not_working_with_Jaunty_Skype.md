---
title: "Mic not working with Jaunty Skype"
date: 2009-06-17
forum: General Help
---

### Post by sarel29 on 2009-06-17
Hi, 

I can't get my microphone to work with skype in Jaunty. I've changed all the audio settings on skype itself to pulse, and I've checked the system sound settings which are also all on pulse except for Default Mixer which is set to my sound card (Intel82801DB-ICH4 Alsa Mixer).  It's very frustrating as I can hear people perfectly when they call me, but nobody can hear me.

Any suggestions welcome.

Thanks.

---

### Post by sigixv on 2009-06-17
in my setup the "sound in" is set to hardware (hw:Intel,0) ; the others to pulse. That's the only setting that seems to be working for me.

---

### Post by sarel29 on 2009-06-18
Thanks, I tried doing that but then when I did a test call on skype it cut off because of "problem with audio capture".  The only way I can get skype to work at all is by having all the sound settings as pulse.  Does it make a difference that I'm using a plug-in headset?

---

### Post by sigixv on 2009-06-18
What happens if you either use the option "(plughw:Intel,0)" or "headset" for sound in? (leave the other 2 to pulse)


EDIT: make sure you connected the headset...

---

### Post by sarel29 on 2009-06-18
The plughw and headset options don't work at all - I have the same problem of the call being dropped because of a "problem with audio capture".  I also have four options which are hw82801DB-ICH4 and with those I can do the test call but I still have the same problem of not hearing what I say.

---

### Post by Chronon on 2009-06-18
I had a problem in the past of having to choose which ports the input sources connect to.  Make sure your input sources in KMix are set to the right connection (e.g. Front Mic) and also set to capture.

---

### Post by sigixv on 2009-06-18
also check if no other program is using the microphone input when running skype.

I've made a video-tutorial once and was a bit boggled when skype didn't work. Turned out that it just failed because the video was consuming the mic...

---

### Post by sarel29 on 2009-06-19
Hi, thanks for the suggestions but it's still not working.  I'm using gnome at the moment (on a laptop which only has one place to plug in a mic).  One thing I've noticed though - when I open up the volume control and go to the "recording" tab, there's s slider for a speaker and microphone.  Whatever these are set to when I open up skype, as soon as I connect to a call, both sliders go to minimum and I can't move them.  Does that make any sense to anyone?

---

### Post by spraff on 2009-06-24
I've had exactly this problem and just figured it out -- even though the mic is going into the 3.5mm jack, Skype thinks it's "USB camera (hw:camera,0)" but this option will yield a "Problem with audio capture" unless you open kmix, uncheck "Capture" at the sound card, then go to the USB camera tab and check "Capture" on the mic channel.

What's frustrating is that "Pulse" is not an option in System Settings/Multimedia/Audio Capture (since it's pulseaudio that should be responsible for organising input from mic/camera/wherever) which is presumably why setting "pulse" to everything in Skype doesn't work -- there is no pulseaudio route for audio capture.

---

### Post by iponeverything on 2009-06-24
Interesting solution, thanks for sharing.

---

### Post by sarel29 on 2009-06-24
Thanks for the suggestions.  I tried it but I don't seem to have the option for USB camera so I'm still searching for solutions.....  I think the fault lies more with the sound settings somewhere though because I can't get the mic to work with Ekiga or even with Sound Recorder.  Everything is on max volume and unmuted, but still no luck.

---

### Post by swappa on 2009-07-06
Having somewhat the same issue. Initially I had no sound in my Mic at all.
Did the follwing:

* killall pulseaudio
* sudo apt-get remove pulseaudio
* sudo apt-get install esound
* sudo rm /etc/X11/Xsession.d/70pulseaudi


[http://boostmyworld.wordpress.com/2009/05/...4-got-no-sound/](http://boostmyworld.wordpress.com/2009/05/...4-got-no-sound/)

..and things got better but still crap compared to Windows/MAC. My sound is breaking up all the time. I have no problem hearing people, but they can only partially hear me. This is a deal breaker for me. I cant switch to Ubuntu on my work PC unless Skype works 100%. We are  using skype for phone meetings all the time. God damn....so close. 

Why is all this small stuff so much harder on Linux? Why cant stuff like this just work?

---

### Post by joel_gil on 2009-07-12
I have the same issue
I am using Jaunty, the 2.0.0.72 version of skype for ubuntu and i have a reagular plug-in headset (no usb)

As some of the people before I've tried every configuration and either I  make the call and I can hear them but they never can hear me, or the call simply won't connect because of "audio problems"

I am sure I have everything correctly pluged-in, same laptop (inspiron 6400) and same headsets as in intrepid where skype worked "fine"

Has someone already solved this issue and cna you tell us how?
Thanks in advance

---

### Post by Rofko on 2009-07-12
I have this problem also. I have been messing around with audio settings for hours, on and off, to no avail. This is a huge problem.

---

### Post by Westmeath on 2009-07-12
I also am having the same issue with the microphone not working in Skype. It is a real dealbreaker for some users.

Is this a Skype issue or a Pulse audio conflict issue? Or is it something else?

I don't remember having this problem under Intrepid - did a number of installs on different machines.

---

### Post by swappa on 2009-07-13
From what I hear; sound on Linux in general is currently a mess. Don't know if this is because of Pulseaudio or something else, but since  things in my case improved by removing Pulseaudio I am thinking that this is where improvement is needed. Maybe a total rewrite of the whole sound layer(s) should be on the top of the to do list for the developers.  I mean; spending two days on making your microphone work? How the hell can something that should be the easiest thing in the world be so hard....beats me. Like I say, cover the basics first. I can live without the fancy "nice to have's" as long as the basic functionality is there and is working. 

My two cents anyway.

---

### Post by MrSnowmiss on 2009-07-21
> **spraff said:**
> I've had exactly this problem and just figured it out -- even though the mic is going into the 3.5mm jack, Skype thinks it's "USB camera (hw:camera,0)" but this option will yield a "Problem with audio capture" unless you open kmix, uncheck "Capture" at the sound card, then go to the USB camera tab and check "Capture" on the mic channel.

I'm still having problems with my mic too. So after reading all kinds off solutions I thought this might be the one, but unfortunatly not.

I unchecked the Capture at all three soundcard options (Kmix)
But I can't understand about which USB Camera tab you're talking.

BTW my video test is working in skype.

[QUOTE=swappa]
* killall pulseaudio
* sudo apt-get remove pulseaudio
* sudo apt-get install esound
* sudo rm /etc/X11/Xsession.d/70pulseaudi[/QUOTE]

Unfortunatly this didn't work either :(

I found out that my mic isn't working at all. Installed Gnome soundrecorder and it says *Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu.* when I start it.
But when I go to Systems Settings - Multimedia (Kubuntu 9.04) I see my HDA Intel (198x Analog) which tries in order

ALSA: x-phonon:CARD=0,DEV=0
ALSA: plughw:CARD=0,DEV=0
OSS: dev/audio
OSS: dev/dsp

Any suggestions?

---

### Post by nbvarun on 2009-08-30
I have a hpdv6000. Had similar problems but started working after following steps to remove pulse audio and then volume control options - set to front mic. This is the last thing I remember doing after which mic started working in skype.

---

### Post by P4man on 2009-08-30
FWiW, I noticed a new version of skype on their website today. it only took them 2 years (!) to produce a minor update, but it (finally!) does support pulse audio.

It got my mic working on my acer laptop.

---

### Post by sqlpython on 2009-10-23
This can be fixed .... at least for my USB Camera/Mic

 I have a new 9.04 amd64 install kernel 2.6.28-11-generic
Running the static Skype kype_static-2.1.0.47
I see this has been a problem since Jan 09 tracing back many internet posts......
Seems neither Ubuntu nor Skype is addressing the issue ..or at least has not fixed it in 11 months..Yikes.
I have a plugin camera
Bus 001 Device 002: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks
and the only way I could get this to work is with an assignment like such to run skype
PULSE_SERVER=192.167.4.105 /home/sqlpython/skype/skype
.........
 The only problem would be is that with my roving laptop I would have to continually modify the ip address depending on WiFi hookup or Cat etho direct connect...
So I wrote a Bash to identify the IPaddress and run the Skype command based on the existing connection and inserting correct IPaddress as a variable..........
 Here is the Script but it does Not fix the Fact the I can not Play back any sound While Skype is connected VOIP to any other Person....
Please Fix it!!!!!
  This does not happen in my 8.04 install I get Sound Play Back with 8.04 while Skype Connected.

..

#!/bin/bash

ifconfig wlan0 | grep "inet addr" | cut -d: -f2 | cut -d" " -f1 $1
ifconfig eth0 | grep "inet addr" | cut -d: -f2 | cut -d" " -f1 $2
if [ $1 -gt $2 ]
  then
echo $1
PULSE_SERVER=$1 /home/sqlpython/skype/skype
fi
if [ $2 -gt $1 ]
  then
echo $2
PULSE_SERVER=$2 /home/sqlpython/skype/skype
fi

---

