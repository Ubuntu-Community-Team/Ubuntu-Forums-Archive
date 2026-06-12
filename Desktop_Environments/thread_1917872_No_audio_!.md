---
title: "No audio !"
date: 2012-01-30
forum: Desktop Environments
---

### Post by StepNjump on 2012-01-30
Yep, 

Everything was working fine. The only thing I have done since was to do the following:

./configuration and make on package curl-7.20.0.tar.gz (not even make install).. Of course nothing shows in dpkg. Could these events be related? 


AT-8:~$ dpkg -l curl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
un  curl                              <none>                            (no description available)

All seems to be normal...

Thanks in advance,


StepNjump

version is natty 32

---

### Post by StepNjump on 2012-01-30
Again, this used to work just fine up to today... Pretty strange!

Additionally, followed the steps in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
```

1- ok

2- aplay /usr/share/sounds/alsa/Front_Center.wav
> nothing heard

3- Can another user play one of these "known-good" sounds?
> nothing heard

4- AT-8:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
5- Do you have the sound modules installed?
AT-8:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.38-13-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/2.6.38-13-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.38-13-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/msnd
/lib/modules/2.6.38-13-generic/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-jazz16.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/galaxy/snd-azt1605.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/galaxy/snd-azt2316.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.38-13-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.38-13-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.38-13-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.38-13-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.38-13-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/2.6.38-13-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/2.6.38-13-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.38-13-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.38-13-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.38-13-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.38-13-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko


5 -
AT-8:~$ sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-2.6.38-13-generic
E: Couldn't find any package by regex 'linux-restricted-modules-2.6.38-13-generic'

6- Is the sound card physically installed and recognized by your hardware?
AT-8:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company PufferM-UL8E
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at ccffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

---

### Post by StepNjump on 2012-01-30
Nothing found in hardware tab! Please see attachment.

---

### Post by StepNjump on 2012-01-30
please see attachment

---

### Post by StepNjump on 2012-01-30
Might have started after I installed and ran 

sudo aptitude install randomsound

In order to increase my entropy count (was trying to generate pgp key)

---

### Post by StepNjump on 2012-01-30
tried steps in [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447522](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447522)

---

### Post by StepNjump on 2012-01-30
tried steps in [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447522](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447522)

The audio is back somehow but when I click on sound preferences, the window no longer comes up.
Recording is also disabled.

---

### Post by StepNjump on 2012-01-30
here is my output of pulseaudio -vvvv command:
[:popcorn:]("http://paste.ubuntu.com/823427/")

---

### Post by StepNjump on 2012-01-30
It seems to be totally stuck on 

D: sink.c: Suspend cause of sink auto_null is 0x0004, suspending

---

