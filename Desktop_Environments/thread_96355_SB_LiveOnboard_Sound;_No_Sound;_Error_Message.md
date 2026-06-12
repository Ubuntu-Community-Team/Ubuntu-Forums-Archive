---
title: "SB Live/Onboard Sound; No Sound; Error Message"
date: 2005-11-28
forum: Desktop Environments
---

### Post by camus on 2005-11-28
Hi everyone, from google searching and others it seems that this might have been done to death, but I couldn't find anything that worked (and found a lot of things way way above my level of understanding).

I installed breezy badger on my system last night and managed to boot up and find my way around and everything fine, but no audio from my cds. 

Device manager showed my onboard and my SB live. Cds would 'play' in juicer, but not affect any sound, system sounds do not affect any noise either. I went to alsamixer and found that it was using the onboard, even though I specified SB live in the sound preferences, so I rebooted with the onboard disabled in the bios. Now, when I try to play cds I get error message "Error playing CD. Reason: Could not open resource for writing." and I have no idea what that means. I should mention that aside from accessing a unix server and using vi for basic c programming, this is my first forray into linux.

Any answers or redirection to more pertinent venues would be hugely appreciated.

Thanks in advance.

---

### Post by camus on 2005-11-29
just as a note, I've tried playing .ogg files also, as well as wave, absolutely nothing will create sound on my system.

I've ensured that nothing was muted in alsa (the analog/digital output jack was muted by default, changed that)

again, the default drivers detect my card, so, what gives?

---

### Post by camus on 2005-11-29
re-installed ubuntu w/ onboard disabled prior to installation this time, again, no difference, SB live is detected, no audio can be affected, even wav.

anyone know a good link to walk a person through troubleshooting sound card stuff in 5.10? Most everything I've found is for older versions and/or addresses codecs and stuff. (right now I've no concern about codecs, considering I can't even play the default .wave system sounds)

I'm guess I'm shooting in the dark here

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=camus]re-installed ubuntu w/ onboard disabled prior to installation this time, again, no difference, SB live is detected, no audio can be affected, even wav.

anyone know a good link to walk a person through troubleshooting sound card stuff in 5.10? Most everything I've found is for older versions and/or addresses codecs and stuff. (right now I've no concern about codecs, considering I can't even play the default .wave system sounds)

I'm guess I'm shooting in the dark here[/QUOTE]
This one looked as good as any:
[https://wiki.ubuntu.com/HowToSetupSoundCards]("https://wiki.ubuntu.com/HowToSetupSoundCards")

---

### Post by camus on 2005-11-29
Hi

Thanks for the reply!

I tried the instructions on that link, which is to install the sound card I believe.

Thing is, the sound card was already installed and has been detected by device manager and displayed in alsamixer since I disabled the onboard sound, but I tried it all anyway.

I think this is a different problem, perhaps simpler, but I haven't solved it yet and it's the second day, maybe 5-6 hours total of dinking with it following several faq's.

---

### Post by YanH on 2005-11-29
I've also had very much the same experience with a SB live, detected in the Device Manager, but no sound. I didn't manage to solve the issue, or find an answer, so eventually reverted to the onboard sound.

---

### Post by camus on 2005-11-29
[QUOTE=YanH]I didn't manage to solve the issue, or find an answer, so eventually reverted to the onboard sound.[/QUOTE]

This is exactly what I did about 30 min ago. Hey, at least it works

Oh well, maybe I'll try it again with a different card.

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=camus]Hi

Thanks for the reply!

I tried the instructions on that link, which is to install the sound card I believe.

Thing is, the sound card was already installed and has been detected by device manager and displayed in alsamixer since I disabled the onboard sound, but I tried it all anyway.

I think this is a different problem, perhaps simpler, but I haven't solved it yet and it's the second day, maybe 5-6 hours total of dinking with it following several faq's.[/QUOTE]

Do you know what version of SB Live! it is?  I had an easy time with the 5.2 card, so when friends of mine got Ubuntu, I picked up a 7.2 card them.  It turns out they changed the chipsets between versions and I have yet to get that card working.

---

