---
title: "Slow, Very Slow, CD Ripping"
date: 2005-10-18
forum: Desktop Environments
---

### Post by shortl on 2005-10-18
It seems my Linux installations (Breezy and Mandriva 2005 and 2006) using Sound Juicer (and Kaudiocreator on Mandriva) rip a CD to Flac at about 0.9x--that is zero point nine.  The very same two machines dual-booted under Windows Me and Winamp rip to Flac at about 7.0x (yes, about 8x faste).  I am not asking for Mandriva support--I am new to Ubuntu and extrememly impressed and charmed, but this cannot be that Linux rips that much slower on two machines and three installations.  I have checked hdparm and dma is on and udma is max (6 or 4 depending on the machine).  One installation had a slider to adjust priority on SJ; I adjusted that to max--no difference.  Linux is not Windows--thank goodness--but I am hoping that there is some adjustment I can make to get more reasonable ripping times.  (You'll enjoy this--the only reason I ever rip any cd's is to put my own on the computer so i can mix them at random--I have found twice--with a sb pci 512 and an m-audio 2496 that the Linux drivers sound noticably better than the windows drivers-noticably!.
thanks for any help.

---

### Post by flaming_monkey on 2005-10-18
There's a reason Audio CD's rip slowly on Linux, it's because Linux is Paranoid. ;-)

I'm not sure about Sound Juicer but GRip, an alternative audio ripper with a lot more options, uses cdparanioa to rip the audio from the CD and by default it uses scratch detection and extra paranoia i.e. rip slow to avoid any blips or pops in the audio.

If you want to speed up the ripping process try installing grip:

```
sudo apt-get install grip
```

Load grip, play with the ripping options (disable scratch detection, paranoia) and try ripping.

Hope that helps.

---

### Post by GazaM on 2005-10-18
Sound Juicer also uses Paranoia by default... unfortunately the only way to change this at the moment is by going into gconf and manually editing Sound Juicer's Paranoia level. Do this as follows:
Go to Applications>System Tools>Configuration Editor... when it has opened select apps>sound-juicer and in the right panel, one of the options should be 'paranoia', what you need to do is right-click on that option, select 'Edit Key' and replace the 4 (default) to a 0 which turns off all paranoia. Turning off paranoia is fine if you're cd's are in fairly good condition and your cd drive isnt on the blink so dont worry about it, this should speed up ripping considerably ;)

---

### Post by jamieson on 2005-10-18
[QUOTE=flaming_monkey]There's a reason Audio CD's rip slowly on Linux, it's because Linux is Paranoid. ;-)

I'm not sure about Sound Juicer but GRip, an alternative audio ripper with a lot more options, uses cdparanioa to rip the audio from the CD and by default it uses scratch detection and extra paranoia i.e. rip slow to avoid any blips or pops in the audio.

If you want to speed up the ripping process try installing grip:

```
sudo apt-get install grip
```

Load grip, play with the ripping options (disable scratch detection, paranoia) and try ripping.

Hope that helps.[/QUOTE]


I'm trying to install grip but it's not in any of the default repos.  Do I need to add some additional repo to sources.list?  This is on a fresh breezy install.

---

### Post by shortl on 2005-10-20
Thank you all; Grip was a big part of the solution, plus I learned a lot about paranoia and cd ripping in Linux (which was the whole point).  The apt-get didn't work at first; I went to Synaptic Package ... and had to enable the Universal respository, then I could get Grip.  I am embarassed to say that another part of my problem was a scratched up cd, which with paranoia enabled made things *really* slow.  thanks again, ls

---

### Post by Purplexus on 2006-01-03
Thank You

Turning off Paranoia took my speeds from 4.5x to 11.2x

Much Better I got 200+ CD's to rip
thank god for your help

---

### Post by grumpymole on 2006-01-03
I also saw a post in another thread about the same topic that got improved CD ripping speed by using hdparm and the 'E' switch.

>        -E     Set cdrom speed.  This is NOT necessary for  regular  operation,
              as  the  drive will automatically switch speeds on its own.  But
              if you want to play with it, just supply a  speed  number  after
              the option, usually a number like 2 or 4.

The poster said that they had used something like:
  hdparm -E 24 /dev/hdc

and got improved ripping speed.

Regards

Warren

---

### Post by cvmostert on 2006-01-24
[QUOTE=GazaM]Sound Juicer also uses Paranoia by default... unfortunately the only way to change this at the moment is by going into gconf and manually editing Sound Juicer's Paranoia level. Do this as follows:
Go to Applications>System Tools>Configuration Editor... when it has opened select apps>sound-juicer and in the right panel, one of the options should be 'paranoia', what you need to do is right-click on that option, select 'Edit Key' and replace the 4 (default) to a 0 which turns off all paranoia. Turning off paranoia is fine if you're cd's are in fairly good condition and your cd drive isnt on the blink so dont worry about it, this should speed up ripping considerably ;)[/QUOTE]

thanx for the help... i turned my paranoid setting from 4 to 0 and now it rips at an even slower 0.9x !

i will try and check all the settings...
ciao

---

### Post by johanPO on 2006-01-25
I have just started ripping my cd collection with grip. I have changed the rippers with various speeds. This morning I changed to cdda2wav and had was ripping at 20x, since my processor is not the newest it could only code with 10x, so the wav files were piling up and the processor glowing. What I find strange is that now, in the afternoon I can only ripp at 6x. Does anyone have any idea why this could be? I would hate to have to restart the PC to see if it improves after a reboot.

I just rebooted and now I am ripping at 20x again. Ideas anyone?

Now I am back to slow ripping. It seems that at some spot some files does not get converted, I can only see the wav files. I assume that at that point grip is starting to make trouble.  Can't find any processes that looks like they are connected to grip. If I now start grip, It states that I am ripping with -3000x and the conversion is not working

rgds
Johan

---

