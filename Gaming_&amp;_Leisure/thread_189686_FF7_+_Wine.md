---
title: "FF7 + Wine"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by JNowka on 2006-06-05
Ok i installed FF7 and am having problems.  When I go to start up FF7 I keep getting that it can't find my sound card and it needs a Win95 compliant midi device.  What can I do to fix this?  I have installed the Sound Drivers from asus.com and have installed the TM20 codecs as needed.  I have windows media player installed as well.  What do I do now?

---

### Post by cogadh on 2006-06-05
You probably don't have midi sequencer support built into your soundcard and you will likely need to install/configure Timidity to get FF7 to work. What kind of soundcard do you have?

---

### Post by cogadh on 2006-06-05
I've been working on this one myself (SB Audigy LS doesn't have the hardware to handle midi sequencing) and I finally got it working. There are two ways to do this:
If you are on Breezy, the easy way is to use Automatix ([www.getautomatix.com](www.getautomatix.com)) to install and configure Timidity for you.
If you are on Dapper, you can do it manually (Automatix doesn't do this on Dapper for some reason):

**EDIT: PLEASE NOTE, THIS HAS CAUSED A SERIOUS ISSUE ON MY DAPPER SYSTEM. ALMOST ANY APPLICATION THAT UTILIZES THE MIDI SEQUENCER CAN LOCK UP THE ENTIRE SYSTEM, REQUIRING A HARD RESET. THIS ISSUE WAS RECORDED IN DAPPER BUG REPORTS PRIOR TO FINAL RELEASE, BUT IT IS APPARENTLY NOT CORRECTED YET**

1. Get a sound font (it will be needed later)
```
wget ftp://ftp.personalcopy.net/pub/Unison.sf2.gz
```

2. Get and install the Timidity and Pmidi packages (you will need to add the universe/multiverse repositories to your sources.list first)
```
apt-get install timidity pmidi
```

3. Modify the /etc/modules file to include the following:
```
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
```

4. Run the following four commands to install the sound font
```
sudo rm -rf /etc/sounds
sudo mkdir /etc/sounds/
gunzip Unison.sf2.gz
sudo mv Unison.sf2 /etc/sounds/
```

5. **/etc/timidity/timidity.cfg** Modify the last two lines  to this:
```
#source /etc/timidity/freepats.cfg
soundfont /etc/sounds/Unison.sf2
```

6. **/etc/init.d/timidity** Change the TIM_ALSASEQPARAMS setting to the following:
```
TIM_ALSASEQPARAMS="-iA -B2,8 -Os1l -s 44100"
```

7. **/etc/default/timidity** Uncomment the TIM_ALSASEQ option and modify the TIM_ALSASEQPARAMS to the following:
```
TIM_ALSASEQPARAMS="-iA -B2,8 -Os1l -s 44100"
```

8. Reboot and midi should work.

---

### Post by JNowka on 2006-06-06
Thank you, saddly Automatix wont work because my linux box can't connect to the net.  But I have it on a network with this computer so I will just down the neccisary files.  I am running breezy.

---

