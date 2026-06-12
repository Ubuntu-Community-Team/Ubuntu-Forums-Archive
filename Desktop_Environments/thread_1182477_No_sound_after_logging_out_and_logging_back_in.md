---
title: "No sound after logging out and logging back in"
date: 2009-06-09
forum: Desktop Environments
---

### Post by Dave_Jackson on 2009-06-09
I am using 64 bit Jaunty on a Dell XPS 1530 laptop (output device is HDA Intel (ALSA mixer) ) and I have a really strange problem regarding the sound. 
After logging out of GNOME and then logging back in again, sound is completely gone. I've tried restarting ALSA and Pulseaudio from the command line, but that does not solve the problem. The only solution is a complete reboot of the system. 

The first time I log in, sound is fine. If I log out of the session and log back in again without rebooting the system, sound is completely lost. I've made no configuration changes that I know of, this just started happening for no apparent reason. I would really appreciate someone's help with this. This is by far the most annoying bug I have encountered using Jaunty.

---

### Post by BlazeFire247 on 2009-06-09
Try choosing one on System>>Preferences>>Sound, then click on the Sounds tab. Under Desktop, there should be something that says "Log In" and "Log Out" click the Default/Disabled and try changing it.

---

### Post by Dave_Jackson on 2009-06-09
No, I think you may have misunderstood my problem. It's not with the sound effects. It's with having no sound at all after logging in again after logging out. Sound only works the first time I log in and then after that is doesn't. Only a complete reboot will bring sound back. Thanks anyway.

---

### Post by Dave_Jackson on 2009-06-09
Well, I managed to find the solution at: [http://mydellmini.com/forum/ubuntu-netbook-remix/5167-firefox-steals-sound.html]("http://mydellmini.com/forum/ubuntu-netbook-remix/5167-firefox-steals-sound.html"). 

The way to fix the problem is: 
> the way I fixed it, was to just to run the command 'killall pulseaudio' at startup, to avoid having to deal with that all the time. To do that, just go to System > Preferences > Sessions, click on 'Add', name it 'Sound Fix' or whatever you want, and in the command field, type: killall pulseaudio 


So apparently it's a problem with PulseAudio. It seems maybe it's not terminating properly from the last session and so past instances of it must be killed on startup so it can be functional again. That's just my theory, if anyone else has any other ideas on it, feel free to chime in. 

It seems like a pretty basic problem that more testing would no doubt have uncovered before final release. For all it's supposedly advanced features, all too often PulseAudio balks at even doing the simplest things right like playing sound. At least ALSA never gave me any problems. 

PulseAudio has gotten much more reliable since it first came out, but it's still not that great. Better quality control should definitely be a priority for the developers. If it's not PulseAudio's developers who are at fault, Ubuntu should take more care with it's implementation in future releases. Such basic problems are not a way to gain new users.

---

