---
title: "Integrated Audio? How to configure? Dell Inspiron 6400"
date: 2007-12-16
forum: Dell  Ubuntu Support
---

### Post by crazyfish666 on 2007-12-16
I recently started on Ubuntu (my first try at Linux) with Feisty Fawn and then upgraded to Gutsy Gibbon, on both installations I did not have to do anything to get perfectly functional sound, but my microphone was not recognized and would not function with my skype program. I didn't get around to really trying to fix the mic problem untill yesterday on Gutsy and carried out the steps outlined here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) based on a recommendation I found to someone else on this forum. I got through the "Update to the Latest Version of ALSA" section fine and rebooted (when I logged back on from the reboot I had no sound, but put this down to being in the middle of configuring alsa), but when I tried to do the "Manually Specify Module Parameters" section I began to run into preblems. I inputted 
> cat /proc/asound/card0/codec#* | grep Codec
but it came back with 
> cat: /proc/asound/card0/codec#*: No such file or directory

and I tried to find out my card another way by inputting 
> aplay --list-devices
and I got back
> aplay: device_list:205: no soundcards found...
which I took to mean that because my laptop came with integrated audio I don't have a sound card and thus will have to edit the code slightly (a problem for me as a major newby). I then skipped to the next step and inputted
> /usr/src/2.6.22/Documentation/sound/alsa/ALSA-Configuration.txt
for which it came back with
> bash: /usr/src/2.6.22/Documentation/sound/alsa/ALSA-Configuration.txt: No such file or directory
it replied in the same way when I replaced the kernel number with "2.6.22-14" and then with "2.6.22-14-generic"
So I followed this [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) link from the original site, but in all honesty I have no idea what to do with the info I found there.
So basically whereas I started with audio but no mic I now have neither audio nor a mic and definitely need the former. 
Any ideas as to what to do??

Edited to add: I am on a Dell Inspiron 6400

---

### Post by crazyfish666 on 2007-12-16
Ok, so I feel like I may be getting somewhere, but I am still very confused. I ran lspci and the result gave this
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

So I looked at the link on the page detailing the original command script I am trying to follow and it says this
> Module snd-hda-intel
	  --------------------
	
	    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
			ATI SB450, SB600, RS600,
			VIA VT8251/VT8237A,
			SIS966, ULI M5461
	
	    model	- force the model name
	    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
	    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
	    single_cmd  - Use single immediate commands to communicate with
			codecs (for debugging only)
	    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)
	
	    This module supports one card and autoprobe.
	
	    Each codec may have a model table for different configurations.
	    If your machine isn't listed there, the default (usually minimal)
	    configuration is set up.  You can pass "model=<name>" option to
	    specify a certain model in such a case.  There are different
	    models depending on the codec chip.
with a list of model names and descriptions after it, but none of the model names seem to match my comp as far as I can tell. The only Dell model listed is the Dell XPS M1210 should I use the model for that (it is simply "dell")

---

### Post by crazyfish666 on 2007-12-16


Ok, and to add to that something very very odd just happened, I backspaced too far in the terminal window until I was backspacing nothing and my computer beeped at me. Before I lost sound I was never able to get it to stop the beeping when I turned it to mute, and it seems that losing sound altogether hasn't stopped it either so my computer must still be communicating with the speakers somehow, it just won't communicate anything other than its automatic basic functions.

---

### Post by m94mni on 2007-12-17
The beep is a different thing - not handled by the sound card...

Anyway, there's a whole lot of things that can start to go wrong. I have upgraded to latest alsa this way several times, so it's not like it's impossible either.

It seems your sound module is not installed. I had this problem recently, and it turned out the alsa install did not clean all versions of the hda intel driver.

Try:

$ find /lib/modules/ -name *hda-intel*

and if I'm right, you'll find two hits, 

/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

The second one is the one alsa installs, the first one is a bugfix update from ubuntu.

Remove the first one

sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

and then do

sudo depmod -a

and then

sudo modprobe snd-hda-intel

---

### Post by crazyfish666 on 2007-12-18
> **m94mni said:**
> 
It seems your sound module is not installed. I had this problem recently, and it turned out the alsa install did not clean all versions of the hda intel driver.

I have sound!!! :D Thank you very much, I can't believe it was that simple after trying so many things! :) Thanks.

---

### Post by m94mni on 2007-12-18
Cool, I'm glad it worked for you. ):P

---

### Post by ::Lagro on 2007-12-18
For DELL INSPIRON 6400, I just right click on the icon > Open Volume Control > Edit > Preference> and mark all radio button.
After that > Recording tab > Capture click on the microphone image to enable it!

---

### Post by crazyfish666 on 2007-12-23
> **m94mni said:**
> Cool, I'm glad it worked for you. ):P

Well it did work... now it has stopped again. And I can't think what I have done that may have effected it. I tried going back in and doing the last bit of your commands again, but it came up with an error, and of course the bit you had already asked me to remove had already been removed. I now have three items coming up for "find /lib/modules/ -name *hda-intel*" 

> /lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko


should I delete one of them?? To make it clear all of them appeared when the sound was working and I don't see any change in them since then. I have no idea what has changed.

---

### Post by m94mni on 2007-12-24
Do you have the error message?

You shouldn't have to remove anything more - the first hit is for an old kernel, the second one just an empty directory, and the third one hopefully the one you installed. Did you install a kernel update?

Try reinstalling the compiled alsa drivers...

---

### Post by crazyfish666 on 2007-12-24
> **m94mni said:**
> Do you have the error message?

You shouldn't have to remove anything more - the first hit is for an old kernel, the second one just an empty directory, and the third one hopefully the one you installed. Did you install a kernel update?

Try reinstalling the compiled alsa drivers...

Missing out the remove command this is what I get

> fae@artemis:~$ find /lib/modules/ -name *hda-intel*
/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
fae@artemis:~$ sudo depmod -a
[sudo] password for fae:
fae@artemis:~$ sudo modprobe snd-hda-intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And as far as reinstalling the alsa drivers that is what lost me my sound in the very beginning when I was trying to get my microphone working and tried to install alsa from here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) . I also tried reinstalling all the alsa stuff that I could find in Synaptic the first time I lost sound and that didn't help then, I will try it again now and put up a message after I reboot to say if it works.

---

### Post by crazyfish666 on 2007-12-28
> **crazyfish666 said:**
> I will try it again now and put up a message after I reboot to say if it works.

I thought I had already posted this, but obviously not. Anyway, it didn't work. Still no sound.

---

