---
title: "Volum-control!"
date: 2005-05-22
forum: Desktop Environments
---

### Post by dragonheart73951 on 2005-05-22
Hallo! ich habe ein Ähnliches Problem, wie in einem anderen Thread behandelt wurde, aber die Lösung hat bei mir nichts gebracht: 
 Ich habe Kubuntu und eine SB-Live! 
 Mein Problem ist, dass ich die Lautstärke am Masterregler nicht verändern kann (und zwar egal wo - mit alsamixer auf der Konsole gehts genausowenig! - wenn ich die PCM-Regler verstelle tut sich aber was...) 
 Das ist vor allem deshalb ärgerlich, weil ich die Sondertasten meiner Tastatur so nicht nutzen kann... 
 Hat vielleicht jemand eine Ahnung, an welcher Stelle man nachschauen muß was da hakt?

I have SB-Live! and I can't djust the volume with the master-volume-control! 'mute' doesn't have any effect either. It dosnt matter if I use kamix or alsamixer at the shell! Only when I change the setting of the PCM-control it results in changed volume. 
Whats wrong? where can I find information or look whats going on? which log should I consult? 
...any ideas? - I'm desperate!

---

### Post by bored2k on 2005-05-22
This is an english only forum.

---

### Post by dragonheart73951 on 2005-05-22
sorry - I translated the german text and forgot to erase it...

---

### Post by usererror on 2005-05-23
my sound is the same way.  I've learned to live with it.  I just set my applet to control the PCM volume, and hide the master bar.

---

### Post by Ironi on 2005-05-23
It's probably a driver issue; I think that I had the same problem with my Audigy 2 a while back. Try upgrading your kernel, perhaps (apt-cache search kernel-image-2.6.11). Make sure that you're using ALSA as well.

---

### Post by dragonheart73951 on 2005-05-24
2.6.11 dosn't seem to have any effect...

---

### Post by Ironi on 2005-05-24
Check [this](http://forums.fedoraforum.org/showthread.php?t=52799) out -- do you have the connections right? If that isn't the problem, then post the output of these:
[font=Courier New]
lspci -v |grep -A5 audio
dmesg |grep -A10 -i sound
dpkg -l |grep -i alsa
sudo grep -i alsa /var/log/syslog
[/font]

---

### Post by dragonheart73951 on 2005-05-25
The connections of the plugs and cables seem to be right.
Here are the outputs (two of the commands didnt produce any...)

root@Spassmaschine:/home/spass # lspci -v |grep -A5 audio
0000:02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! Player 5.1
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at cf20 [size=32]
        Capabilities: [dc] Power Management version 1
             
root@Spassmaschine:/home/spass # dmesg |grep -A10 -i sound
->no output

root@Spassmaschine:/home/spass # dpkg -l|grep -i alsa
ii  alsa-base      1.0.8-4ubuntu4 ALSA driver configuration files
ii  alsa-oss       1.0.7-1        ALSA OSS-compatibility application wrapper
ii  alsa-utils     1.0.8-1ubuntu1 ALSA utilities
ii  libasound2     1.0.8-1        ALSA library
ii  libwine-alsa   0.0.20050310-1 Windows Emulator (ALSA Sound Module)

root@Spassmaschine:/home/spass # grep -i alsa /var/log/syslog
->no output

---

### Post by Jonathan2007 on 2005-05-25
Hi. I am also having a problem with my sound. I am using a SB Live! sound card. I can only control my volume using the Wave Surround. I believe I am using the Alsa drivers but maybe it is EMU10K1 as I see 3 levers for that in KMix. But they don't do anything. Only Wave Surround. I think this must be a problem with SB Live! sound cards. I have also tried Xandros 3 and Suse 9.2 and they also have this problem so it doesn't appear to be Kubuntu related.

---

### Post by dragonheart73951 on 2005-05-29
I had the same problem with a previous distribution as well (Suse 8.x) - but in a later release this wasn't an issue anymore - so I considered that as resolved...

---

