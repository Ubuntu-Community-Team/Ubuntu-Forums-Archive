---
title: "Linux noob-no sound on Intel dual pentium pro"
date: 2006-02-26
forum: Desktop Environments
---

### Post by Selecter on 2006-02-26
standard ubuntu install. Looks like everything works, but no sound. Shows no default sound card installed. This is the old PR440FX Intel "Providence" board with dual PII Overdrives at 333 mhz. First time evar on Linux. 

Can anyone help me on this? I'm liking it so far. I tried Automagix and it complains a lot about my sound set up, giving me a error message over and over. Just wanna get the sound issue fixed and explore. Please dont tell me to compile this thing or that thing. That's not what I want from Linux, I dont want command line wonderment, just 
a free and easy op system. Thanks for any help.

---

### Post by az on 2006-02-26
[QUOTE=Selecter]standard ubuntu install. Looks like everything works, but no sound. Shows no default sound card installed. This is the old PR440FX Intel "Providence" board with dual PII Overdrives at 333 mhz. First time evar on Linux. 

Can anyone help me on this? I'm liking it so far. I tried Automagix and it complains a lot about my sound set up, giving me a error message over and over. Just wanna get the sound issue fixed and explore. Please dont tell me to compile this thing or that thing. That's not what I want from Linux, I dont want command line wonderment, just 
a free and easy op system. Thanks for any help.[/QUOTE]

Try this:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

It is a lot less complicated than it sounds.

---

### Post by Selecter on 2006-02-26
OK did that. Got it working, its a CS4236 chip. But it wont automagically load at boot.

---

### Post by az on 2006-02-26
[QUOTE=Selecter]OK did that. Got it working, its a CS4236 chip. But it wont automagically load at boot.[/QUOTE]
Yes.  That would be because isa hardware is not safe to probe.  You need to add the module name to /etc/modules for it to get loaded on boot.

---

### Post by Selecter on 2006-02-27
there is no /etc/modules.....went looking for it. No /modules dir there.

---

### Post by newuser111 on 2006-02-27
sudo nano /etc/modules

it is a file in the /etc/ directory

---

