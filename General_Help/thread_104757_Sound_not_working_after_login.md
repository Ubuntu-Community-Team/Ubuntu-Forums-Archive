---
title: "Sound not working after login"
date: 2005-12-16
forum: General Help
---

### Post by jschupbach on 2005-12-16
I just installed Ubuntu Breezy (5.10) onto my computer a couple of days ago.  I am very impressed; everything works ... but the sound.  When I boot my computer I get the sound byte at the login screen (african drums ?); however, thereafter I get no sound at all.

Here is some info:
'lsmod | grep snd' gives me:
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

'aplay -l' gives me:
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This seems strange I think because I actually have a AC'97 sound card; not an intel.

'lspci|grep audio' gives me:
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

In alsamixer, I have all channels unmuted but the 'headphone jack sense' and 'line jack sense' (I have tried to unmute these as well, but to no avail).  I have tried about everything I could find to try on these forums and still have no sound.  Does anyone have any idea what could be going on here?  I appreciate any help I can get as I am a linux novice.

---

### Post by jschupbach on 2005-12-17
Here is a bit of additional info for use in trying to diagnose the problem:

When I try to play a file in totem, I get the following error message:

"Totem could not startup:  The audio output is in use by another application. Please select another audio output in the Multimedia Systems Selector. You may want to consider using a sound server."

Can anyone help?

---

### Post by Zimmer on 2005-12-17
Have a look at my post #2 here:
[http://ubuntuforums.org/showthread.php?t=95947](http://ubuntuforums.org/showthread.php?t=95947)
and see if that helps..
First try disabling sound events 
System >Preferences >Sound         menu.
and see if XMMS will work... try twice...

Zimmer

---

### Post by jschupbach on 2005-12-17
thanks for the help zimmer.  unfortunately, no luck.  i disabled the sound events and restarted the computer; went through this process twice and still get the same error message.  by the way, in my multimedia systems selector, i currently have my output and input both set for ALSA.  Is this OK?  Also, whenever i try to test the input or output for ALSA or for any other setting, i get the following error message:

Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
or...
Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'
etc...

another thing to consider: even though i have the sound events disables, i still do get the bongo drums noise on the ubuntu login screen.

---

### Post by jschupbach on 2005-12-17
when i try to play a short video clip in totem, i get this message not - a different message than before:

There were no decoders found to handle the stream, you might need to install the corresponding plugins

thoughts?

---

### Post by Zimmer on 2005-12-17
Have a read of this thread...
[http://ubuntuforums.org/showthread.php?t=87849](http://ubuntuforums.org/showthread.php?t=87849)
and if that does not produce results....
If it is any consolation I get the same errors regarding pipelines when I have tested...but I do have sound working  ????
Have you seen this?
[http://makuchaku.info/amnesty/#configuresoundproperly](http://makuchaku.info/amnesty/#configuresoundproperly)
Have you expanded your repositories...(ouch! that sounds painful :)  )
[http://makuchaku.info/amnesty/#extrarepositories](http://makuchaku.info/amnesty/#extrarepositories)     
   
With the 'no decoders loaded'  error.....
Have you then installed the necessary gstreamer0.8 plugins (that is a metapackage which installs many individual gstreamer plugins in one go..and then Synaptic will show each one individually)...?
Check which totem packages you have in Synaptic.
I have totem and totem-xine.

As I wrote in that other thread..Sound in Ubuntu seems a bit of a black art...

Regards

Zimmer

---

### Post by jschupbach on 2005-12-18
all good suggestions zimmer!  unfortunately, again, no luck.  this is really silly; i am sure the fix ultimately is simple and quick.  Can you think of any other suggestions?  Thanks for the help!  I have by the way expanded my repositories (it was surprisingly pain free!) but here is where my novice-ness comes in to play.  I am not sure exactly how to go about installing the gstreamer0.8 plugins?

---

### Post by Zimmer on 2005-12-18
Well..
System>Administration>Synaptic Package Manager.
(your very own software supermarket !)
enter your User password..
now, either scroll through the packages list until you encounter gstreamer0.8-plugins, or use the search facility to reach them ...
If the Status box on the left of the package is not Green, then it is not installed.
Mark the checkbox aginst that one package and click the  'Apply' button at the top of the screen.
Synaptic will then load the meta package, which consists of many of the commonly used gstreamer plugins. (but not ALL of them.) and will turn their status boxes Green (Installed).
This is (to me) the easiest and safest way to load all software packages.
As you have probably now realised you can search the package manager for all manner of software and just check the status box to install ........

If you ever require any more plugins just check the status box and install them.

As you are in the 'land of the Free' (ah that brought back memories.. a Davy Crockett coonskin hat circa 1960..)
 you had better read this....
[http://www.ubuntuforums.org/showthread.php?t=102884](http://www.ubuntuforums.org/showthread.php?t=102884)

Here's hoping this is of use....

Regards
Zimmer

---

### Post by this213 on 2005-12-24
Just for laughs:
```
# cat /proc/asound/cards
```
Take note of the number at the beginning (left) of the line that lists your card, then:
```
# cat /etc/asound.conf
```
There should be (at least) 2 lines in there (I don't use Ubuntu, so I'm not sure what exactly is in there):
```

defaults.ctl.card 0
defaults.pcm.card 0
```
If there's a 0 at the end (as above), change it to match the card ID as it was listed in /proc/asound/cards.

If you have a file at ~/.asoundrc delete it as this will override the global configuration in /etc/asound.conf

Hope this helps

---

### Post by jschupbach on 2005-12-28
thanks for the help.  it looks like the number at the left is '0'.  here  is the output for cat /proc/asound/cards:

0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with AD1981B at 0xd0180000, irq 10

...and I think that the numbers match wherever they need to, as there is a '0' everywhere it looks like there needs to be.  The output from cat /etc/asound.conf:

pcm.card0 {
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
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

---

