---
title: "WUBI installed NO sound.. helps not working yet"
date: 2009-02-12
forum: General Help
---

### Post by forestwalkerjoe on 2009-02-12
Ok.. is still stumped despite the fact that there are help links in here. 
I am on a new WUBI install.. never done that before.. and i have no sounds. 
I have done some of these helps from this link.. and come up empty.. so far.. i am bound and determined that we can solve this issue. 
can some one please help me out here? 

I started reading the helps and followed these instructions.. even to the point of uninstalling and reinstalling the alsa sound utils.. with the other stuff that does seem to get uninstalled too.. and REINSTALLED rebooted.. still no sound. the comments below are what my system says.. denied and in use. etc. 

I have been trying to trouble shoot why I have NO sound at all in ubuntu 810 wubi install. 
Can some one help me out? This is the first time I have ever done a WUBI and then I have also first time to have the special effects working. THEY are GREAT! 
The page I was working with has this link 


[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

I deleted some of these so make this a shorter post. 

 ```

rj@ubuntu:~$ lspci -v





02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X

	Subsystem: Creative Labs Device 1003

	Flags: bus master, medium devsel, latency 64, IRQ 17

	I/O ports at cf20 [size=32]

	Capabilities: <access denied>

	Kernel driver in use: EMU10K1X

	Kernel modules: snd-emu10k1x



02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller

	Subsystem: Creative Labs Device 1003

	Flags: bus master, medium devsel, latency 64

	I/O ports at cf08 [size=8]

	Capabilities: <access denied>

	Kernel driver in use: Emu10k1_gameport

	Kernel modules: emu10k1-gp






rj@ubuntu:~$ sudo modprobe snd emu10k1-gp

rj@ubuntu:~$ sudo modprobe snd-emu10k1-gp

FATAL: Module snd_emu10k1_gp not found.

rj@ubuntu:~$ sudo modprobe snd emu10k1-gp

rj@ubuntu:~$ 
```
i have followed the instructions from that link as best as i understand them.. but i need further help now. 

when i type in this other one.. it just goes back to promt
rj@ubuntu:~$ sudo modprobe snd snd-emu10k1x
rj@ubuntu:~$ 


FWJ

---

### Post by Darkmage09 on 2009-02-12
I had a problem with my sound as well, see what had happaned was Vista (My host OS) the sound was down. I naturally made a post about it here. but several hours later I booted up into Vista, and found out that I had turned the volume down. So I turned that up, and then rebooted and I had sound.

So reboot into your Host OS. Turn the volume up, reboot back into Ubuntu.

(This is all based on a laptop.) So if you have a desktop, and the volume is up, as well as the volume manager. Then someone else may know the answer.

Good luck :)

---

### Post by forestwalkerjoe on 2009-02-12
I tried that.. its not the sound not being up on my windows system. it seems that the driver is confused.. which one goes where.. i think is the issue. 
I need someone to help me set up the alsa.. and i have done a few changes.. i remember there is some thing called alsa config.. but i have no idea what the code is to set that up. 
any one know some thing i can do to get my sounds?

EDIT  ok.. i had to think about this.. but when i first installed this wubi it was fine and sounds were working. then i did the update.. and at the end of the update.. my mouse was not clicking correctly.. and sounds were strange. 
Errors required a reboot. 
so i rebooted.. and then suddenly realized.. i had no log in or or password drums. 
I went out on the Forums here to find answers and ran into [trouble shooting pages]("https://help.ubuntu.com/community/SoundTroubleshooting") like this . 
which does through a lot of changes to the system.. has you use OPEN SOUND.. or change back to uninstalling and reinstalling ALSA core. 
the checks i have done showed my card was installed and recognized.. then after the reinstall it was not seen. 
when i go through Each step.. it responses correctly till the last set.. now i have the settings all on default.. i think.. and NO way to know why i have NO sounds at all. 
i am sure one of you can help me reset things so that the sounds are all back again. 
IF someone will just come look and show me what to do next. 
FWJ 

FWJ

---

