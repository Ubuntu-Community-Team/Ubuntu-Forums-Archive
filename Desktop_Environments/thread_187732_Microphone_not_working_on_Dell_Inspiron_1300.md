---
title: "Microphone not working on Dell Inspiron 1300"
date: 2006-06-03
forum: Desktop Environments
---

### Post by zaiyon on 2006-06-03
The named notebook comes with a microphone connector.

Sound generally works great, I have no problems at all.

But I cannot get the microphone to work. I unmuted and maxed everything I could find in alsamixer and tried several programs:

gnome-sound-recorder
audacity
skype
tapioca

None of em has any sound. I cannot hear myself when speaking into the microphone though I maxed everything. 

This is was lspci says about the soundcard:
```

0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

```

---

### Post by marmux on 2006-06-05
Hi,
I have the same laptop and the same problem. I had some little improvement after installing the last alsa drivers (now 1.0.11) and using the version of /etc/asound.conf posted below (unfortunately, I don't remember where I found it)
The microphone is now doing something, though the volume is very low and hardly usable.
```

#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type softvol
	slave.pcm {
		type hw
		card $CARD
		device 0
	}
	control {
		name "PCM Playback Volume"
		card $CARD
	}
}	

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			type softvol
			slave.pcm {
				@func concat
				strings [ "dmix:" $CARD ]
			}
			control {
				name "PCM Playback Volume"
				card $CARD
			}
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dsnoop:" $CARD ]
		}
	}
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Playback Default"
				lock true
				preserve true
				value [ $AES0 $AES1 $AES2 $AES3 ]
			}
			{
				name "IEC958 Playback Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
	capture.pcm {
		type hooks
		slave.pcm {
			type hw
			card $CARD
			device 1
		}
		hooks.0 {
			type ctl_elems
			hook_args [
			{
				name "IEC958 Capture Switch"
				lock true
				preserve true
				value true
			}
			]
		}
	}
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type hw
	card $CARD
	device 6
}


```

---

### Post by zaiyon on 2006-06-06
I just tried your asound.conf out blue eyed as I am and now it actually works!
I didn't even have an asound.conf file to begin with.

But as you told, the volume is pretty cheap - it's actually impossible to hear me talk.

Please tell me if you find a way to do this more beautifully, I will do so too of course.

<edit>
I just figured out that I cannot control my microphones volume, the volume I hear my own voice when talking ("screaming" does fit better atm, since it's so low-volume) via any alsamixer frontend.

This is frustrating.
I really think this asound.conf file could use some adjustment by someone who actually understands this, who could probably assign the microphone to the according alsamixer just fine, I'm looking forward for help, since I really want to do some voip with this notebook ;).
</edit>

---

### Post by marmux on 2006-06-07
Hi,
I had a look in the wiki at
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")
and edited my [COLOR="Red"]/var/lib/alsa/asound.state[/COLOR] file as explained there in the "Software Mixing" section.
I could not understand what this file does (hoped it would modify the alsamixer controls but sadly it's not the case...), but it seems to me that my mic is now recording a bit louder. Still crappy, but a bit louder.
Let me know if you have the same impression. Maybe I am allucinating.

ciao

---

### Post by zaiyon on 2006-06-07
Hm, I think it just sounds equal crappy and faint as before.

I removed the /etc/asound.conf and tada -> nothing changed.

So one of this solutions is not necessary, since one of it and two at the same time seem to do nothing different at all for me.

---

### Post by el.tomo on 2006-09-29
Hi

I have the Dell Inspiron 1300 as well and had the same problem. 

Try this, it works:

[http://www.ubuntuforums.org/showthread.php?t=201887](http://www.ubuntuforums.org/showthread.php?t=201887)

Cheers tomi

---

