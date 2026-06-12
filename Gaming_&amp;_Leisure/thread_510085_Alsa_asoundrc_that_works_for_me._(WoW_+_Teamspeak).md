---
title: "Alsa asoundrc that works for me. (WoW + Teamspeak)"
date: 2007-07-26
forum: Gaming &amp; Leisure
---

### Post by chromerium on 2007-07-26
I've been having a horrible time getting audio to work. 

By default, the alsa-oss hack will work fine, if you just run that in front of wine and Teamspeak. But I found that it introduces far too much audio delay in WoW. Teamspeak I can deal with but spell cast sounds were starting nearly a full second after they started on screen ... really offputting.

So, I set out into the dark badly charted waters of ALSA asound configs and hacked and hacked until I got a config that worked.

For reference, this is my entry in lshw:

```

             description: Multimedia audio controller
             product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
             vendor: VIA Technologies Inc.
             physical id: 6
             bus info: pci@05:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ICE1724 latency=32
             resources: ioport:a000-a01f ioport:a400-a47f irq:21

$ cat /proc/asound/pcm
00-02: ICE1724 Surrounds : ICE1724 Surround PCM : playback 2
00-01: IEC1724 IEC958 : IEC1724 IEC958 : playback 1
00-00: ICE1724 : ICE1724 : playback 1 : capture 1

```

So, I have one device on the card that can do playback & capture, no surprises there.

After hacking around, I came up with this:

```
pcm.card0 {
        type hw
        card 0
	device 0
        mmap_emulation true
	nonblock yes
	rate 44100
}

pcm.!default {
        type plug
        slave.pcm "duplex"
}

pcm.duplex {
        type asym
        playback.pcm "dmixer"
	capture.pcm "dsnooper"
}

pcm.dsnooper {
	type dsnoop
        ipc_key 4096
        slave {
                pcm "card0"
                format S32_LE
                period_time 0
                period_size 1024
                buffer_size 8192
                rate 44100
		channels 32
        }
        bindings {
                0 0
                1 1
        }
}

pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
                pcm "card0"
                format S32_LE
                period_time 0
                period_size 1024
                buffer_size 8192
                rate 44100
		channels 32
        }
        bindings {
                0 0
                1 1
        }
}

ctl.dmixer {
        type hw
        card 0
        device 0
}
```

What happens here is we define the base hardware entry that all our programs will access. Thats the pcm.card0 entry.

Then, we want to define the default pcm device that all ALSA applications that havn't been explicitly configured to use something else will use. This is pcm.!default. Don't ask me why.

The pcm.!default entry is just a plug that takes all access and routes it to it's slave called "duplex". Why don't we just make pcm.duplex the default? Doesn't work. Try it. It'll hate you. I don't know why; ALSA is just stupid that way.

pcm.duplex's job is to provide a device that applications can use to record and playback audio from. It doesn't do any mixing; thats the job of dsnoop and dmix.

pcm.dsnooper allows multiple applications to record from the device. Because other applications would otherwise block access to each other depending on the order that you start them, you need this.

pcm.dmixer does the same for output.

Note there isn't an OSS thingy. We don't need one. By default, Fiesty's version of ALSA will create one if you load the module, and it'll use pcm.!default. Don't create one unless you need to; it didn't work for me. Besides, both Teamspeak and wine applications will be using ALSA.

This all worked for me, but YMMV. I don't really understand ALSA. It's possibly the worst part about linux right now, and deserves to be shot in the head. This stuff should all just *work* with NO CONFIGURATION by the user. I also shouldn't have to use aoss to fix things broken old apps. The OSS emulation should be better.

I force everything to 44100 because I don't want alsa to be doing rate conversion. This adds delay.

Period size and buffer size need to be powers of 2. They also should be generous; they don't affect latency at all.

mmap_emulation does effect latency but if you turn it off TeamSpeak won't work.

Run TeamSpeak using the aoss wrapper. Should work fine with the default /dev/dsp selected in the settings.

Run winecfg and tick ONLY the ALSA drivers. Emulation should be turned off, Hardware Acceleration should be set to Full. Default Sample Rate of 44100 and Default Bits Per Sampe of 16.

I'm currently testing the following in WTF/Config.wtf

```

SET SoundOutputSystem "1"
SET SoundBufferSize "64"
SET SoundNumChannels "128"

```

Setting the SoundBufferSize directly affects the latency in game. Really small numbers seem to cause a fair bit of crackling, which is unsurprising. Perhaps renicing wineserver or the app pid can alleviate this, or running realtime scheduler patches. I'm hoping that the upcoming completely fair scheduler will help with this, but its just a guess.

Start WoW without aoss, and it should just work, without the horrible latency that aoss adds in. Start Teamspeak alongside it (with the aoss wrapper) and you should be able to confirm its workign properly by doing a local test.

Like I say above, YMMV, but hopefully this helps someone else out there. None of the asoundrc files that are out there worked for me; if you just edit the pcm.card0 device numbers, you can probably get it to work fine with any other card out there. There is probably a way to make this asoundrc work with anything actually; there are default pcm devices defined for the hardware. But I wanted to force the rate, so meh.

I hate ALSA. I hope it dies. Horribly. In a fire.

---

### Post by blue_puyo on 2008-02-18
I can't believe it. This configuration file you've posted makes it NEARLY WORK.

This is the closest I've come to beating alsa. Thank you.

For me, this all works *except* that wine still blocks audio for other applications, whether I use aoss or not. :-(

But if not running wine, I can use teamspeak and play music at the same time. :D *chuffed* Just need to figure out why wine is blocking and I might be totallly solved.

---

### Post by blue_puyo on 2008-02-18
Okay. I have all 3 apps (teamspeak, wow and amarok) working together.

I threw this on the end of ~/.asoundrc although I'm not sure if that's what did it

```
pcm.dsp0 {
    type plug
    pcm "card0"
    nonblock yes
    mmap_emulation true
}

```

I think the real win was when I configured wine using winecfg to use OSS instead of alsa and running it via "aoss wine WoW.exe -opengl". I don't have the sound latency problems you were having with aoss.

I'm just guessing my way through all of this because none of it makes any sense to me. ;-) If I refine it I'll post more here.

---

