---
title: "audio enhancer or equalizer kubuntu 11.10? (+anything else I could do for my sound?)"
date: 2011-12-05
forum: Desktop Environments
---

### Post by MarcosCosmos on 2011-12-05
Edit: .... I've put it in the wrong section haven't I?..

So. I have a laptop, it's fairly good.. well capable of 64bit, but I had windows 7 32 bit until recently, and without an audio enhancer program that came with my laptop for windows 7 32-bit, the inbuilt speakers are rather trashy.

So I decided to install ubuntu, and then messed up the location of grub, and reinstalled the whole thing. Now I can't run windows, because every time I click the windows 7 boot option, it just reopens grub. But that's another issue.

Now, I'm stuck in Ubuntu, and am running KDE which I love, apart from being pretty much unable to watch any sort of movie or multimedia, because the sound is too trashy to understand human dialogue...

So I tried looking into PulseAudio, sounded ok, but isn't ready for 11.10? And I don't know how to downgrade Ubuntu.

I've been looking around the forums for a week now but couldn't get anything I heard of working..

Could anyone please help me?

Side note: The internal mic won't function at all, and I don't know how to fix it, if anyone can help me there aswell..

Thanks!
Marcos Cosmos

---

### Post by kio_http on 2011-12-06
> **MarcosCosmos said:**
> Edit: .... I've put it in the wrong section haven't I?..

So. I have a laptop, it's fairly good.. well capable of 64bit, but I had windows 7 32 bit until recently, and without an audio enhancer program that came with my laptop for windows 7 32-bit, the inbuilt speakers are rather trashy.

So I decided to install ubuntu, and then messed up the location of grub, and reinstalled the whole thing. Now I can't run windows, because every time I click the windows 7 boot option, it just reopens grub. But that's another issue.

Now, I'm stuck in Ubuntu, and am running KDE which I love, apart from being pretty much unable to watch any sort of movie or multimedia, because the sound is too trashy to understand human dialogue...

So I tried looking into PulseAudio, sounded ok, but isn't ready for 11.10? And I don't know how to downgrade Ubuntu.

I've been looking around the forums for a week now but couldn't get anything I heard of working..

Could anyone please help me?

Side note: The internal mic won't function at all, and I don't know how to fix it, if anyone can help me there aswell..

Thanks!
Marcos Cosmos

Ok, some music playing applications like Clementine come with a nice equaliser that you can play with. Pulseaudio is included by default in 11.10. Pulseaudio has nothing to do with sound effects. About the microphone. Try installing pavucontrol then press ALT + F2 type "pavucontrol" and launch it. Under input devices remove the lock channels setting and set the left mic to s lower value then the right. If that fails, check if it is muted in alsamixer.

---

### Post by MarcosCosmos on 2011-12-06
> **kio_http said:**
> Ok, some music playing applications like Clementine come with a nice equaliser that you can play with. Pulseaudio is included by default in 11.10. Pulseaudio has nothing to do with sound effects. About the microphone. Try installing pavucontrol then press ALT + F2 type "pavucontrol" and launch it. Under input devices remove the lock channels setting and set the left mic to s lower value then the right. If that fails, check if it is muted in alsamixer.

Thanks, haven't tried pavucontrol, but I'm about to

And if I we're just dealing with local files, I would resort to a media player application. but most of my problems are with flashplayer multimedia streaming, such as youtube, or tinychat.

By pulseaudio, I meant an equalizer for pulseaudio x.x

The internal sound output has improved though and I don't know how, I think the sound profiles were bugging out in any case, because I hooked up a turtle beach headset and then it has allowed me to select the duplex profile for the internal hardware again instead of dropping to dummy output, though the mic on the headset is being weird.. I was on tinychat and it was picking sound up fine in the options, easily reaching the top of the volume indication meter thing, but past the settings menus, only sending minimum volume to the server.. I had to yell with the mic touching my lips for it to display any sound, which is NOT normal for my turtle beaches...

What do you think caused that?

edit: I had PA volume control, changed the left right stuff as you said and its working..... but it's picking up everything... If I'm gunna use it for webchats, I'm gunna need to cancel out any sound coming from the system/speakers, so will enabling "mute audio" on the input device do that?

edit2: nope... so how do I cancel it? ._.

---

### Post by oldos2er on 2011-12-07
There is a pulseaudio-equalizer package here: [https://launchpad.net/~psyke83/+archive/ppa/+packages](https://launchpad.net/~psyke83/+archive/ppa/+packages) 
I haven't tried it on 11.10 though.

---

### Post by MarcosCosmos on 2011-12-08
> **oldos2er said:**
> There is a pulseaudio-equalizer package here: [https://launchpad.net/~psyke83/+archive/ppa/+packages](https://launchpad.net/~psyke83/+archive/ppa/+packages) 
I haven't tried it on 11.10 though.

Thanks, I have, I thought I mentioned that x.x

---

### Post by oldos2er on 2011-12-09
Please forgive my reading comprehension problem! Sorry.

---

### Post by MarcosCosmos on 2011-12-10
> **oldos2er said:**
> Please forgive my reading comprehension problem! Sorry.

Not a problem... Is there a way I can run steam games on an extended desktop whilst still using other windows? (Hell I'm having major troubles using kde on an extended desktop at all..)

---

### Post by oldos2er on 2011-12-11
> **MarcosCosmos said:**
> Not a problem... Is there a way I can run steam games on an extended desktop whilst still using other windows? (Hell I'm having major troubles using kde on an extended desktop at all..)

I would ask that question on the Gaming & Leisure forum. I know nothing about Steam.

---

