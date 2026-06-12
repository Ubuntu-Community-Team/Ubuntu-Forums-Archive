---
title: "Webcam and mic Vostro 1310"
date: 2008-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keryonic on 2008-05-23
I have installed Ubuntu 8.04 and it works pretty well but I still have this problem with the webcam which stopped working after a few days and no sound can be recorded with an external or the internal microphone.

And sometimes I think Linux (Ubuntu) is too complicated compared with Windows: Some of Bluetooth funcionalities work but using a smartphone to connect to internet through a PAN is a noob's nightmare. I know it is possible writing lines in a terminal but when I do that, I don't know what I am doing and I have no idea how to undo if something goes wrong. That is how I lost the webcam and I caused a "broken pipe" (don't ask me what it is) playing with Virtualbox (which, now, works pretty well with XP).

I need help because I am desperate with the webcam. It worked, it works if I use the live CD and it works if I load kernel 2.6.24-12-generic instead of 2.6.24-16-generic (Why Ubuntu installs two kernel options for the same distro?)
The microphone is another problem and I hope somebody here could help me.

---

### Post by Keyper7 on 2008-05-23
Ubuntu does not install two kernels by default. You probably received the -16 on an update. Ubuntu lets you keep the older kernel in case something breaks in the new one and you need to boot the old one to fix it. When you're sure that -16 is working, then you can uninstall -12.

You probably only have camera drivers compiled for -12. Ubuntu usually delivers module updates for a new kernel, maybe something went wrong with the update process. Probably the updated drivers are in the repositories and could be installed manually.

For the mic, let's start with simple steps: perhaps it's simply disabled. Open the volume control (right click on the sound icon next to the clock) and check if everything is enabled and properly configured (read: with a volume high enough). Perhaps you're lucky and the problem is simply that.

---

### Post by keryonic on 2008-05-23
Thank you for your answer Keyper. How do I know which driver is used for webcam in kernel -12 and how can I use it and compile manually kernel -16 with this driver?

I checked the microphone with the tips you gave me but it didn't work. I tried with all devices listed:

1.HDA Intel (Alsa mixer); 
2.Realtek ALC268 (OSS mixer); 
3.capture: Monitor Source of ALSA PCM on front:0 ALC268 (Analog) via DMA (PulseAudio mixer)
4.capture: ALSA PCM on front:0 ALC268 (Analog) via DMA (PulseAudio mixer)

Sorry to bother you but if you or somebody else could help me, I would greatly apreciate. Regards.

---

### Post by Keyper7 on 2008-05-23
No, no, I think you clicked on the volume icon and just opened the "preferences" window. This one you don't need to fiddle with, the default option is probably fine. I'm talking about the "volume control" window (the one with a lot of volume control sliders). There should be a "preferences" window INSIDE this volume control with a lot of checkboxes, perhaps your microphone is unchecked.

About the camera, if the kernel in fact came with un update, a package with the driver might be available in the repositories. I'll do a little search and get back at you.

---

### Post by Keyper7 on 2008-05-23
Here ya go, try this:

[http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-16-generic)

This should've been installed when you received the new kernel, check if the files in the file list are not on your system already.

---

### Post by keryonic on 2008-05-24
Tx again. I have tried to copy the drivers from /lib/modules/2.6.24-12-generic/ubuntu/media/ to /lib/modules/2.6.24-16-generic/ubuntu/media/ and it didn't work so I copied the entire /media folder but it didn't work either. The question: If I copy the drivers like this is there a chance that it could work? or after copying them I need to compile the kernel (I have no idea what compiling is)?

For the sound, I did what you said but nothing worked. I'll try more.

Regards from Madrid

---

### Post by Keyper7 on 2008-05-24
Oops, I just said to check if the files were in your system already and install them if they weren't, you were not supposed to copy anything from one folder to another!

The files in /lib/modules/2.6.24-12-generic folder are the drivers for the 2.6.24-12 kernel and the files in the /lib/modules/2.6.24-16-generic folder are the drivers for the 2.6.24-16 kernel, the system reads the adequate folder according to the kernel you are loading, if you copy the files from one folder to another you mess everything up...

Now, were all the files in the list already in your system or not? If they weren't, here's what you should do:

- go to the link I gave you above
- click on the link under "architecture" according to what you use. I'm guessing you use a 32-bit Ubuntu (do you?), so click on the "i386" link.
- you'll go to a list of mirrors, click on any of them to download the package
- double-click on the package after downloading it to install the modules
- reboot and choose the 2.6.24-16 kernel

---

### Post by keryonic on 2008-05-24
Thank you for your patience. I have done like you said, I reinstalled all the drivers (downloading the package) but it didn't solve the problem. 

The strange thing is that if I copy the folder 2.6.24-16-generic from the live CD and copy it to the same folder on the hard drive. The result is that the webcam works but the whole configuration is messed up (video setting, sound, user/password account, etc...) so I changed back to the old config and I am back to square one. But now, I know there is one (or more) file that could be copied from the live CD to the hard drive and it could work leaving the original config untouched.

I will investigate more, but if you (or anybody else) have a new idea, I'll be glad to try anything.

Best regards.

---

### Post by Keyper7 on 2008-05-24
Hmm, I shooting in the dark a bit now, but try copying only

/lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko

from the liveCD. If copying the entire folder works, this might work
without messing up your settings because this is the driver module.

---

### Post by andied on 2008-05-25
I struggled a long time to get my mic working. Double click or right click the volume icon and open the volume control window. The device should be "HDA Intel (Alsa mixer), then go to edit> preferences and select (probably all of the options) and after you get the mic working you could try deselecting some, but the important options for me are  "master", "pcm" "front", "digital" and "digital input source". Now on the "recording" tab, make sure the options are enable and the volume up. Then go to the "options" tab and be sure "digital mic" is selected. Hopefully that will enable your mic.

---

### Post by keryonic on 2008-05-25
To Keyper7:
I have tried that before (copying the entire folder /lib/modules/2.6.24-16-generic/ubuntu/media/) but it didn't work. It only worked when I copied the folder /lib/modules/2.6.24-16-generic/ so I guess I should copy a driver from subfolder different than /ubuntu/media/ but I don't know which one.

To Andied:

I did what you said but it didn't work. There is one thing in your explanation that I couldn't change. You said "...Then go to the "options" tab and be sure "digital mic" is selected..." but I don't have the option "digital mic" but only "front mic".

Tx anyway for your advices. I keep investigating.

---

### Post by Keyper7 on 2008-05-25
> **keryonic said:**
> I did what you said but it didn't work. There is one thing in your explanation that I couldn't change. You said "...Then go to the "options" tab and be sure "digital mic" is selected..." but I don't have the option "digital mic" but only "front mic".

Hmm, good clue, the digital mic is not enabled... When you open the volume control and go to "edit > preferences", which checkboxes do you see?

As for the camera, I'd recommend doing an exaustive testing of which folders you need to copy and which you don't. That might give some insight into the problem.

Sorry for all the inneficient advice so far, but in the current situation it's hard to know where to attack... :(

---

### Post by keryonic on 2008-05-26
Good news! The webcam works!!! But I didn't find the problem. I just upgrade to the new kernel 2.6.24-17 (System->Software Sources->Updates I checked everything and automatically it updated my system to the new kernel. Now when I boot, in Grub, I have the option to load 2.6.24-12, 2.6.24-16, 2.6.24-17 or Vista. I need to clean that mess and will look for that later (It should be easy to fix).

After update, I had to reinstall Virtualbox because a driver was missing. That was really easy downloading the .deb following download links on [www.virtualbox.org](www.virtualbox.org). So, if Virtualbox doesn't work for you, don't mess, try to reinstall the last version and it might work out of the box like it does for me.

BUT the mic is still dead!!! Here is my config in Volume Control:

Device: HDA Intel (ALSA mixer)
Preferences: all checked (Master,Headphone, PCM, Front, Front Mic Boost, Capture, Capture 1, Digital, Input Source, Input Source)
Playback tab (all up): Master, Headphone, PCM, Front, Front Mic Boost
Recording: Capture (up), Capture 1 (down because if it is up there is a clicking noise when I playbak), Digital (up)
Options: 
Input Source: Front Mic (no other choice)
Input source: Front Mic (same as above, no other choice)

In system->Preferences->Sound Preferences: Autodetect for all. Sound Capture: ALSA, Device: HDA Intel (Alsa mixer).

I am quite desperate and will try any suggestion.

---

### Post by keryonic on 2008-05-26
I found it very easy to edit Grub. Just edit /boot/grub/menu.lst (# sudo gedit /boot/grub/menu.lst). Now when I boot, I only have the choices I really need.

---

### Post by Keyper7 on 2008-05-26
That's weird, you're supposed to have "Digital Input Source" among the checkboxes in preferences...

I'll have to do a little research.

---

### Post by keryonic on 2008-05-27
I begin to become desperate. I think I am the only one on the planet who installed ubuntu 8.04 to a Vostro 1330. It seems that  Linux-backports-module fixes the problem with most Dell computers but not mine. It should work if I could activate "digital mic" in "input source" in Gnome volume control but (in input source) I only have the option "front mic" (twice).

---

### Post by Keyper7 on 2008-05-27
Okay, keyronic, I won't give up on you. :)

Could please find out the details of your sound board? You might find out on system> preferences > hardware information.

Once we have the exact model, we can find out if the current version of the alsa drivers is supporting it.

I did some research and found out that the 1310 is quite a recent model, that might be the problem.

When I bought my 1400 (in January), support for my microphone had just been incorporated into Ubuntu. Gutsy didn't have it but Hardy did.

---

### Post by keryonic on 2008-05-28
CPU: Intel® Core&#8482; 2 Duo T8100 chipset Intel PM965/GM965/GL960. 

Multimedia Controller Intel 82801H (ICH8 Family)HD Audio Controller (rev 3)

I hope this is the information you need. I have read and tried many things I found on the web but I am still looking. I will post the solution if I find it.

Thank you to not let me down.

---

### Post by Keyper7 on 2008-05-29
Could you please post the sub-itens of the "HD Audio Controller" item? Copy-paste might not be possible so you might have to type the itens manually, sorry for that.

I really want to help you, but like I said, be prepared for the possibility that your mic simply isn't supported yet (but don't be desperate if that's the case, I doubt it would be long before alsa starts supporting it).

---

### Post by keryonic on 2008-05-29
Subsystem for sound card is "Dell unknown device 026f". I am not sure it will help you much. Anyway, thanks for your support and patience. I guess I will have to wait for an Alsa new release.

---

### Post by Keyper7 on 2008-05-31
Yeah, I just realized that the hardware info app doesn't detect my card properly either.

I did some googling on the Vostro 1310, but had no success.

Perhaps your manual has this hardware info?

---

### Post by keryonic on 2008-06-03
Hi Keyper7,
I don't find that information but I see more and more people having the same problem with XPS M1330, Vostro 1400 and others which must have the same hardware. I seems there is no solution at that time with Hardy Heron. I find it very strange that Dell offers the XPS M1330 with Ubuntu 7.10 and doesn't provide support and solution for 8.04. Imagine people buying a Dell with Vista and the microphone doesn't work after an upgrade!! That would cause a revolution!

---

### Post by Keyper7 on 2008-06-03
The Vostro 1400 mic is supported by Hardy, I know because I have one. :)

Thing is, I know that my sound chipset is "STAC 9228" and it was not difficult to find out this with Google and discover that alsa supports it, but I wasn't able to do the same thing with your 1310, Google didn't help. :(

---

### Post by keryonic on 2008-06-04
I found this about my soundcard but I am not sure it would help:

Realtek High Definition Audio

PCI\VEN_8086&DEV_284B&SUBSYS_026F1028&REV_03\3&21436425&0&D8

hdaudio\func_01&ven_10ec&dev_0268&subsys_1028026f

HDAUDIO\FUNC_01&VEN_10EC&DEV_0268&SUBSYS_1028026F&REV_1000\4&FAAE6E&0&0001

---

### Post by Keyper7 on 2008-06-05
Based on some small researchs, I'm almost sure your card chipset is also a STAC9XXX. If you could find out what XXX is, it might be helpful.

---

### Post by jhwilliams on 2008-06-08
The audio chipset in the Vostro 1310 is a Realtek ALC268:

jameson@salmon:~$ aplay -L
default:CARD=Intel
    HDA Intel, ALC268 Analog
    Default Audio Device

The microphone is not working for me either.

---

### Post by keryonic on 2008-06-09
Here is the info on my soundcard (this info can be obtained with the command "cat /proc/asound/oss/sndstat") 

Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux kerdel 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xf8300000 irq 22

Audio devices:
0: ALC268 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC268

---

### Post by keryonic on 2008-06-09
I have just received an email from Dell and they told me that the soundcard model for my Vostro 1310 is SigmaTel® STAC9205

---

### Post by Keyper7 on 2008-06-10
Can you confirm the model by running alsamixer?

I just remembered it also shows up there.

---

### Post by pilothaz on 2008-06-10
Gentlemen,
i have this laptop now as well and I will be taking my wubi to a full install (I was just trying it out for the sake of installing it in windows :))  I usually have ubuntu on all my laptops.

I recently purchased and received my vostro 1310 so you are not alone.  I will try and work through this tonight, as I also want to get the wireless working for the Broadcom N wireless card.

---

### Post by keryonic on 2008-06-11
Welcome to the club. Don't hesitate to post if you have any problem maybe I can help (but don't ask for the moon, I am noob).

---

### Post by pilothaz on 2008-06-16
Do you have your wireless working for your laptop?  I decided to get the Broadcom (Dell) 1505 instead of the Intel.  After thinking about it that was the stupidest thing I have done, as I totally forgot that broadcom don't open their drivers.  

I have to go through and get that working still.  I have not gotten around to trying to get the webcam and mic working.  But I do know that it is not showing up as digital input for the mic (I didn't see that on the sound mixer).

---

### Post by keryonic on 2008-06-16
I have the Intel wifi card and it works fine. 

I removed the nm-applet and changed it for Wicd because I was tired of entering keyring password and now it works perfectly. 

I had fun hacking the wiimote ([http://wiki.wiimoteproject.com/Main_Page](http://wiki.wiimoteproject.com/Main_Page))

Webcam still doesn't work. I don't have any hope.

---

### Post by elastigirl on 2008-06-30
Cant beleive the solution was so simple, I am glad I did not try anything complicated first! Thanks Andied!

Just FYI, I am using the Vostro 1400 with Hardy and this solution worked perfectly for me.

Thanks again!

---

### Post by elastigirl on 2008-06-30
> **andied said:**
> I struggled a long time to get my mic working. Double click or right click the volume icon and open the volume control window. The device should be "HDA Intel (Alsa mixer), then go to edit> preferences and select (probably all of the options) and after you get the mic working you could try deselecting some, but the important options for me are  "master", "pcm" "front", "digital" and "digital input source". Now on the "recording" tab, make sure the options are enable and the volume up. Then go to the "options" tab and be sure "digital mic" is selected. Hopefully that will enable your mic.

Sorry...The above message was in reply to this quote!

---

### Post by halln on 2008-07-04
> **andied said:**
> I struggled a long time to get my mic working. Double click or right click the volume icon and open the volume control window. The device should be "HDA Intel (Alsa mixer), then go to edit> preferences and select (probably all of the options) and after you get the mic working you could try deselecting some, but the important options for me are  "master", "pcm" "front", "digital" and "digital input source". Now on the "recording" tab, make sure the options are enable and the volume up. Then go to the "options" tab and be sure "digital mic" is selected. Hopefully that will enable your mic.

Thanks for this post. It helps my mic problem.:KS

---

### Post by macross3003 on 2008-07-09
New member of the Vostro 1310 (+ webcam) here :(
Same issues, no webcam (it works under fedora) and no mic.

---

### Post by Mal__ on 2008-07-09
I've just bought a new vostro 1310 too and installed 8.04 on it.  I had the webcam working straight from the install but the mic doesn't work (both internal and external).

macross3003 what version kernel do you have? keryonic fixed the webcam problem by updating that (although that was on May 26th) so it might work for you.  If not I'm sorry I can't help I'm rather new to this linux jazz!

I've rather blindly followed quite a few guides on fixing this microphone problem, to no success.  I thought I had done it when I followed the advice from hyperandy on this thread: [http://ubuntuforums.org/showthread.php?t=707231&highlight=ICH8+sound]("http://ubuntuforums.org/showthread.php?t=707231&highlight=ICH8+sound")  but the last bit of code wouldn't work as I didn't have the files (or even folders!) there to copy across...  I admit I didn't really know what I was doing so that link might help someone else who knows what they're doing.  Other than that, I too shall wait to see if a solution emerges.

---

### Post by keryonic on 2008-07-12
I have not found a solution yet for the Mic but the webcam works (it worked straight from first install but then I messed up and - I don't remember how - I reinstalled the kernel.

I have searched extensively and never found a solution for the mic!!!!!!!!!

---

### Post by stepdown on 2008-07-27
> **keryonic said:**
> I have just received an email from Dell and they told me that the soundcard model for my Vostro 1310 is SigmaTel® STAC9205I'm having the same issues with a Sigmatel STAC9205 here, if I find anything to fix it, you'll be the first to know! :)

---

### Post by keryonic on 2008-07-29
Thanks Stepdown, I hope your search will be more successful.

I have messed up again with my Ubuntu install when I reinstalled Vista on another partition. It erased MBR and tried to recover with Supergrub but had no success. The startup menu with choice Linux - Windows reappeared but I can't login because it doesn't find my home directory which is on another partition. 

I am quiet disappointed with Ubuntu. It works quiet well once tuned up (lot of time needed) but when something goes wrong it is not always easy to find a solution despite goodwill on forums. Also, I never found a solution for the mic. Since I need to work and I don't want to waste more time, I am back to Windows...Vista. But I certainly will keep an eye on Linux (and on this thread. I wish I could find a solution for that damned mic.)

Regards to all.

---

### Post by stepdown on 2008-07-30
Okay, I've got the mic working now! :D

I tried getting the new ALSA installed, version 1.0.17, but that didn't help, so I reverted back to version 1.0.16 that I believe is included with Hardy Heron.

Anyway, trick for me was going into Sound Preferences (System > Preferences > Sound) and then changing everything in there from the normal "Auto detect" settings, to "ALSA - Advanced Linux Sound Architecture".

Hope this is of some help :)

---

### Post by keryonic on 2008-07-30
I reinstalled Ubuntu and it was much easier than I thought because my /home directory was on another partition so most of my previous tweaks reapeared. This is a nice feature in Ubuntu (Linux).

Stepdown, could you explain how you reinstalled Alsa 1.0.16? When I call Alsamixer in terminal, the version is 1.0.15 but in synaptics I see something like Alsa Base 1.0.16 installed. In [www.alsa-project.org](www.alsa-project.org), I see there is a lot of files that can be installed: driver, utils, tools, firmware,... What exactly did you install and how (from source or through repository?)

Thanks for your help.

---

### Post by Keyper7 on 2008-07-30
keyronic,

First of all, sorry I disappeared. I forgot to check on the Dell part of the forums for a while.

Second, from what I did understand of stepdown's post, it was not reinstalling 1.0.16 that solved the problem (he only did that to get rid of a failed attempt to install 1.0.17). It was the changes on sound preferences he mentioned above. See if that works for you (and since you reinstalled Ubuntu, don't forget to check again if nothing in the volume control is disabled or muted). Also, how are you testing the mic when you try something?

---

### Post by keryonic on 2008-07-31
Hi Keyper7, Nice to see you again.
I tried exactly what Stepdown said, but it didn't work. I've tried everything with the untouched Alsa freshly installed coming with Hardy Heron (final release) but I probably miss something. I feel we are very close to a solution. Thanks for your support and regards from sunny Madrid.

---

### Post by Keyper7 on 2008-07-31
stepdown, since you seem to have exact same board as keyronic, I think it might be worth a shot asking for your *exact* sound settings just to make sure that keyronic didn't skip anything. Could you please post them?

keyronic, could you tell me how are you testing the mic? Perhaps that might be an issue with the recording software you are using?

---

### Post by stepdown on 2008-07-31
> **Keyper7 said:**
> I think it might be worth a shot asking for your *exact* sound settings just to make sure that keyronic didn't skip anything. Could you please post them?More than happy to help in any way possible, where would I go to get a printout of the exact settings, or would screen dumps suffice?

---

### Post by Keyper7 on 2008-07-31
The less hassle for you, the better, so I think screenshots would suffice.

I think it would be good to start with:

volume applet > preferences
volume applet > volume control > edit > preferences
volume applet > volume control > keys
volume applet > volume control > options
system > preferences > sound (default tab)

Sorry for all this work, but I'm with keyronic since the beggining of the thread and I'm starting to take it as a matter of honor. :)

---

### Post by keryonic on 2008-08-01
Hi Keyper7,
Hi Stepdown,

First of all, thanks for your patience with me :)

I use Gnome-Sound-Recorder 2.22.0 to test the mic.

Here are the options I can tune up.

1. Volume applet -> Preferences:
 I can choose: 
HDA Intel (Alsa Mixer) (...I think this is the one to choose)
Channels available: Volume Control, Headphone, PCM, Front, Font Mic Boost, Record, Record 1, Digital (I think Digital is the one needed)

Realtek AC268 (OSS)
Channels: Volume, PCM-2, Input Gain

Playback ALSA PCM on Front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
Channel: Master

Capture: Monitor Source of ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
Channel: Master

Capture ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
Channel: Master

In "Edit Preferences" everything is checked: General Volume, Headphone, PCM, Front, Front Mic Boost, Recording, Recording 1, Digital, Input source, Input Source (twice). 

In Volume Control 

2. First tab "Playing" (I am not sure of the english word because I installed Ubuntu in french)
General Volume, Headphone, PCM, Front, Front Mic Boost are all up

3. Second tab "Recording"
Recording and Recording 1 are set to 0 (minimum) and Digital at max.

4. Third tab "Options"
I see Input Source twice and the only choice I have for each Input Source is Front Mic (I have read that some folks can also choose Digital but I don't have that option).

5. In system > preferences > sound: Everything is set to ALSA and Default Channel Mixer is set to HDA Intel (Alsa mixer)

Thanks again for your time.

Regards.

---

### Post by Keyper7 on 2008-08-01
> **keryonic said:**
> 4. Third tab "Options"
I see Input Source twice and the only choice I have for each Input Source is Front Mic (I have read that some folks can also choose Digital but I don't have that option).

Yeah, there's something missing here. You're supposed to have "Digital Input Source" in addition to the other two "Input Source". Let's wait and see what stepdown has in this tab.

---

### Post by stepdown on 2008-08-03
Sorry, was away over the weekend. Back now with some screen dumps for you :)

**Volume Settings**
[IMG]http://xs130.xs.to/xs130/08310/a956.png[/IMG]

[IMG]http://xs130.xs.to/xs130/08310/b742.png[/IMG]

[IMG]http://xs130.xs.to/xs130/08310/c667.png[/IMG]

[IMG]http://xs130.xs.to/xs130/08310/d215.png[/IMG]

**Sound Settings**
[img]http://xs130.xs.to/xs130/08310/lol722.png[/img]

---

### Post by Keyper7 on 2008-08-03
Sweet! Thank you very much, stepdown!

keyronic, any noticeable difference? Obviously there's the Digital Input Source thing...

---

### Post by cagcag on 2008-08-04
Hi!

Could you please look into your /etc/modprobe.d/alsa-base ?
There could be a line somewhat like:
```
options snd-hda-intel model=dell
```
I would really appreciate to know what model you use..

Thanks

btw: How did you update ALSA? I tried to do so, but still the old modules of 1.0.16 are used..

---

### Post by keryonic on 2008-08-04
Hi Keyper7 and Stepdown,
I am on vacation right now and my Ubuntu partition is corrupted :(
I'll find time to reinstall and will be back with you soon. But one thing I am sure is that I don't have a tab named "switches". Thank you for your help

---

### Post by R%&amp;92GH&amp; on 2008-08-05
keryonic, when you say that your microphone is working, do you mean the internal micro or the external one?

I still havn't tried to plug an external micro, but I've been struggling with the internal one without any success (just horribles noises coming from the speakers).

In my case, I'm using a Vostro 1510, but I think the problem is exactly the same (although my webcam worked out of the box).

---

### Post by stepdown on 2008-08-05
> **marcpalaus said:**
> In my case, I'm using a Vostro 1510, but I think the problem is exactly the same (although my webcam worked out of the box).Do you know which card you've got? I managed to get my Sigmatel STAC9205 making some horrible noises when I turned up the volume on the Mux channels I think, just sounded like a whole load of static coming out.

---

### Post by lbdan on 2008-08-05
Hi there, just want to add my voice here. I've been setting up Hardy on my new Vostro 1510 and I can't get the microphone going either. According to alsamixer my card is a Realtek ALC268. Like other posters, I don't see any other choice under 'Options' than 'Front Mic' for 'Input Source'.
Dan

---

### Post by cagcag on 2008-08-05
Hi!

If you can see only one possible input, have a look at 
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz 
and try changing it in /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=dell
```

Like that, I got other input choices..

---

### Post by R%&amp;92GH&amp; on 2008-08-05
Like lbdan, I have the Realtek card (don't know if it is exactly the same model, as I don't have the computer with me now, but I think it is), and I can only see one input source, too.

This afternoon I'll try to modify the alsa-base file and I'll post the results.

Marc

---

### Post by R%&amp;92GH&amp; on 2008-08-05
Ok, I tried to put this
> options snd-hda-intel model=dell

in /etc/modprobe.d/alsa-base and now I can choose the input source between: Mic, Front Mic, Line and CD. I suppose the internal mic is the "Front Mic" but I'm not sure.

I tried several combinations, but I still only hear noise...

PS: my card is a HDA Intel with the Realtek ALC268 chipset

---

### Post by yeus on 2008-08-17
> **marcpalaus said:**
> Ok, I tried to put this


in /etc/modprobe.d/alsa-base and now I can choose the input source between: Mic, Front Mic, Line and CD. I suppose the internal mic is the "Front Mic" but I'm not sure.

I tried several combinations, but I still only hear noise...

PS: my card is a HDA Intel with the Realtek ALC268 chipset

I am exactly in the same situation as all the users above vostro 1310 with that soundcard having all the same issues and same settings and mixer-configuration...

Has there been any progress on this yet?

greetings, tom

---

### Post by macross3003 on 2008-08-18
using version 1.0.17-1 ([http://packages.debian.org/experimental/libasound2](http://packages.debian.org/experimental/libasound2)) under debian sid, still doesn't work.
:(

---

### Post by rpwaf on 2008-08-20
ok I've try everything in all the post in that thread because I want my mic to work. 

Probably it's a combination of all the sugestion that work. I was at the last post saying that modify did'nt change anything I was a bit disapointed.

> options snd-hda-intel model=dell 


Good news is that IT'S WORK FOR ME! After adding that line in the sugested file and a reboot it works yes!!! 
The big noise you mention was cause by the capture 1 device. You must disable the Capture 1. That's what cause the very disturbing blik blik blik noise for me. 

Only thing that did'nt work for me is my Dell wifi card (no webcam, no blue tooth, no external mic) I will probably find the solution on another post. 

Thanks to everyone to persist to find a solution for the mic. Your help was really apreciated.

---

### Post by pilothaz on 2008-08-21
I got the webcam to work,

[http://linux-uvc.berlios.de/#download](http://linux-uvc.berlios.de/#download)

for instructions use this:
[http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS](http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS)

But i can't get my mic to work or my sound in general.  This is starting ot piss me off.  All I get is pulses with some sound coming out for the audio when things are on my pc.   

Any help?

---

### Post by nana147n on 2008-08-22
Hi!
I just bought Dell Vostro 1310 (really like it :grin: ) and I installed Ubuntu 8.04 on it ...My Webcam is working - with Cheese and Skype I have no problems. But my mic isn't working at all... I read all of what you wrote and I have the same problems... just want you to know - I'm reading carefully and waiting for a solution... Until then my skype contacts will only see me without hearing... :cry::(

---

### Post by cRoMo on 2008-09-05
The fix, or rather a workaround, for mic problem is described by me here: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972/comments/21](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972/comments/21) .

---

### Post by yeus on 2008-09-07
> **cRoMo said:**
> The fix, or rather a workaround, for mic problem is described by me here: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972/comments/21](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/188972/comments/21) .

the next kubuntu/ubuntu has that kernel version included right? i think I am going to wait for 8.10 then...

---

### Post by saffagirl on 2008-09-23
Another one to the club I'm afraid ;)

Although i've got the sound and mic working (if a bit quietly), but still I can just about manage without a webcam.

---

### Post by Ronen the II on 2008-09-28
> **pilothaz said:**
> Do you have your wireless working for your laptop?  I decided to get the Broadcom (Dell) 1505 instead of the Intel.  After thinking about it that was the stupidest thing I have done, as I totally forgot that broadcom don't open their drivers.  

I have to go through and get that working still.  I have not gotten around to trying to get the webcam and mic working.  But I do know that it is not showing up as digital input for the mic (I didn't see that on the sound mixer).


Did you manged to get the Wifi-Card work? They Do not sell Vostro with Intel card here, So I have to get the "Dell" card if I want a Vostro at all.

---

### Post by yeus on 2008-09-28
> **Ronen the II said:**
> Did you manged to get the Wifi-Card work? They Do not sell Vostro with Intel card here, So I have to get the "Dell" card if I want a Vostro at all.

yeah i accidently bough this dell wifi card, too. but works without any problems.

---

### Post by Ronen the II on 2008-09-29
> **yeus said:**
> yeah i accidently bough this dell wifi card, too. but works without any problems.


Thanks, So I can buy it with out fear.
Did you use native driver or ndiswarpper driver?

---

### Post by yeus on 2008-09-30
> **Ronen the II said:**
> Thanks, So I can buy it with out fear.
Did you use native driver or ndiswarpper driver?

I used the proprietary driver that was proposed by my kubuntu installation automatically and it shows up under SystemSettings->Hardware Drivers manager...  don't know whether its "native" or using the ndis wrapper. I think it was automatically installed with the first online-update of ubuntu. All I know is, that it worked fine for me witout having to configure antyhing by myself :)...

Greetings, Tom

---

### Post by saffagirl on 2008-10-01
> **Ronen the II said:**
> Thanks, So I can buy it with out fear.
Did you use native driver or ndiswarpper driver?

I had quite a bit of hassle , but there's a test wifi driver which seems to work (although seems to time-out.)..not using ndiswrapper.

Anyone got the webcam to work yet? I'm struggling....

---

### Post by sibidiba on 2008-10-05
Lot of people experience problems with various codecs using snd-hda-intel.

I have set up this page to summarize the problems:
[https://wiki.ubuntu.com/SndHdaIntelSoundProblems](https://wiki.ubuntu.com/SndHdaIntelSoundProblems)

Bugs are only related if they are for the same module and codec/chipset:

cat /proc/asound/card*/codec\#*|grep -i codec

---

### Post by jesuisbenjamin on 2008-10-09
Hey there,

Can i join the club with my Vostro 1510? So if i understand there is no solution for internal microphone not working, nor any workaround?

---

### Post by R%&amp;92GH&amp; on 2008-10-09
> So if i understand there is no solution for internal microphone not working, nor any workaround? 

It seems that it will be solved with the new kernel (in ubuntu 8.10 maybe). Let's wait a little bit...

---

### Post by saffagirl on 2008-10-10
> **jesuisbenjamin said:**
> Hey there,

Can i join the club with my Vostro 1510? So if i understand there is no solution for internal microphone not working, nor any workaround?


I think the 1510 and 1310 have the same hardware. I got both mics and sound working with this thread thanks to vignayni... my only complaint is the sound is v. quiet , (on an already quiet machine) but can still hear.

I really hope that a lot of our bugs are ironed out in 8.10, there've been quite  a bit.
[http://ubuntuforums.org/showthread.php?t=878608](http://ubuntuforums.org/showthread.php?t=878608)

---

### Post by _serenity on 2008-10-12
I got the mic working by using kernel 2.6.27 (kernel.org)

Compiling your own kernel might be a little too difficult for beginners, but at least it means they got it fixed and newer distros will include newer kernels so.. :KS

---

### Post by yeus on 2008-10-22
Got it working on the new kernel, too...  (using the beta version of kubuntu 8.10)

---

### Post by ispmarin on 2008-11-09
Don't know if can be of much help, but just to report: running debian sid, kernel 2.6.26-1-amd64, everything worked out of the box. Didn't tried the last ubuntu on my 1310.

---

### Post by skiold on 2008-11-09
Hi, everybody.
Finally I could fix the internal microphone.
I upgrade the whole system with a clean installation with 8.10 but 32 bits now. After that, I modified alsa-base file with this option:

> options snd-hda-intel model=acer

And finally I configured my input device as ALSA PCM

---

### Post by R%&amp;92GH&amp; on 2008-11-10
With ubuntu 8.10, both microphones (built-in and external) work out of the box, but you must adjust the volume first. 

In the "recordin"g settings, put "capture" and "capture 1" to the 90% (at 100% they do not work), and in "options", select "mic" in both input sources.

It is not necessary to modify the /etc/modprobe.d/alsa-base file at all

If you upgraded to ubuntu 8.10 from a previous instalation, just run:
> sudo apt-get install --reinstall  linux-image-$(uname -r)
in order to reconfigure the soundcard.

The solution that worked for saffagirl, didn't work for me.

---

### Post by yeus on 2008-11-14
Now after all the sound-problems have been solved, I got a new Problem with my dell vostro 1310 on the new 8.10 distribution. And that is the birghtness of my LCD-screen it just randomly drops to 0% from 100% all the time.. I have no idea, what's going on.. sometimes it stays on 100% for 2 hours or so... sometimes only 5 minutes...  any idea whats going on? I didn't have that problem on hardy....

greetings, tom

---

### Post by swiftarrow on 2008-11-28
> **keryonic said:**
> I think I am the only one on the planet who installed ubuntu 8.04 to a Vostro 1330.

LOL... I feel your frustration.
Glad to see some solutions here.
Will be upgrading to intrepid if that works oob...

---

### Post by saffagirl on 2008-11-28
I've just updated to hardy kernel -22. Anyone elsehave massive issues with this( and the previous kernel)? Sorry I know it's off topic- but I know we've all got pretty much the same hardware.

---

### Post by saffagirl on 2008-11-28
> **yeus said:**
> Now after all the sound-problems have been solved, I got a new Problem with my dell vostro 1310 on the new 8.10 distribution. And that is the birghtness of my LCD-screen it just randomly drops to 0% from 100% all the time.. I have no idea, what's going on.. sometimes it stays on 100% for 2 hours or so... sometimes only 5 minutes...  any idea whats going on? I didn't have that problem on hardy....

greetings, tom

Mine actually does that a lot too, it's really annoying. Mine drops in hardy though? Who knows.

---

### Post by pookito on 2008-11-28
> **keryonic said:**
> I have installed Ubuntu 8.04 and it works pretty well but I still have this problem with the webcam which stopped working after a few days and no sound can be recorded with an external or the internal microphone.

And sometimes I think Linux (Ubuntu) is too complicated compared with Windows: Some of Bluetooth funcionalities work but using a smartphone to connect to internet through a PAN is a noob's nightmare. I know it is possible writing lines in a terminal but when I do that, I don't know what I am doing and I have no idea how to undo if something goes wrong. That is how I lost the webcam and I caused a "broken pipe" (don't ask me what it is) playing with Virtualbox (which, now, works pretty well with XP).

I need help because I am desperate with the webcam. It worked, it works if I use the live CD and it works if I load kernel 2.6.24-12-generic instead of 2.6.24-16-generic (Why Ubuntu installs two kernel options for the same distro?)
The microphone is another problem and I hope somebody here could help me.

You are not the only one, I was having the same problem with the Dell integrated camera, for ubuntu 8.4 it was working fine, but after the upgrade, for some reason it stopped working.  Let's see how this is going to work out.

pookito

---

### Post by andmej on 2009-01-05
*bump*

Still having problems with the built-in microphone of a Dell Vostro 1310. I've tried most advices in this threads but nothing seems to work.

I'm on Ubuntu 8.10 with kernel 2.6.27-9. Any idea?

---

### Post by EvilMonki on 2009-01-17
> **andied said:**
> I struggled a long time to get my mic working. Double click or right click the volume icon and open the volume control window. The device should be "HDA Intel (Alsa mixer), then go to edit> preferences and select (probably all of the options) and after you get the mic working you could try deselecting some, but the important options for me are  "master", "pcm" "front", "digital" and "digital input source". Now on the "recording" tab, make sure the options are enable and the volume up. Then go to the "options" tab and be sure "digital mic" is selected. Hopefully that will enable your mic.

Solved the microphone issue. Thanks

---

### Post by egallo on 2009-01-24
I am using ubuntu 8.10, kernel 2.6.27-9-generic
on DELL vostro 1310

internal mic doesn't work (I have not an external one to test)
I cannot record any sound (only noise is recorded); I cannot use Skype 

I edit /etc/modprobe.d/alsa-base

adding line

options snd-hda-intel model=dell

my volume control window settings:
device  "HDA Intel (Alsa mixer)"
edit> preferences and I select master, speakers, internal mic boost 5 (no "front", "digital" and "digital input source" are shown)
 "recording" tab,  mic are disable by default: I enable them
the volume is up; I can hear noise from speaker setting hight mic boost  and volume up
 "options" tab "front mic" is selected (no "digital mic option" available).
I close volume control window settings

mic doesn't work

I open it again: mic are disable again !:(

any suggestion?

thanks in advance

---

### Post by jimmybarcelona on 2009-02-26
I'm running ubuntu 8.10 on a Dell Vostro. My wireless didn't work out of the box with 8.04, but worked fine after upgrading to 8.10. My webcam worked fine with both distributions, but never my integrated mic. It seems we've got quite the club going. 
When I run alsamiser from the command line, and hit F5 to get all of my controls showing, it doesn't show that I have an internal microphone. just a section for "Capture". It shows my card and chipset as pulseaudio. In windows it is a sigmatel audio driver. I'm kind of new at this, so what is pulse audio, anyways? And if it's a sigmatel audio driver, should I change it from pulse audio to sigmatel?

---

### Post by jimmybarcelona on 2009-02-26
Okay, not I'm really confused. I tried booting into a newer kernel. Everything seemed the same, but in the new kernel I enabled Capture  and Capture 1. While they were muted, skype would pick up my integrated microphone, but the sound recorder would not. Sound recorder only picked up a really loud and annoying buzzing sound. I'm glad that my mic works on skype now, but don't know why it works with the digital mic set to be muted. What's going on?

---

### Post by cunner on 2009-07-29
I've also had problems with the internal mic of my Vostro 1310. Some 10 month ago I tried to get it working and added the line

```
options snd-hda-intel model=dell
```

to my /etc/modprobe.d/alsa-base.conf as suggested earlier in the thread. Unfortunately this didn't make the mic work and after a while I gave up and left the above line in place.

Today I started another attempt to get it working. Meanwhile I had updated Ubuntu and the kernel, but I still couldn't get recording to work with any combination of settings in the gnome-sound-recorder and the mixer applet.

After I went through this thread once again I commented out the line in alsa-base.conf. This made the Digital Capture option disappear from the mixer applet, but therefore recording started to work with Capture enabled and set to 70 % and Input Source set to Mic. Capture 1 was disabled.

Skype telephony, here I come...  :guitar:

---

### Post by skiold on 2009-07-29
Try this option on alsa-base:

```
options snd-hda-intel model=laptop
```

and restart your system.

Hope this solve your trouble.

---

### Post by michelkogan on 2009-10-10
> **egallo said:**
> I am using ubuntu 8.10, kernel 2.6.27-9-generic
on DELL vostro 1310

internal mic doesn't work (I have not an external one to test)
I cannot record any sound (only noise is recorded); I cannot use Skype 

I edit /etc/modprobe.d/alsa-base

adding line

options snd-hda-intel model=dell

my volume control window settings:
device  "HDA Intel (Alsa mixer)"
edit> preferences and I select master, speakers, internal mic boost 5 (no "front", "digital" and "digital input source" are shown)
 "recording" tab,  mic are disable by default: I enable them
the volume is up; I can hear noise from speaker setting hight mic boost  and volume up
 "options" tab "front mic" is selected (no "digital mic option" available).
I close volume control window settings

mic doesn't work

I open it again: mic are disable again !:(

any suggestion?

thanks in advance

EXACTLY THE SAME PROBLEM ! ... mic problem didn't solve with adding those lines in alsa-base .... ONLY NOISE ... I'm in Ubuntu 9.04

---

### Post by seggiebee on 2011-09-11
Hello,

I seem to be having the same problem with my internal mic on the Vostro 1310; it is not working at all.  However, to make matters worse I don't even seem to have as many volume options as mentioned in other posts.  When I right click the volume control there is no 'Edit' or 'Preferences' option.  Just an 'Options' and then 'Properties' which shows thes options of 'Realtek HD Audio Output' or 'Realtek HD Audio'.

I would be very grateful if anyone could help at all.  I have tried everything I can think of.

Thank you,
S

---

