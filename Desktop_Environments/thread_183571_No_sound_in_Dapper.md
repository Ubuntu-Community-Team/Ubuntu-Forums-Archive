---
title: "No sound in Dapper?"
date: 2006-05-28
forum: Desktop Environments
---

### Post by PereUbu on 2006-05-28
Hi

After upgrading to Dapper my soundcard is no longer detected.
I have a SB Live! soundcard, which worked fine in Breezy.

Any solution to the problem would be nice!

:-) PereUbu

---

### Post by Sutekh on 2006-05-28
Ah SB Live cards.  Mine was a pain in Breezy but fine in Dapper.

Do we have the same model?

How do you know its not detected?  Whats the ouput from these commands?
```
lspci | grep audio
```to find PCI audio```
lsmod | grep snd
```to find sound modules loaded

---

### Post by PereUbu on 2006-05-29
Hi Sutekh

I get these outputs so it seems that the card is detected.

```
lspci | grep audio
0000:00:0f.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a )
```

```

lsmod | grep snd
snd_pcm_oss            46368  0
snd_pcm                78344  1 snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_mixer_oss          16128  1 snd_pcm_oss
snd                    48644  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9184  1 snd
```

But what to do next?

/PereUbu

---

### Post by Sutekh on 2006-05-29
It doesn't look like you have any sound modules for your card (2nd command output)

For your card, the ALSA documentation indicates you should have the sound module - snd-emu10k1

[ALSA Installation - Creative SB Live! - emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1)

I got to go, do those instructions look ok to you.  Else try re-installing alsa-base and alsa-utils in Synaptic.

---

### Post by PereUbu on 2006-05-30
Hi again!

Finally I found the solution. After updating to Dapper, the GRUB-menu have not been updated for some reason. So I was actually booting in to the old Breezy kernel. 

By updating the GRUB-menu the sound is working again and other small annoyances have disappered!

I'm a happy guy again. :) 

Cheers! 
PereUbu

---

### Post by Sutekh on 2006-05-30
[quote=PereUbu]Hi again!

Finally I found the solution. After updating to Dapper, the GRUB-menu have not been updated for some reason. So I was actually booting in to the old Breezy kernel. 

By updating the GRUB-menu the sound is working again and other small annoyances have disappered!

I'm a happy guy again. :) 

Cheers! 
PereUbu[/quote]
Oh thats a unique problem, well done or finding the solution :)

Glad it its working now!!

---

