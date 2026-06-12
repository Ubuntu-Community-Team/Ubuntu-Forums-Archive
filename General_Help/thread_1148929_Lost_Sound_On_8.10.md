---
title: "Lost Sound On 8.10"
date: 2009-05-04
forum: General Help
---

### Post by Sabar on 2009-05-04
I have been running 8.10 since the release with no problems. Latly how ever my sound has been konking out. All volume is at 100% doesnt matter if it is on a web site like Amazon MP3 downloads or on Amarok (Running Amarok 2.0.1) 

Doesn't seem to be any hard ware problems because when I boot up Windows XP I have sound again. 

I helped the problem temporarily a few times by either 
1. rebooting. That worked one time.    
2. Changing the setting under System>Preference>Sound to OSS Open sound. That worked for a little bit (10 mins.)


I found a post that I think is kinda on this subject but not sure what all to try

[[COLOR="Blue"]Comprehensive Sound Problems[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+stops+working")

Typed: > aplay -l in terminal 

Responce:   > **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Typed:  > lspci -v

Responce:    Along with a bunch of other things 

        > 00:1b.0 Audio device: Intel Corporation 82801G     
        (CH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device 0303
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 50200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Typed:  > alsamixer 

Responce was a screen, and at the bottom it says 

> 100<>100
Master

So it looks like master volume is on. The volume knob at the top of the screen is at 100%. 

When I do try to play music or sounds I get a faint slight crackle from the speakers.

Should I do the part about puging drivers and things? what should I do now?

Thank you every one in advance

Sabar

---

### Post by trendal.toews on 2009-05-04
Are you saying the sound doesn't work or that is on 100% volume no matter what?

I got this off a different page.  But it was talking about a fresh install of 8.10.  Probably wouldn't hurt to try it but I am not super savvy at this so if it stuffs your system......ffft ffft  (the sound of me dusting my hands of the matter):)


Solution 1

sudo killall pulseaudio

sudo alsa force-reload

and then go to System>Preferences>Sound and change everything to ALSA

or

Solution 2

Try to uninstall pulse audio check here for [http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")

---

### Post by Sabar on 2009-05-04
The Sound is not working. all I hear from my speakers is a little static when something is supposed to be playing.

About the volume being at 100% I was just trying to show where all I had checked and what I had found. trying to help narrow down the issue quicker with any relevant info I could provide.

Under System > Preferences > Sounds.  If I change all setting to  OSS Open Sound system and hit test I get this error 
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

If I change to the other options like Pulse Audio then hit test all I get is a little very light static.

---

### Post by Sabar on 2009-05-04
Just tried something new with odd results. 

I turned Amarok 2 off, switched to OSS in sounds and did a test and it worked. is my problem amarok related then? should I remove it and try to get the older version back?

Sabar

---

### Post by trendal.toews on 2009-05-04
Well I googled that error and got this link.  

[http://ubuntuforums.org/showthread.php?t=827588]("http://ubuntuforums.org/showthread.php?t=827588")

Again not my experience but thought it might help.

I really don't know that much about Linux I just relentlessly browse the web until I solve my problem.  So if this doesn't work then I probably don't have any other advice because it would just be shooting in the dark and would probably only frustrate you.

Good luck, sorry I couldn't help

Edit:  If all else fails  [This Guy]("http://www.category5.tv/") has a ton of knowledge and should be able to help you.

---

### Post by Sabar on 2009-05-05
Amarok related? Maybe not

Went to synaptic removed Amarok from the computer.  Rebooted system.


When it came on I went to sounds and while it was still under oss I hit test. It worked. I then played a video clip I have that worked then I went to amazon and tried to listen to a music clip there. Nothing. 

Went back to sounds and hit test and got an error
> 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

I am really at a loss. everything has been running fine until lately. maybe one of the updates did something? I don't know 

Any ideas wound be appreciated
Thank you 
Sabar


Ok maybe Firefox is messing with something. I said above about trying to hear something on amazon. well after posting this I closed that browser window and opened Rhythmbox. and it played so I went back to sounds and hit test witch is still under OSS and that worked. Pulse audio is still giving light static.  

What is causing my problems here?

---

### Post by trendal.toews on 2009-05-05
So.... You have sound EXCEPT in firefox?  Or am I wrong?

---

### Post by trendal.toews on 2009-05-05
That error in your last reply,  part of it said this "Device is being used by another application"  maybe thats a clue.

---

### Post by Sabar on 2009-05-05
Yea I think thats a key to the whole problem. I just dont know what door the key fits. hell with my luck it goes to a locker.

that I think all my settings should be on pulse audio and nothing is working there. so driver issues now?  why would I have them after everything worked for so long?

---

### Post by trendal.toews on 2009-05-05
what happens when you reboot?  Does the sound work then?  If it does then what app kills the sound.

---

### Post by Sabar on 2009-05-07
I may have gotten the Problem fixed.  Found this post today.

[[COLOR="Blue"]HOWTO: PulseAudio Fixes & System-Wide Equalizer Support[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789578&highlight=Resetting+Pulseaudio")

I read down what all to do was getting ready to do it then reread one of the Note's. the post that I linked to in my origanal post said to put this into the terminal

> alsamixer

But this new post I was reading had this

> $ alsamixer -Dhw

With a note that said;

> Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

The part about specifying hardware device is what cought my eye.

So I put > alsamixer -Dhw into the terminal and I got a diferant  screen that came up and it did not say Pulseaudio on it this time. 

it has

> AlsaMixer v1.0.17

everything was at 100% except PCM. I have no idea what that is but when I turned that to 100% and went back to sounds changed everything to auto detect. (Think that's what this site said to do) and hit test IT WORKED! I got the annoying beeeeeeep. moved everything to pulse audio that worked also, then I moved settings back to auto detect opened Amazon  went to mp3 downloads and tried to hear a sample that worked also!

So right now I am cautiously saying I have the problem fixed. not sure if I want to mark it solved because I don't know what it was I did or what PCM, is or why it was zeroed out. But for now I think it is working. maybe :)

Thank you [COLOR="RoyalBlue"]KatmanHH[/COLOR] For sticking with me and trying to get me thrue this. I can not tell you how much I appreciate that. 

Later

Will post again if I was wrong about this working :(

---

### Post by trendal.toews on 2009-05-07
It looks to me like none of the suggestions I had really helped.  You got it figured on your own. :)

Really glad you got it though.  If it aint' something critical I enjoy fixing problems in Linux.  Just don't have a lot of knowledge yet.

---

