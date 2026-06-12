---
title: "Alsa Mixing (multiple sounds) help :("
date: 2005-04-09
forum: Desktop Environments
---

### Post by RastaMahata on 2005-04-09
I'm unable to play several sounds at a time.
I tried to use ESD, but it creates an incredible lag between video and sound when I play movies. Alsa is great, but I can only hear one sound at a time. How can I fix this? I already searcheed the forums, but I couldnt find any answers for Hoary stable :(

---

### Post by RastaMahata on 2005-04-09
bump? :(

---

### Post by RastaMahata on 2005-04-09
bah, I fixed the problem. I found a .asoundrc file that allowed me to play several sounds. Here are the steps Followed (I have an **nforce2** chipstet)

1. killall esd
2. System > preferences > sound > the sound server thing: unchecked
3. gedit ~/.asoundrc (or /etc/asound.conf), and paste this:
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
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
```
3. sudo gedit /etc/libao.conf, and where it says esd, type alsa:
```
default_driver=alsa
```
4. System > preferences > multimedia: select both things ALSA
5. After you've changed /etc/asound.conf, use Synaptic to perform a smart pakage install. Install the libesd-alsa0 and all dependecies.
6. Reboot gnome (ctrl+alt+backspace)

test by playing a movie, and a song (totem, rhythmbox)...

anyway, gaim sounds seem choppy / bad quality, but totem movies play excellent (no audio delay)

Note: I dont know if alsa-oss is needed or not. If this doesnt work, try installing this package (apt-get install alsa-oss), and rebooting gnome

---

### Post by Ranime on 2005-04-11
Tnx RastaMahata =D> 

You're guide is the only one that worked with my configuration!

Finally I got multiple sounds!

1 recommandation though:
After you've changed */etc/asound.conf*, use Synaptic to perform a smart pakage install. Install the *libesd-alsa0* and all dependecies.

Please make sure you use the smart installation option, or otherwise, conflicting libraries won't be un-installed!

---

### Post by rwabel on 2005-04-13
I can only set the output to alsa, for input  I need to take OSS!

Because with ALSA as Input I get that error message:
Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

Is there a way to fix that somehow.

I've also the problem that my mic is very very low, even having the mic boost activated.

---

### Post by emmbec on 2005-04-15
> 4. System > preferences > multimedia: select both things ALSA

Where is that??? I'm new to linux, and I can't find it. Is there a command for this??? if so, how do I put a shorcut in Nautilus??? thanx

---

### Post by rwabel on 2005-04-16
[QUOTE=emmbec]Where is that??? I'm new to linux, and I can't find it. Is there a command for this??? if so, how do I put a shorcut in Nautilus??? thanx[/QUOTE]

do you have warty or hoary?
I don't know how the menus are in warty.

---

### Post by emmbec on 2005-04-16
I have warty

---

### Post by rwabel on 2005-04-16
I'm even not sure if that one is available in warty. in hoary it's system->preferences->multimedia systems selector

maybe someone else who knows better warty can help if you don't find it that way. sorry

---

### Post by julipanno on 2005-04-28
> Alsa is great, but I can only hear one sound at a time. How can I fix this? I already searcheed the forums, but I couldnt find any answers for Hoary stable

I also have difficulties in configuring ALSA for multiple sounds on my Inspiron. I have tried what I could find of HowTos and advice on the ubuntuforums. I also tried figuring out the instructions on the ALSA-website, but they were mostly above my head.

Any assistance would be appreciated as I have spent weeks on this problem without coming closer to a solution. My PC is an Inspiron 9200 with an intel 82801DB-ICH4 soundcard that uses a SigmaTel STAC9750/51 chip (according to alsamixer). I am running Ubuntu Hoary, and believe I have all the right packages installed.

ALSA is working fine with one sound only, but when I try to start sound from two players, the last one waits for the first one to stop before it begins. No error message (anymore).


Here is my asound.conf should anyone be able to help me:
```

pcm.intel8x0 {
type hw
card 0
}

ctl.intel8x0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}

```

My esd.conf is exactly as in the HowTo on [http://www.ubuntuforums.org/showthread.php?t=8882&highlight=multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=8882&highlight=multiple+sounds)


Stian

---

### Post by guardian653 on 2005-04-28
Well I too have an Intel board with a AC'97 compliant audio chip so maybe my config can help you:

Copied and modified from the dmix site:
```
# .asoundrc for use with ALSA and the dmix plugin, for ALSA-level
# software mixing across all apps.
#
# http://alsa.opensrc.org/index.php?page=AlsaSharing
# http://alsa.opensrc.org/index.php?page=DmixPlugin

pcm.dmix0 {
    type dmix
    ipc_key 219345           # any unique number here
    slave {
            pcm "hw:0,0"
            period_time 0
            buffer_time 0
            period_size 2048    # jm: much smoother than 1024/8192!
            buffer_size 32768
            rate 48000
    }

    bindings {
        0 0   # from 0 => to 0
        1 1   # from 1 => to 1
    }
}

pcm.dsp0 {
  type plug
  slave.pcm "dmix0"
}

# this makes native ALSA apps default to using dmix
pcm.!default {
  type plug
  slave.pcm "dmix0"
}

ctl.dsp0 {
  type hw
  card 0
}

ctl.!default {
  type hw
  card 0
}

```

I also installed the alsa-oss from synaptic so that OSS based apps (firefox being one of them  ](*,))

```
# FIREFOX_DSP=aoss firefox
```

If your running totem or rythmbox you should install totem-xine as it seems the gstreammer one doesn't work with w32codecs or alsa. If your running BMP or XMMS of course have the ALSA plugins for them.

For Gaim, if the automatic setting doesn't work try using

```
aplay %s
```

If that all works out you should be able to hear a flash movie, bmp, gaim any anything else all spouting their hearts out at the same time  :-) without needing ESD I might add!

---

### Post by julipanno on 2005-04-29
> 
If that all works out you should be able to hear a flash movie, bmp, gaim any anything else all spouting their hearts out at the same time  without needing ESD I might add!


Thanks to your configuration, my ALSA is finally able to play multiple sounds. Thank you very much.

Stian

---

### Post by ColdWind on 2005-05-27
The '.asoundrc' of guardian653 worked for me perfectly! 

Totem, amaroK, Gaim.... all sounds fine!!!

Thank you

---

