---
title: "No system sounds but all other sounds are fine."
date: 2005-04-12
forum: Desktop Environments
---

### Post by cajunaggie on 2005-04-12
Let me preface this by saying that everything else works fine. I can get sounds from XMMS, Totem, Xine, and Flash vids in Firefox. But for some reason my dang system sounds don't want to work. I've searched the forums but nothing I've found has matched this particular case.Here's a breakdown of what I've done so far:

I tried opening volume mixer and recording level monitor and I got this:
> Cannot connect to sound daemon
Please run esd and command prompt

When I run esd at the command line I get this:
> ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM dmixer

I went to the sound preferences in the menu and "Enable Sound Server at Start-up" was on.

I went to multimedia system selector. My Default Sink is ESD and my Default Source is OSS. I clicked "test" for both and got
> Failed to construct pipeline for "...." 

I'm completely stumped. Does anyone else know what to do?

---

### Post by Xian on 2005-04-12
Can you first verify that you have 'esound' installed by looking in synaptic?

---

### Post by cajunaggie on 2005-04-13
I checked Synaptic and I have esound, esound-clients, and e-sound common.

---

