---
title: "No sound - Dell Latitude C610, Xubuntu 7.04"
date: 2007-07-07
forum: Dell  Ubuntu Support
---

### Post by Chili.willy on 2007-07-07
I'm stuck, trying to figure out why my Dell C610 won't play any audio. aplay and Alsa can't seem to find the sound card. According to "lspci -v", the card is "Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02) Subsystem: Cirrus Logic Crystal WMD Audio Codec". 

"cat /proc/asound/cards" produces this output:
 0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with CS4205 at 0xd800, irq 5

(So do I have an Intel 82801 sound card, or a Cirrus Logic CS 4205 card?? Many of my sound drivers refer to snd_intel8x0 and none refer to CS 4205.) 

I think the wrong drivers are being loaded. XMMS thinks it's playing an mp3, but no sound can be heard. When I give aplay a .wav file, it gives a list of ALSA errors like "cannot find card '0'" and "no such device". 

Anyone have ideas to solve this?

Many thanks,
Will

---

### Post by Darkcloud on 2007-07-07
Hi  I also have a Dell C610 with Ubuntu on it   my audio is Crystal CS4205  should be the same

---

### Post by Chili.willy on 2007-07-07
Hmm. Darkcloud, can you tell me what info you get when you type 
lsmod | grep snd
in a terminal window? (It will list sound drivers that are loaded.)

Thanks,
W.

---

### Post by Darkcloud on 2007-07-07
Hi sure  here it is

lauri@lauri-laptop:~$ lsmod | grep snd
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
lauri@lauri-laptop:~$ 
hope that helps

---

### Post by Chili.willy on 2007-07-07
Thanks much. I think it does help. My output is much the same as yours; sometimes the number in the 2nd column of my output, e.g., the "34204" in 
[COLOR="DarkGreen"]snd_intel8x0           34204  0 [/COLOR]

is different from yours (in this case you had 34332), not that I know what it means. 

However, you have this line:
[COLOR="DarkGreen"]soundcore 8672 1 snd[/COLOR]
and I don't have anything corresponding to it. 

I wonder what that means. It's probably important, because I think it means your system is loading a driver that mine isn't. 

When i was reading up on this before I posted the question, I encountered 
[COLOR="DarkGreen"]modprobe -l snd*[/COLOR] 
which is supposed to list all the ALSA (Advanced Linux Sound --something--) drivers that are "built", a much longer list than you get with [COLOR="DarkGreen"]lsmod | grep snd[/COLOR]. That doesn't show anything called "soundcore".  I wonder if I need to get a "soundcore" driver someplace. 

I hope someone Linux-smarter than me can advise. 

Will

---

### Post by Darkcloud on 2007-07-07
there could be a significance in the fact you are running Xubuntu and I have Ubuntu on mine  could be a matter of certain files that come with Ubuntu that doesn't  with Xubuntu  I don't know all I know is its a lighter system

---

### Post by Darkcloud on 2007-07-07
well  look through what I have here  maybe you can spot what is missing in yours

lauri@lauri-laptop:~$ modprobe -l snd* 
/lib/modules/2.6.20-16-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.20-16-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-gus-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/ad1848/snd-ad1848-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.20-16-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/trident/snd-trident-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.20-16-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.20-16-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.20-16-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd-rtctimer.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-instr.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/instr/snd-ainstr-simple.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/instr/snd-ainstr-fm.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/instr/snd-ainstr-gf1.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/instr/snd-ainstr-iw.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.20-16-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/snd-bt-sco.ko

---

### Post by Chili.willy on 2007-07-08
Thanks, Darkcloud! there may be a difference in the order of the lines, i don't know how to test that without looking line by line by line. But i sorted your output and mine, and the only difference is that yours have 2.6.20-16 and mine have 2.6.20-15. I guess that means your kernel is one tweak newer than mine. I doubt that's the problem. 

I ran Synaptic Package Manager to look for any sound-related stuff that might be broken. Found nothing. 

Are you happy with regular Ubuntu on the C610? The 1st distr. I installed was openSuse. I basically liked it, but many operations were   so o o o o     s  l  o  w.  Xubuntu is much quicker. 

Will

---

### Post by Darkcloud on 2007-07-08
I am quite happy with it  I just have 384 Ram with the gig processor and it has been responding very well  beryl hasn't even caused a problem   although I haven't had feisty on here for very long and I am still learning and still experimenting  it seems to me very stable on this laptop  but I do know what you mean about xubuntu  I repair laptops and have quite a few here in various stages of use or disuse as the case may be  and I have found xubuntu to be a choice for the older ones   as to the sound issue  well I wish I could be more helpful  maybe alsa-utils could be a source of a fix   but I am still quite a newbie  and loving it!!:)

---

### Post by Darkcloud on 2007-07-08
That has to be irritating, my not using punctuation or capitalization.  Sorry bout that

---

### Post by Darkcloud on 2007-07-08
Stumbled on this a few minutes ago  don't know if it will be helpful but worth a shot maybe
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by Chili.willy on 2007-07-08
I followed the procedure in that HdaIntelSoundHowTo. It looked good, but actually things appear worse now, because [COLOR="Green"]cat /proc/asound/cards[/COLOR] now produces [COLOR="Green"]No such file or directory[/COLOR] rather than information about the sound card (in fact there is no [COLOR="Blue"]/proc/asound[/COLOR] directory at all), and when I issue [COLOR="Green"]lsmod | grep snd_[/COLOR], instead of a list of loaded drivers, there is nothing. The list of "built" drivers is the same as before, so somehow whatever tells the system to load sound drivers must be gone.

---

### Post by clivebn on 2007-07-08
try using 'Cafiene ' as your sound mixer .... just might work ... let me know ..ok !

---

### Post by Darkcloud on 2007-07-08
oh wow now that sucks   maybe reinstalling the driver for that sound card may help

---

### Post by Darkcloud on 2007-07-08
and I keep trying to help   heres another place for manual sound setup/debug    what I would do if this doesn't work  is install Ubuntu  or reinstall xubuntu
[https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

well for some reason part of the word Debugging  doesn't show up but thats what it is

---

### Post by Chili.willy on 2007-07-09
clivebn: I'm reluctant to add new software now--since the system isn't finding the sound card at all, I don't think using a difft. mixer is likely to help at this point.  Thanks for the idea.

Darkcloud: The site you listed looks like it might be worth a try. I just posted my question (updated) to Linuxquestions.org. I'm gonna wait & see if anything really brilliant pops up there before I do that. You also suggested reinstalling the driver for the card. How do you do that?

---

### Post by Darkcloud on 2007-07-09
I used this once before on a different laptop and it worked  

 Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

   1. Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
          * Here's the likely output you'll get by running that above command 
   2. Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils
          * VERY IMPORTANT NOTE - Ubuntu (GNOME): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following sudo apt-get install gdm ubuntu-desktop
          * VERY IMPORTANT NOTE - Xubuntu (XFCE): users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base. If this happens, then do the following sudo apt-get install gdm xubuntu-desktop
          * Here's the likely output you'll get by running the above commands 
   3. Reboot
   4. At this point, try using aplay -l you should get your soundcard listed.
          * Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
          * Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation. 

Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.


 Using alsamixer

    * Type this into a shell alsamixer 

You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place.

    * To navigate around:
          o Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen )
          o Up and Down Arrow Keys - Increase and decrease volume respectively.
          o Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey. 

[edit]
Saving Sound Settings

Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do sudo alsactl store 0 or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.

---

### Post by Darkcloud on 2007-07-09
](*,)  I suppose it would have been easier to just post the url  

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

### Post by Darkcloud on 2007-07-10
I was just over at a friends house whos latitiude c500 I installed ubuntu on for  lost sound   so I went over to see what I could do  and not that this is what is up with yours  but the only thing wrong was  the audio mixer in her music app out of Applications> Sound and Video had somehow been turned down to the point you couldn't hear anything  even if you had the sound volume on the toolbar turned all the way up   it was weird because she had watched a movie on it and had no problems and then when I came over to configure her wireless  the sound had disapeared   but adjust the audio mixer  fixed the problem  sound!  maybe just maybe  that is what is up

---

### Post by Chili.willy on 2007-07-10
Great ideas! Especially the one about removing & reinstalling the ALSA drivers. (I didn't want to reinstall the entire system, partly because of the hassle and partly because that's the MS Windows way of life; it seems like we should be able to do better!) 

I am working my tail off this week, so I may not get a chance to try it for a couple more days. Thanks much for all the thought you have been devoting to this. 

As for your friend's situation--I don't think I'd be getting some of my symptoms (like what is it, [COLOR="Green"]modprobe -l[/COLOR] or something? reporting no drivers loaded) if the problem were simply the mixer application being turned way down or muted. And [COLOR="Green"]aplay -l[/COLOR] reports it can't find a soundcard. 

Anyway I'll get to that & let you know what happens. Later...

---

### Post by Darkcloud on 2007-07-10
too true    if there is no driver that wouldn't be the probem  hopefully unistalling and reinstalling alsa  will make all the difference.  I don't mind helpin  its become kind of a pitbull kind a thing  can't let go   but I also do that with work  if there is a problem I won't stop till I find some kind of answer  and we have the same kind of laptop so I figure its a good thing for me to try to help and being a tech I love the challenge:)   I work at home mostly or contract out for work  so I am already working with machines and multitasking is ADD in disguise well for me anyway  and wouldn't you just love to be able to fix this so you can move on to some fun things with xubuntu?

---

### Post by inuyokai on 2007-07-10
Have either of you tried the following:

Do this in terminal (if for an odd reason you need to run as root then use sudo <code>)

Check if your sound card is seen by Ubuntu

```
asoundconf list
```

If you see your sound card then make sure it is set as the default card

```
asoundconf set-default-card yourcardname
```

Then open ALSA Mixer and make sure that the volume is up and anything similar to Analog/Digital Output is off

```
alsamixer
```

Play around with the ALSA Mixer settings and see if you can get sound.

Hope that works

---

### Post by Darkcloud on 2007-07-11
I hadn't hit on that one yet   my sound works  I was just trying to help him look for an answer that maybe a good one to try

---

### Post by Chili.willy on 2007-07-13
Thanks, everyone, for the help & ideas. Still listening to the sound of silence. 

** Inuyokai**--
[COLOR=Green]asoundconf list[/COLOR] gives nothing, a blank response. The file that it looks in, [COLOR=Blue]~/.asoundrc[/COLOR], doesn't exist in my machine. 
[COLOR=Green]aplay -l[/COLOR] shows that the soundcard isn't being "found" (i.e., "[COLOR=Green]device_list:222: no soundcards found...[/COLOR]")
[COLOR=Green]but lspci -v[/COLOR] shows that the system does know about the soundcard in some way (see the very 1st post in this thread). 

That command, [COLOR=Green]asoundconf set-default-card yourcardname[/COLOR], probably can't work with the state the system is in right now, but even if it could, I have never been able to figure out what "mycardname" should be. Can you tell me how to tell? 

** Darkcloud**--
I tried the directions for purging & reinstalling the ALSA packages (post #17 in thread). Scary, because my graphical environment was trashed as the warning explains, but it came back all right. Still no sound, however, and no [COLOR=Blue]/proc/asound/[/COLOR]. 

When I issue the command [COLOR=Green]lsmod[/COLOR], nothing referring to sound shows up in the long list of loaded modules. So then I tried issuing [COLOR=Green]modprobe soundcore[/COLOR] and [COLOR=Green]modprobe snd[/COLOR]. ("modprobe is a program to intelligently add and remove modules from the Linux Kernel.") After that, [COLOR=Green]lsmod[/COLOR] showed these additional lines:
[COLOR=Green]snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  1 snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  4 snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd[/COLOR]
I think there should be more sound-related items in the list, but I don't know what to tell modprobe to load. Maybe I could tell if you can post the output of [COLOR=Green]lsmod[/COLOR].

The [Debugging website]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") that you cited says you can issue "modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]" but I have never been able to figure out what that NAME should be. I tried [COLOR=Green]sudo modprobe snd-intel8x0[/COLOR] and some variations, but it just gives error messages.

If I can't fix this with [COLOR=Green]modprobe,[/COLOR] the only idea I have at the moment is to try [compiling ALSA drivers]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") as explained in the debugging website you quoted before. I don't have any special reason to think it would help, but it's something to try.

---

### Post by Darkcloud on 2007-07-14
Hi there   sorry been very busy today  mmm  here's my list for you to check out   still think that if you upgrade to Ubuntu that will solve your problem  well hopefully  beings as I have the same type laptop and I have zero serious problems  anyway  I will do some more checking  

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_ich           6288  0 
speedstep_lib           6148  1 speedstep_ich
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
freq_table              5792  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
ac                      6020  0 
container               5248  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ndiswrapper           194608  0 
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 10816  0 
pcmcia                 39212  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
pcspkr                  4224  0 
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
psmouse                38920  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25244  1 
agpgart                35400  2 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
floppy                 59524  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
uhci_hcd               25360  0 
usbcore               134280  3 ndiswrapper,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
lauri@lauri-laptop:~$

---

### Post by Chili.willy on 2007-07-15
Many thanks. 

You know, Darkcloud, your suggestion of upgrading to Ubuntu is probably the best advice, and it's what I might end up doing. But not just yet! for a couple of reasons. First, the reason I installed Xubuntu in the first place was, I had been running openSuSE and it was so slow at a lot of things on this old machine. I figured another full-featured distro like Ubuntu was also likely to be slow. Rightly or wrongly. The other reason is, I hope to learn some good stuff :???: by trying to make the sound work here in Xubuntu. 

When I compiled & installed the Alsa system (alsa-drivers, alsa-lib, and alsa-utils) I used version 1.0.14rc4.  I looked more carefully and realized that version 1.0.14 is newer, and the changelog for it says that they addressed some Ubuntu "quirks" between 1.0.14rc4 and 1.0.14. So I compiled and installed 1.0.14.  

I believe the main problem is, although now I have the drivers & stuff, they aren't being loaded. If I understand rightly, the files in [COLOR=Blue]/etc/modprobe.d/[/COLOR] contain the instructions for what modules to load when the system starts up. There is a [COLOR=Blue]/etc/modprobe.d/alsa-base[/COLOR] that seems to have all the sound-related stuff. And there are various blacklist files that tell the system NOT to load certain drivers that otherwise might get loaded. 

Anyway, Darkcloud, if you're not completely tired of this thing yet, 
if you post your  [COLOR=Blue]/etc/modprobe.d/alsa-base[/COLOR], I can compare and see if my system is loading the same sound modules as yours, maybe.

---

### Post by Darkcloud on 2007-07-15
no of course not   I am learning along with you in trying to figure this out   but your getting the best lessons   I have probably installed xubuntu and ubuntu on like 10 laptops and one desktop   and I have yet to run into a serious problem  but I just started   actually I am impressed   anyway  heres that output  is this what you wanted??

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by Chili.willy on 2007-07-15
Muchas gracias, Darkcloud. I think what I'll do a little later is just replace my [COLOR="Blue"]/etc/modprobe.d/alsa-base[/COLOR] with what you posted and see what happens. 

Before you posted that, I managed to load most of the sound drivers using statements like [COLOR=Green]sudo modprobe snd[/COLOR], etc. etc. and I'm still getting this error when I try to play a sound using [COLOR=Green]aplay usr/share/sounds/gaim/receive.wav[/COLOR]:
[COLOR="Green"]ALSA lib confmisc.c:769:(parse_card) cannot find card ''[/COLOR] (Note the end of that error message is single quotes with nothing in between. I've seen the same message with a zero between the quotes.)

Does that look like drivers are missing? Or is there something else that keeps it from finding the soundcard? Note, I still haven't found a way to load snd_intel8x0, which is probably a really important one. The modules I did load using modprobe correspond to files with [COLOR=Blue].ko[/COLOR] extensions. If anyone can suggest how to load snd_intel8x0 that might be a huge help.

---

### Post by Darkcloud on 2007-07-15
> **Chili.willy said:**
> Muchas gracias, Darkcloud. I think what I'll do a little later is just replace my [COLOR="Blue"]/etc/modprobe.d/alsa-base[/COLOR] with what you posted and see what happens. 

Before you posted that, I managed to load most of the sound drivers using statements like [COLOR=Green]sudo modprobe snd[/COLOR], etc. etc. and I'm still getting this error when I try to play a sound using [COLOR=Green]aplay usr/share/sounds/gaim/receive.wav[/COLOR]:
[COLOR="Green"]ALSA lib confmisc.c:769:(parse_card) cannot find card ''[/COLOR] (Note the end of that error message is single quotes with nothing in between. I've seen the same message with a zero between the quotes.)

Does that look like drivers are missing? Or is there something else that keeps it from finding the soundcard? Note, I still haven't found a way to load snd_intel8x0, which is probably a really important one. The modules I did load using modprobe correspond to files with [COLOR=Blue].ko[/COLOR] extensions. If anyone can suggest how to load snd_intel8x0 that might be a huge help.


my understanding (and believe me its little still) is that you have to put the name of the sound card as well   something like  snd_intel8x0,snd_ac97_codec,snd_pcm_oss  that is what my sound is   should be exactly yours too  but I am sure there are more commands to go with that   I'll keep looking too

---

### Post by Darkcloud on 2007-07-15
[https://help.ubuntu.com/community/forum/hardware/OldSoundCard]("https://help.ubuntu.com/community/forum/hardware/OldSoundCard")


check this one out

---

### Post by Chili.willy on 2007-08-19
For those who might be interested:

I finally "solved" the problem by giving up on Xubuntu and installing regular Ubuntu. The sound worked fine as soon as I installed Ubuntu. 

My worries about Ubuntu running much slower than Xubuntu did not come true. Ubuntu works just about as fast.

---

