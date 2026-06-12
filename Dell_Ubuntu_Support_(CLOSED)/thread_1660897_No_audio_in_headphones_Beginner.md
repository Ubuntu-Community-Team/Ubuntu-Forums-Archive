---
title: "No audio in headphones? Beginner"
date: 2011-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Corky1217 on 2011-01-06
Hello, I am completely new to Ubuntu and Linux in general.  I installed Ubuntu 10.10 on my Dell Studio 17 tonight and I cannot get the sound to work through headphones.   It works otherwise.  I've done some google searching, but since I am so new, I am having a hard time figuring out a solution.

Would anyone mind helping a noob?

---

### Post by lidex on 2011-01-06
First check your mixer settings.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Also, in your sound preferences, toggle the connector option on the output tab.

---

### Post by Corky1217 on 2011-01-07
Thanks for your reply.

I have tried everything you've mentioned, however, everything seems to be in order, but it still doesn't work... Any other suggestions?

I've read in places about the audio jacks becoming "confused," meaning that the ports are configured correctly, but I have no idea if this is the problem or how I'd go about fixing it...

Any further help would be greatly appreciated.

---

### Post by lidex on 2011-01-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Corky1217 on 2011-01-07
[http://www.alsa-project.org/db/?f=6fbc722ce687519c09ecd46e0147d32210905984](http://www.alsa-project.org/db/?f=6fbc722ce687519c09ecd46e0147d32210905984)

---

### Post by lidex on 2011-01-07
Interesting. Time to edit alsa-base.conf
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m6-dmic 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Here are more options in case that doesn't work. Take the left column value and place after the = , overwriting the previous one.
```

  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x
  auto		BIOS setup (default)
```

---

### Post by Corky1217 on 2011-01-07
When I open alsa-base.conf, the file is blank.  Should I go ahead and add the line or is there another problem at play?
[B]
Edit 1: Nevermind.  Typo in my terminal command.

Edit 2: Worked perfectly!  Thanks a ton!


[/B]

---

### Post by Trandre on 2011-01-15
Thank you Calais225 for directing me to this thread. I have an HP pavilion, but hope I can ask Q on this post, even if its nor Dell :-)

I have the problem with my sound on laptop speakers not muting when inserting headphones. 

i started with the suggestion here, but dont know which soundcard to choose from the list in the print screen.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181165&stc=1&d=1295100925[/IMG]

---

### Post by lidex on 2011-01-16
> **Trandre said:**
> Thank you Calais225 for directing me to this thread. I have an HP pavilion, but hope I can ask Q on this post, even if its nor Dell :-)
I have the problem with my sound on laptop speakers not muting when inserting headphones. 
i started with the suggestion here, but dont know which soundcard to choose from the list in the print screen.


For HP Dvx models, generic fix is the following. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by dsmann12 on 2011-03-06
Hello. I have the the same problem as Trandre, but I'm using an Asus K701J. Think you can help me, Lidex?

---

### Post by lidex on 2011-03-06
> **dsmann12 said:**
> Hello. I have the the same problem as Trandre, but I'm using an Asus K701J. Think you can help me, Lidex?

It probably comes down to the same process as above - with different options dependent on your hardware. Use the alsa-info script please (see earlier post)

---

### Post by dsmann12 on 2011-03-07
[http://www.alsa-project.org/db/?f=1d1b85432a7bf4ea040205b12420f19d370fb5fd](http://www.alsa-project.org/db/?f=1d1b85432a7bf4ea040205b12420f19d370fb5fd)

Thanks for any help!

---

### Post by lidex on 2011-03-07
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by dsmann12 on 2011-03-07
No luck. That muted both the speakers and the headphones when I plugged them in. And I could override the mute, but sound would still play through both.

---

### Post by lidex on 2011-03-08
> **dsmann12 said:**
> No luck. That muted both the speakers and the headphones when I plugged them in. And I could override the mute, but sound would still play through both.

Try toggling the independent headphone value.

```
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
```

---

### Post by dsmann12 on 2011-03-22
Could you explain what to do here in more detail? I can't copy and paste the code in the terminal. It says "simple" isn't an understood command so I'm guessing there were steps to take before that. I'm pretty much a total noob at all this. I'm trying to teach myself the Linux basics and CLI commands and everything to better understand the OS, but I've only just begun. Google wasn't much help either

---

### Post by lidex on 2011-03-22
> **dsmann12 said:**
> Could you explain what to do here in more detail? I can't copy and paste the code in the terminal. It says "simple" isn't an understood command so I'm guessing there were steps to take before that. I'm pretty much a total noob at all this. I'm trying to teach myself the Linux basics and CLI commands and everything to better understand the OS, but I've only just begun. Google wasn't much help either

That's not a command, just the status of those controls. You'll need a mixer to change the values.

Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install (in a terminal):
```
sudo apt-get install gnome-alsamixer
```

---

### Post by dsmann12 on 2011-03-22
I opened the gnome-alsamixer in the terminal. Checking Independent HP did not help the problem. And when I'd open the gnome-alsamixer, these messages appeared in the terminal:


** (gnome-alsamixer:16553): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Independent HP"!

** (gnome-alsamixer:16553): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

I don't know if that helps or not

---

### Post by dsmann12 on 2011-03-23
I meant with the terminal, not in the terminal.

---

### Post by lidex on 2011-03-24
> **dsmann12 said:**
> I meant with the terminal, not in the terminal.

Instead try altering in this file:
```
gksu gedit /var/lib/alsa/asound.state
```
Save, close, reboot.

---

### Post by dsmann12 on 2011-03-24
> **lidex said:**
> Instead try altering in this file:
```
gksu gedit /var/lib/alsa/asound.state
```
Save, close, reboot.
The code looks like this: 

control.11 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 OFF
		comment.item.1 ON
		iface MIXER
		name 'Independent HP'
		value OFF

Is that right?

---

### Post by lidex on 2011-03-24
Yes.

---

### Post by dsmann12 on 2011-03-24
Still didn't work.

---

### Post by dsmann12 on 2011-04-01
Any other suggestions?

---

### Post by lidex on 2011-04-01
> **dsmann12 said:**
> Any other suggestions?

Upgrade alsa (link in my sig)or update driver modules(below).

Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by dsmann12 on 2011-04-16
I already have version 1.0.24. And updating the modules didn't work either.

---

### Post by sarahwiz210 on 2011-04-17
I'm having the same problem, with a lenovo thinkpad.. The sound just comes out of the built-in speakers and not the headphones. I can't get the laptop to recognise the headphones and send the audio to the headphones, not the speakers? Any ideas?

---

### Post by lidex on 2011-04-17
> **dsmann12 said:**
> I already have version 1.0.24. And updating the modules didn't work either.
According to your alsa-info output you're at v. 1.0.23
At this point you should file a bug. 
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Evrt on 2011-05-09
Same problem (beginner, Ubuntu 11.04)
No sound once headphones are plugged in jack...
Sound does work when no headphones attached, headphones work in Win xp.
Thanks in advance for your help.

Evrt

                                  [http://www.alsa-project.org/db/?f=5e6a29146c5101aea073e5d5c2257af9cd43fa32](http://www.alsa-project.org/db/?f=5e6a29146c5101aea073e5d5c2257af9cd43fa32)

---

### Post by lidex on 2011-05-10
> **Evrt said:**
> Same problem (beginner, Ubuntu 11.04)
No sound once headphones are plugged in jack...
Sound does work when no headphones attached, headphones work in Win xp.
Thanks in advance for your help.

Evrt

                                  [http://www.alsa-project.org/db/?f=5e6a29146c5101aea073e5d5c2257af9cd43fa32](http://www.alsa-project.org/db/?f=5e6a29146c5101aea073e5d5c2257af9cd43fa32)

This should be a simple fix. Go into alsa-base.conf and edit the line beginning with 'options snd-hda-intel...'
To edit:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Change to:
```
options snd-hda-intel model=hp
```
**Reboot**

---

### Post by Evrt on 2011-05-10
> **lidex said:**
> This should be a simple fix. Go into alsa-base.conf and edit the line beginning with 'options snd-hda-intel...'
To edit:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Change to:
```
options snd-hda-intel model=hp
```**Reboot**

Thank you Lidex.
Works fantastic! :)

---

### Post by lidex on 2011-05-10
You're welcome!

---

