---
title: "No microphone input signal while sound still works"
date: 2020-09-14
forum: Desktop Environments
---

### Post by staskhudzik on 2020-09-14
Hello everyone,

I run xubuntu 20.04 on the Samsung Chromebook with Chrome OS deleted. Initially I was able to fix sound driver issue using the solution here: [https://askubuntu.com/questions/974073/no-audio-on-acer-chromebook-14-under-ubuntu-17-10](https://askubuntu.com/questions/974073/no-audio-on-acer-chromebook-14-under-ubuntu-17-10) (replacing asound.state) but it turned out that I still have no input signal and microphone's not working, although the system displays a mic volume. So there is output signal with no input. Does anyone has any idea how that can be fixed?

---

### Post by gdesilva on 2020-09-15
Can you post the output of alsamixer command?

---

### Post by staskhudzik on 2020-09-15
> **gdesilva said:**
> Can you post the output of alsamixer command?

Sorry, did not really understand what do you mean by alsamixer command's  output. When using 'alsamixer' command it simply shows mixer. When used  with 'pastebinit', terminal says that it can't read from 'alsamixer'.

---

### Post by gdesilva on 2020-09-16
I should have mentioned to post a screen shot. Anyway, check whether there is 'MM' on the Mic column - this means the mic is muted. If so tab across to the Mic (should display Mic in red while others in white) and press 'm' on your keyboard which should unmute the mic.

---

### Post by staskhudzik on 2020-09-16
> **gdesilva said:**
> I should have mentioned to post a screen shot. Anyway, check whether there is 'MM' on the Mic column - this means the mic is muted. If so tab across to the Mic (should display Mic in red while others in white) and press 'm' on your keyboard which should unmute the mic.

Oh, now I get what you're talking about. I thought of doing this but the problem is that there is an insane number of columns in alsamixer for my soundcard and I don't know which deals with mic. I tried unmuting everything I saw there some time ago but it did not help as far as I remember. I can try uploading the screenshot but there would be dozens of them since alsamixer displays only one column at a time with my soundcard.

---

### Post by gdesilva on 2020-09-17
Not sure what's going on with your sound card - in my case, alsamixer gives me all playback settings in one screen, all capture settings in another and then I can see both playback and capture on one screen by pressing F5 - like this [https://imgur.com/WgndIZu.png](https://imgur.com/WgndIZu.png)

What type of sound card are you using? The output of lsusb and lspci commands would be useful to start with.

---

### Post by staskhudzik on 2020-09-18
> **gdesilva said:**
> Not sure what's going on with your sound card - in my case, alsamixer gives me all playback settings in one screen, all capture settings in another and then I can see both playback and capture on one screen by pressing F5 - like this [https://imgur.com/WgndIZu.png](https://imgur.com/WgndIZu.png)

What type of sound card are you using? The output of lsusb and lspci commands would be useful to start with.

Yeah, I know how normal mixer in ubuntu should look like with alsamixer. The problem is that with this soundcard it's totally not the case. According to alsamixer my soundcard is chtrt5650

Command output is:


lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 04f2:b657 Chicony Electronics Co., Ltd 720p HD Camera
Bus 001 Device 009: ID 25a7:fa23 Compx 2.4G Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci 
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 35)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 35)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 35)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 35)
00:1b.0 Audio device: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller (rev 35)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 35)
00:1c.2 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #3 (rev 35)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 35)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

---

### Post by gdesilva on 2020-09-19
It appears that this card has been creating headaches to many people. For whatever its worth you may want to try one of these solutions

[https://github.com/rgvxsthi/Braswell-EDGAR-Linux-Fixes#fixes-for-ubuntu-based-distros-ubuntuxubuntukubuntumint-etc](https://github.com/rgvxsthi/Braswell-EDGAR-Linux-Fixes#fixes-for-ubuntu-based-distros-ubuntuxubuntukubuntumint-etc)

[https://mailman.alsa-project.org/pipermail/alsa-devel/2019-October/156099.html](https://mailman.alsa-project.org/pipermail/alsa-devel/2019-October/156099.html)

---

### Post by staskhudzik on 2020-09-20
> **gdesilva said:**
> It appears that this card has been creating headaches to many people. For whatever its worth you may want to try one of these solutions

[https://github.com/rgvxsthi/Braswell-EDGAR-Linux-Fixes#fixes-for-ubuntu-based-distros-ubuntuxubuntukubuntumint-etc](https://github.com/rgvxsthi/Braswell-EDGAR-Linux-Fixes#fixes-for-ubuntu-based-distros-ubuntuxubuntukubuntumint-etc)

[https://mailman.alsa-project.org/pipermail/alsa-devel/2019-October/156099.html](https://mailman.alsa-project.org/pipermail/alsa-devel/2019-October/156099.html)

well, it seems that proposed solutions do not deal with mic specifically. I could, however, test some of them because I fixed the sound using a different solution. Also, I did not understand what the second link deals with. Anyway, thanks for suggestions!

upd: I tried the first solution for the soundcard and it proved to be not effective, unfortunately. Still no mic signal. I think alsamixer might be the source of problem but I simply do not know what to unmute

---

### Post by gdesilva on 2020-09-21
Note that there is a bug report on no sound on Samsung chromebooks which may or may not be similar to your issue

[https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg398292.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg398292.html)

Sorry cannot be of any further help.

---

### Post by staskhudzik on 2020-09-22
> **gdesilva said:**
> Note that there is a bug report on no sound on Samsung chromebooks which may or may not be similar to your issue

[https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg398292.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg398292.html)

Sorry cannot be of any further help.


It may be, though from what I've seen it does not deal with mic in particular. Again, thanks for the suggestion. At at least now I'm fully convinced that that the soundcard on Sumsung chromebooks is ass)

Also, the issue might be connected with system seeing two soundcards. Few minutes ago I attempted to use 
[COLOR=#4CE64C][/COLOR][COLOR=#295FCC][/COLOR]alsamixer -c 0 sset 'Mic',0 100% cap unmute
[COLOR=#4CE64C][/COLOR][COLOR=#295FCC][/COLOR]alsamixer -c 0 sset 'Mic Boost (+20dB)',0 on

and the result was that alsamixer displayed the mixer for HDA Intel PCH with no parameters being modifiable instead of chtrt5650.
here's how it looked like: [https://imgur.com/Q0dVBEs.png](https://imgur.com/Q0dVBEs.png)

---

### Post by gdesilva on 2020-09-23
According to lspci there is only one sound device which is HDA Intel PCH. I may be wrong here but Braswell HDMI refers to this sound device built in on the Braswell mobo.

Is there a separate HDMI IN port on your system?

EDIT: check that you have defined the correct profile for the HDMI Audio - if it can handle two way (both output and input) then the profile should be something like Digital Stereo Duplex in pavucontrol->Configuration

---

### Post by gdesilva on 2020-09-23
Did a bit of digging into these Chromebooks and it appears that audio on these things running Linux is a known problem. As MrChromebox says, "Then you have to deal with potentially porting functionality/drivers  from ChromeOS to the upstream Linux kernel, because there's zero chance  everything works out of the box (especially audio)." in [https://www.reddit.com/r/chromeos/comments/fz362l/linux_on_samsung_galaxy_chromebook/](https://www.reddit.com/r/chromeos/comments/fz362l/linux_on_samsung_galaxy_chromebook/)

---

### Post by staskhudzik on 2020-09-27
> **gdesilva said:**
> According to lspci there is only one sound device which is HDA Intel PCH. I may be wrong here but Braswell HDMI refers to this sound device built in on the Braswell mobo.

Is there a separate HDMI IN port on your system?

EDIT: check that you have defined the correct profile for the HDMI Audio - if it can handle two way (both output and input) then the profile should be something like Digital Stereo Duplex in pavucontrol->Configuration


What do you mean by "on my system"? According to pavucontrol my profile was stereo output + multi-channel input. I tried switching it to multi-channel duplex but nothing really changed.

---

### Post by gdesilva on 2020-09-27
What I meant was whether you have two HDMI ports, HDMI IN and HDMI out - unlikely but thought of checking it anyway.

Perhaps, someone with experience with Chromebooks can suggest a solution or a workaround this issue.

---

### Post by staskhudzik on 2020-09-28
> **gdesilva said:**
> What I meant was whether you have two HDMI ports, HDMI IN and HDMI out - unlikely but thought of checking it anyway.

I have a one port.

Today I decided to mess with alsamixer a bit more and tried unmuting everything possible. After the operation the mic turned on but with an extremely loud hiss. I started tweaking knobs to figure which one was responsible for mic and somehow messed the whole sound. Now even output signal is off, in the pavucontrol there are only dummy input and output and the sound does not react to alsamixer at all.
The good thing that after upgrade alsamixer allows to display multiple parameters in terminal. Now, however, this is not a big help, I guess(

---

### Post by gdesilva on 2020-10-01
If I were you, I would try re-installing alsa sound but given there appears to be an underlying issue with sound on Chromebooks it may not fix your issue - still worth a try now that it is all broken anyway!

---

### Post by TheFu on 2020-10-01
I've had 2 chromebooks. Put ubuntu on both. Sound always worked on both, though did use a usb mic to get better input audio for recordings.  The audio jack on my toshiba chromebook was always a mystery. The usb mic solved all sorts of issues for me.  Samson GoMic.

Never had any special audio issues with my Haswell 2995U chromebook.
Never had any special audio issues with my  Broadwell 5015U chromebook.

The only issue I had with either was low RAM (expected on chromebooks) and 10-ish dead keys after about 2 yrs of daily use. The keyboards on these things just can't take my typing.

---

### Post by staskhudzik on 2020-10-03
> **gdesilva said:**
> If I were you, I would try re-installing alsa sound but given there appears to be an underlying issue with sound on Chromebooks it may not fix your issue - still worth a try now that it is all broken anyway!

You know, the funny thing is that de-installing and re-installing alsa-utils did not work, as alsa force-reload and replacing asound.state, BUT alsa force-unload did actually help restore alsamixer parameters and I was able to return the output sound. However, I still can't understand which parameter in alsamixer is responsible for mic sound and now I know that attempting at straight up unmuting everything risks messing the whole sound configuration.

---

### Post by gdesilva on 2020-10-04
Have you tried [https://alsa.opensrc.org/](https://alsa.opensrc.org/)  ?

EDIT : Check out this post [https://bbs.archlinux.org/viewtopic.php?id=252123](https://bbs.archlinux.org/viewtopic.php?id=252123)  - read the second and the last post by **uhmzilighase**. The problem is not identical to yours but it is claimed that only certain versions of alsa packages work on Braswell.

---

### Post by staskhudzik on 2020-10-04
> **gdesilva said:**
> Have you tried [https://alsa.opensrc.org/](https://alsa.opensrc.org/)  ?

EDIT : Check out this post [https://bbs.archlinux.org/viewtopic.php?id=252123](https://bbs.archlinux.org/viewtopic.php?id=252123)  - read the second and the last post by **uhmzilighase**. The problem is not identical to yours but it is claimed that only certain versions of alsa packages work on Braswell.

I took a look at  **uhmzilighase**'s posts and it seems that we have different kinds of problems. I could enable alsamixer to show the actual soundcard instead of HDMI and make it work, even made alsamixer show all parameters after updating it. The thing that bothers me currently is figuring which of the **** ton of parameters is responsible for mic. And after my previous experiment I'm sure that one of them unmutes mic, but I simply can not decide which one and the fact that unmuting random parameters can kill the whole soundcard settings is not particularly encouraging. If only there was a guide to chtrt5650 alsamixer parameters.

Here's how alsamixer looks currently:

[https://imgur.com/ZAV2OAR.png](https://imgur.com/ZAV2OAR.png)
[https://imgur.com/TmR2HLc.png](https://imgur.com/TmR2HLc.png)
[https://imgur.com/ng6OaoT.png](https://imgur.com/ng6OaoT.png) 


I took a look at the first link also but I honestly don't know what to make out of it.

---

### Post by gdesilva on 2020-10-04
Wow, never seen anything like that before!!!

What happens if you slide the scales to mid point mark on all items? Worth a try as most of your input channels are set to zero.

I still cannot work out how your external mic is connected to the Chromebook - aren't you supposed to use the **built in** mic for input and use the HDMI port just to route the output audio/video signals to external speakers/display?

---

### Post by staskhudzik on 2020-10-05
I don't have external mic, I want to make my internal mic work. The setting you saw at the pictures is the one I got after using alsa force-uload. Earlier I tried tweaking some of them and if I remember, even slightly enhancing one of the media1 or media0 leads to overdrive of the output channel and turns any sound into the wall of static noise. Also, from my experience modifying this stuff by turning several parameters on simultaneously(even to the slightest) can mess up the soundcard settings, I assume due to some internal conflicts between parameters. So, in a way it's like walking through the minefield)

---

