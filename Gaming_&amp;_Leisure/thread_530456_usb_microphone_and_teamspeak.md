---
title: "usb microphone and teamspeak"
date: 2007-08-20
forum: Gaming &amp; Leisure
---

### Post by cameran on 2007-08-20
does anyone here have experience with a usb microphone (logitech) and teamspeak?  i am having a lot of problems getting it to work

i can get teamspeak to work with my microphone if i use the windows version of teamspeak through cedega but using the native linux version doesn't work

any help would really rock.  i spent 12+ hours yesterday on it and no luck :(

---

### Post by jnorthr on 2007-08-20
For what it's worth - i never could get my usb microphone to work so i found an old one with a micro-jack and used that ok.

---

### Post by Deived on 2007-09-01
I was able to get it working by changing the sound driver to /dev/dsp1.  This was with a standard Logitech headset.  One that came with Socom on PS2 (I'm so cheap)

---

### Post by unc0nn3ct3d on 2008-08-26
[http://blog.netflowdevelopments.com/2009/02/25/setting-up-a-usb-mic-to-work-with-ubuntu-and-specifically-teamspeak/](http://blog.netflowdevelopments.com/2009/02/25/setting-up-a-usb-mic-to-work-with-ubuntu-and-specifically-teamspeak/)


Wow, after spending hours and hours looking for this solution, then giving up, then trying again then giving up it is a done deal.. I can't believe I am actually able to use TS now in linux.

First of all you need to run the windows version of TS through WINE as the linux version is a complete POS and has zero support for USB mics and you may as well give up now before wasting the days that I have.

So get WINE installed if you haven't already
then go and download the windows version of TS2 and install it through Wine

Now from this point onwards I am going to assume you are using ALSA , if not then you have your own google adventure to go on.

So:

go into your home directory (cd ~) and create a file called ".asoundrc" minus the quotations of course with your favorite editor ( vi ./.asoundrc )
The .asoundrc file in your home directory acts as kind of a configuration file that is used to override default settings
Our goal here is to make our default capture device our USB mic and NOT our sound card, this is accomplished by inserting the following text into the .asoundrc file:

pcm.!default {
        type asym
        playback.pcm {
                type plug
                slave.pcm "hw:0,0"
        }
        capture.pcm {
                type plug
                slave.pcm "hw:2,0"
        }
}


something to note: "hw:0,0" and "hw:2,0" are MY card locations for my soundblaster and my usb mic, yours might be different.  

In order to find out what your desired output device is you type the following in terminal:

"aplay -l" and you should receive and output something like this:


**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Obviously My card is 0 as that is the only one that shows up, so I use "hw:0,0"

now to find my capture device I type:
"aplay -l" and my output should be something like this:
**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now we already know that Card 0 is my soundblaster, which I don't want to use, so we can rule that out.. The only other option(which is conveniently labeled USB Audio) is Card 2 so that means I used "hw:2,0" .  Yours could be different so edit your .asoundrc file accodingly. 

I quickly checked to make sure WINE was seeing my usb mic by running the command 'winecfg' and going into Audio and seeing the ALSA WAVE IN device show up as USB Audio.  

I have Hardware Acceleration set to Emulation as well as Driver Emulation checked on, not sure if it matters but it is on for me and works.

Now this is literally all I needed to do. Much to my complete shock I can now run TS2 (windows version) through WINE just fine and dandy.  You have no idea how much mucking about I've done with my system just to find out this was the easy fix.. I hope this helps someone else out there and saves them the time and energy.

cheers

---

### Post by flickerfly on 2008-10-13
To hear things:
Settings -> Options -> Sound Driver -> Other to /dev/dsp1

To say things:
Setting -> Sound Input/Output -> Push to Talk and set that to something.

I also had to change the default source for PulseAudio. I'll leave you to figure out how to do that. It isn't something straight forward.

That's all I had to do.

---

