---
title: "Wiley sound volume icon doesn't show &gt; 100%"
date: 2015-11-11
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2015-11-11
In sound settings I have chosen allow volume > 100% But under the sound icon the volume bar is already at the far right with no room to move further (screenshot) I can only increase the volume beyond 100% by either from Sound Settings (second screenshot) or using the hardware key. 

Ubuntu 15.10.

---

### Post by monkeybrain20122 on 2015-11-12
Can anyone confirm this?

---

### Post by Dennis N on 2015-11-12
I think what the indicator volume (sound menu) does show is the fraction of the: **Sound Settings > Playback device** level that you effectively hear.
 
```
Sound Settings Playback Level 	Indicator Menu Level 	Effective (Final) Level
100%  			        100% 		        100%
120%				100%			120%
100%				50%			50%
120%				50%			60%
60%				100%			60%
60%				50%			30%

```
So 120/50 would sound the same as 60/100.

Been that way for quite a while I think.

---

### Post by monkeybrain20122 on 2015-11-12
> **Dennis N said:**
> I think what the indicator volume (sound menu) does show is the fraction of the: **Sound Settings > Playback device** level that you effectively hear.
 
```
Sound Settings Playback Level     Indicator Menu Level     Effective Level
100                100            100
120                100            120
100                50            50
120                50            60
60                100            60
60                50            30

```
So 120/50 would sound the same as 60/100.

Been that way for quite a while I think.

No, it is not this way in 15.04. Maybe I don't explain very well, when the box allow volume > 100% is checked and volume is set to 100% in Sound Settings, the bar under the volume icon should be somewhere in the middle (at 100%) so it leaves room to increase beyond 100%. But in 15.10, when volume is at 100% (and box allow volume > 100% is checked), there is no room left to the right under the volume icon to allow increasing volume beyond 100%.

Attached screenshot shows 15.04 with volume at 100%, compare this to the 15.10 one above to see the difference.

---

### Post by Dennis N on 2015-11-12
I was not looking at Ubuntu, but Xubuntu 15.10 - could be differences*, but I think were are saying the same thing about 15.10. My assumption is that indicator sound menu level needs to be at 100% to pass through unchanged the sound level set in sound settings. Any lower setting reduces it as in the table. 

Example:
Set playback sound level at 110% in sound settings; to keep this output level set indicator sound menu at 100%.  Any setting <100% in indicator sound menu reduces final volume. If I want more final volume instead, I have to adjust the level in sound settings.

* for one thing, I have no box to check saying "allow volume > 100%".

---

### Post by Dennis N on 2015-11-13
Checked the release manifests, and Ubuntu 15.10 doesn't install pulse audio volume control (pavucontrol) by default, while Xubuntu 15.10 does. Both have the same pulseaudio package installed. This might account for any differences in behavior between them. 

 
[INDENT]Rephrasing Xubuntu behavior as I see it:
The Sound Settings playback value sets the range of values of the Indicator Sound Volume. Sound Settings = 150% means the Indicator Sound Volume's range goes from 0 to 150% of normal volume. Sound Settings = 100% means Indicator Sound Volume ranges from 0 to 100% of normal volume - the initial default situation.[/INDENT]

So your request for a confirmation of your Ubuntu system's behavior remains unanswered.

---

### Post by monkeybrain20122 on 2015-11-13
> **Dennis N said:**
> Checked the release manifests, and Ubuntu 15.10 doesn't install pulse audio volume control (pavucontrol) by default, while Xubuntu 15.10 does. Both have the same pulseaudio package installed. This might account for any differences in behavior between them. 


I have installed pauvcontrol. I can increase volume beyond 100% with no problem by opening Sound Settings, just that I can't do this with the volume icon/applet for the reason  that there is no room to move the bar pass 100%. This is different from Ubuntu 15.04 and earlier releases. I think it is a bug in Unity or gnome. Maybe I should have posted this on the desktop environment subforum.

---

### Post by Dennis N on 2015-11-13
I would be happy to confirm this for you, but have no Ubuntu 15.10 installation to test. So, I will have to pass. There are lots of users on this forum who should be able to.

---

### Post by Dennis N on 2015-11-14
I did get hold of a Ubuntu 15.10 installer and ran live session to see for myself how things worked with these sound menus in Ubuntu 15.10 vs. Xubuntu 15.10. 

_Comments_:

Adjusting slider on indicator sound level also moves slider on Sound Settings, and vice versa. They are locked together. In Xubuntu the two sliders move independently - for example, I can keep the indicator sound at far right and it stays there while I adjust the sound settings. So this  alone suggests you system works differently. 

In Ubuntu, When I checked "allow louder than 100%" the sliders could both moved all the way to the right, but I don't know what level that represents.

Even though I checked "show sound volume on menu bar" no volume number is showing there like in your screenshot; in fact there is no numerical indication of the sound level (in %) anywhere. Maybe some indicator or plug in needs to be added to the panel before it shows. 

I was going to try Pulse Audio Volume Control. Pulse Audio is installed, but  when I looked to install pavucontrol, there is no candidate to install. Maybe the correct repository (universe?) is not enabled in live system. I didn't check further.

```
ubuntu@ubuntu:~$ apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:6.0-0ubuntu13 
  Candidate: 1:6.0-0ubuntu13
  Version table:
 *** 1:6.0-0ubuntu13 0
        500 http://archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
        100 /var/lib/dpkg/status

ubuntu@ubuntu:~$ apt-cache policy pavucontrol
pavucontrol:
  Installed: (none)
  Candidate: (none)
  Version table:


```I don't know if anything in this test is useful, but the comments I gave about how sound level adjustment works in Xubuntu don't seem to apply to Ubuntu 15.10.

---

### Post by monkeybrain20122 on 2015-11-15
Hi, Thanks for looking into it. Checked with the live usb again, the problem is the same.

Before 15.10, if I open Sound Settings, check the box allow louder than 100 % then move the slider in sound settings to 100%, the slider under the volume icon would move to the middle, leaving room to amplify beyond 100% (like in post #3) Whereas for 15.10 (live usb and installed) the slider under the volume icon is all the way to the right, leaving no room to amplify beyond 100% like the first screenshot in OP (sound can still be amplified if open Sound Settings and move the slider beyond 100%, but the slider under the volume icon doesn't move since there is no room)
 
There has never been number showing the % in the volume icon, that isn't a problem.

---

### Post by bapoumba on 2015-11-15
*Thread moved to **Desktop Environments**.*

---

### Post by monkeybrain20122 on 2015-11-17
Bump!

---

### Post by mc4man on 2015-11-21
The indicator stopped showing above 100% in this build - 
[https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150812.3-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150812.3-0ubuntu1)
build fixed this bug & involved many lines
[https://bugs.launchpad.net/canonical-devices-system-image/+bug/1481913](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1481913)

Last version to show extra (above 100) - 
[https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150807.6-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150807.6-0ubuntu1)

---

### Post by jurgen32 on 2015-12-07
I work with **K**ubuntu 15.10 and have exactly the same problem.
In Kubuntu 15.04 I had very good sound levels but I have upgraded the system to 15.10 last Friday and encountered this problem. 
Pavucontrol shows (and allows) that the volume can go to 150%, but audio control does exceed 100% (witch results in very low sound levels).

Jurgen

---

### Post by monkeybrain20122 on 2015-12-27
> **mc4man said:**
> The indicator stopped showing above 100% in this build - 
[https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150812.3-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150812.3-0ubuntu1)
build fixed this bug & involved many lines
[https://bugs.launchpad.net/canonical-devices-system-image/+bug/1481913](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1481913)

Last version to show extra (above 100) - 
[https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150807.6-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150807.6-0ubuntu1)

Still can't go beyond 100%.indicator-sound/12.10.2+15.10.20150915-0ubuntu1 Not sure what the bug was and what was the "fix" that was released,--maybe this behaviour of not being able to go beyond 100% is the "fix"?

---

### Post by mc4man on 2015-12-28
> **monkeybrain20122 said:**
> Still can't go beyond 100%.indicator-sound/12.10.2+15.10.20150915-0ubuntu1 Not sure what the bug was and what was the "fix" that was released,--maybe this behavior of not being able to go beyond 100% is the "fix"?

The bug was that the EU requires mobile devices to present a warning when one tries to increase sound level above a certain level or certain levels over a certain period of time. Plus there was some stuff about tracking exposure/quota,  blah, blah - see here
[https://wiki.ubuntu.com/Sound?action=diff&rev2=146&rev1=145](https://wiki.ubuntu.com/Sound?action=diff&rev2=146&rev1=145)

How that works out for Desktop installs no clue, (never see a warning, it may only be for headphones & or mobile devices), only it appears it (the changes) resulted  in the indicator only going to 100
The actual pulseaudio sound control should allow higher if desired.

Desktop settings regarding are in dconf > com.canonical.indicator.sound though some allude to com.ubuntu.sound's 'allow-amplified-volume' setting which I've no idea where that is (maybe again only the mobile version of Ubuntu whatever that is...

---

### Post by monkeybrain20122 on 2015-12-28
> **mc4man said:**
> The bug was that the EU requires mobile devices to present a warning when one tries to increase sound level above a certain level or certain levels over a certain period of time. Plus there was some stuff about tracking exposure/quota,  blah, blah - see here
[https://wiki.ubuntu.com/Sound?action=diff&rev2=146&rev1=145](https://wiki.ubuntu.com/Sound?action=diff&rev2=146&rev1=145)

How that works out for Desktop installs no clue, (never see a warning, it may only be for headphones & or mobile devices), only it appears it (the changes) resulted  in the indicator only going to 100
The actual pulseaudio sound control should allow higher if desired.

Desktop settings regarding are in dconf > com.canonical.indicator.sound though some allude to com.ubuntu.sound's 'allow-amplified-volume' setting which I've no idea where that is (maybe again only the mobile version of Ubuntu whatever that is...

So basically the volume indicator won't be allowed to go above 100, and to change it has to go to sound settings?

---

### Post by mc4man on 2015-12-29
> **monkeybrain20122 said:**
> So basically the volume indicator won't be allowed to go above 100, and to change it has to go to sound settings?

Correct 
The only other way would be to downgrade to the package before the changes 
I believe that this build still allows over 100 in the indicator
[https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150807.6-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-sound/12.10.2+15.10.20150807.6-0ubuntu1)

There never seemed to be any direct mention of limiting the indicator,  warnings aside, the indicator volume doesn't account for app volume nor any external volume control like some headphones have, Bluetooth speakers, etc.
To me just more government meddling & waste management

---

