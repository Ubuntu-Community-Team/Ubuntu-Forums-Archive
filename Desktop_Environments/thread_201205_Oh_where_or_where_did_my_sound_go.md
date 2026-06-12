---
title: "Oh where or where did my sound go?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by irv on 2006-06-21
I have a problem that just started a few days ago. I lost my sound. I have three PCs running Ubuntu 6.06 and this is the only one that has no sound. It was working for months now and I am not sure if something got turned off or what?
It is not hardware because if I boot into another OS I have sound. It has to be a setting somewhere in Ubuntu. I checked my Master Mono: and it saids it muted when it set to high (the +) and when I bring the slider down to (-) it says 100%. It seem to be backwards. I tried it both ways and I still do not have sound. In the volume Control I am using the right driver. (Sis S17012 Alsa mixer) with the master set.
Dose anyone have any idea what else I can check?

Edit: I also checked my "Multimedia Systems Selector and it is set to on Autodetect (Default Output Plugin) and if I do a test I get no sound. Also my Default Input Plugin is (ALSA - Advanced Linux Sound Architecture) and if I do a test I get no sound also.

---

### Post by irv on 2006-06-21
Hay, anybody out here got any ideas what to try?
Thanks

---

### Post by irv on 2006-06-21
I did a "lshw" and got:
> *-multimedia
             description: Multimedia audio controller
             product: Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:e800-e8ff ioport:ec00-ec7f irq:201

So I know ubuntu is seeing my sound card.
I am still wating for someone to let me know is there is something else I can try.
Thanks

---

### Post by irv on 2006-06-22
After going through a large number of thread on sound problems I find many out there with these same types of sound problems. (A lot of questions but not many answers). Well I got some of my sound working, and I believe I am getting to the bottom of many of the problems out here. Let me tell you what I did and what I found.
First, I thought my problems started when I did the last update and the kernel was changed. I rebooted the machine and went back one kernel (vmlinuz-2.6.15-23-386). We are at vmlinuz-2.6.15-25-386.
I now have sound working in XMMS player. My master sound controller is still working backwards. If I move the slider up (+) it has lower sound and down (-) it has louder sound.
I don't know what was changed in the last kernel update, but what ever it was it broke my sound. I hope someone fine out what was changed because I believe if it broke my sound it might have broke sound for others also.
It appears from all the post our here there is a serious problem with sound in Ubuntu Linux, and especially Dapper 6.06. I know some problems are because of codec's and such, but there seems to be a problem with many sound cards, and that is because of vendors not giving us Linux users the right drivers for our hardware. Maybe with time that will change. I posted this last post on this thread in hopes others will fine this informative and answer some of the question they might have on sound issues.

---

### Post by Blind-Summit on 2006-06-22
I'm having many sound issues. Ubuntu sees my soundcard, but I want all audio going via SPDIF to my amplifier. I too can get XXMS audio just fine, but DVDs play all choppy (audio only, the video is fine) and also, the card changes from hw0,2 to hw1,2 sometimes. It seems everything I try and install is a struggle on Ubuntu. I am beginning to think windows isn't so bad afterall.

---

### Post by irv on 2006-06-22
[QUOTE=Blind-Summit]I'm having many sound issues. Ubuntu sees my soundcard, but I want all audio going via SPDIF to my amplifier. I too can get XXMS audio just fine, but DVDs play all choppy (audio only, the video is fine) and also, the card changes from hw0,2 to hw1,2 sometimes. It seems everything I try and install is a struggle on Ubuntu. I am beginning to think windows isn't so bad afterall.[/QUOTE]
I really like using Linux (Ubuntu 6.06) and never really want to go back to windows, but I still keep a duel boot system because of issues like this (sound, etc). The mulitmedia issues need to be address in Linux in a big way. I am hoping the the next release of Ubuntu comes up with some good answers to these problems. I find everything else works for the most part.
Maybe the sound issue will not be a problem for me soon, I am almost deaf because of ear problems. This is why I love forums like this because I still have a way to hold a dialog with others. Thanks for your input.
Oh, ya! I played around with the setting in the audio section in mplayer and got my sound to sound better (or at least it sounded better to me, for what I could hear).
Irv

---

### Post by Blind-Summit on 2006-06-22
I guess the developers are really on their own here. No real support from the manufactuers of the hardware, so it's always down to them to work out how the devices communicate etc etc. For that reason, I am so very impressed with what they have achieved. As I said in another post - imagine if these guys had the financial backing of microsoft! 

Good luck with the sound - I hope it does get sorted as that's a really big part of why I use a computer - home recording!

---

### Post by trorion on 2006-06-23
I'm in the same boat.

lspci gives:
```
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 8201
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at e6000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 8201
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        I/O ports at d400 [size=256]
        I/O ports at d800 [size=128]
        Memory at e6082000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>
```

---

### Post by Blind-Summit on 2006-06-23
my lshw for multimedia:

```
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@00:05.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             resources: iomemory:ee000000-ee07ffff irq:5
        *-multimedia:1
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:d000-d0ff ioport:d400-d47f iomemory:ee080000-ee080fff irq:201

```

and the lspci

```
  0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

```

I don't know why we can't have a single interface like with windows where it detects the controls or functions of the hardware and just enables the sound for digital (or the best possible output) My also gnome mixer has about 20 different sliders and I'm sure non of them actually do anything for my audio control.

What's worse is the lack of knowledge on the subject. It seems so trial and error or so specific for other soundcards. I also noticed that many people use older PCs for linux and the newer stuff just isn't supported. It's putting me off using Ubuntu a bit

I have a .asoundrc file in my home dir and it looks like this:

```
pcm.nforce-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "nforce"
}


pcm.nforce {
type dmix
ipc_key 1234
slave {
pcm "hw:0,2"
period_time 0
period_size 1024
buffer_size 32768
rate 44100
}
}

#ctl.nforce-hw {
#type hw
#card 0
#}

#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

#pcm.!default {
#type plug
#slave.pcm "surround51"
#slave.channels 6
#route_policy duplicate
#}

################################################## ######
#This is the normal spdif output profile (optical, toslink).

#pcm.!spdif {
#type plug
#slave.pcm "hw:0,2"
#}

################################################## #####
#This is what one could call the "factory default setting", in other
#words, it only plays the actual channels. so if you fx want to watch a
#5.1 movie, on the analog output, this is the option you want.
#
#
#pcm.analog {
#type plug
#slave analog_slave;
#}

#pcm_slave.analog_slave {
#pcm surround51;
#format S32_LE;
#}

```

When I go to edit the file, I get this error (but I can still edit it ok)

blind-summit@blind-summit:~$ sudo gedit ~/.asoundrc
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave


So I then comment out the top lines, and use the bottom sections, and I get this


blind-summit@blind-summit:~$ sudo gedit ~/.asoundrc
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'cards.USB-Audio.pcm.surround51.0:CARD=0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51


I've set it back to just run the initial file, as this has less errors!

---

### Post by irv on 2006-06-23
Yesterday I went out on the IRC Chat Freenode and went into the ubuntu-kernel channel and was told that the new kernel doesen't ever use alsaconf any more. I am not not sure what that's all about. But I didn't get much in the way of help out there. I wish someone with more knowledge on this subject could really help us out on this one. I agree there is no real straight forward way to set up sound and hardware for sound in Ubuntu. I know it is an issue with the kernel because I can get it to work in some cases when going back to an older kernel.

---

### Post by irv on 2006-06-24
Haver doing some searching I found this great how to on setting up sound in Linux: check it out.
[[COLOR="Red"]http://tldp.org/HOWTO/Sound-HOWTO/index.html[/COLOR]]("http://tldp.org/HOWTO/Sound-HOWTO/index.html")

---

### Post by Lrover on 2006-06-24
Hmm, interesting. I installed Kubuntu 6.06 a few days ago, forgetting that my ESI Pro card isn't supported in ANY linux distro yet, so I pulled it out and rebooted and enabled my onboard AC97 sound. It picked up on the chip right away and system sounds now work and I can play from a CD, but no MP3's will play and no sound in any .avi or mpg videos. Definately weird. This chip has always worked without fail with any other distro I've tried, live-CD or otherwise. I even went into Adept and installed mpglib support and rebooted and no difference. Before I changed the cards out I did do a full update (including the kernel image), and from what I've seen the new kernel seems to be breaking a lot of sound drivers. Any comments / advice would be appreciated. ;)

---

### Post by Blind-Summit on 2006-07-03
[QUOTE=irv]Haver doing some searching I found this great how to on setting up sound in Linux: check it out.
[[COLOR="Red"]http://tldp.org/HOWTO/Sound-HOWTO/index.html[/COLOR]]("http://tldp.org/HOWTO/Sound-HOWTO/index.html")[/QUOTE]

Nothing in there about my SPDIF issues. Still not working

---

