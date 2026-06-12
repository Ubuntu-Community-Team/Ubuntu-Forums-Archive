---
title: "[SOLVED] Ibex shutdown sound problem"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Corfy on 2008-11-02
I have read several posts on the forum about people not having a shutdown sound.

I'm having the reverse problem. When I shutdown on my laptop, the shutdown sound comes out of the speakers at what I think is full volume (it is pretty loud, in any rate), this despite the fact that I have the sound on my mixer turned completely down. Since these are the internal speakers for the laptop, I can't turn them down any other way.

It isn't a huge problem, but I typically forget about it and get blown out the back of my chair with sound when I'm not expecting anything.

BTW, I'm running Kubuntu 8.10 on a Dell Latitude D620 laptop.

---

### Post by jedimasterk on 2008-11-03
I have had similar problems with Ubuntu as well. It all has to do with Pulse Audio. What I did was remove pulse audio and ubuntu desktop (don't worry ubuntu desktop is a meta package so all of ubuntu will not be removed.). I then would install e-sound and then reboot. Sounds would then all work fine. This is also a solution to getting back your sound in flash with Ibex. This should work for kubuntu as well. Just remove kubuntu-desktop, pulse audio, and install esound then reboot.

---

### Post by grotto on 2008-11-03
You can tweak the system sounds in System Settings -> System Notifications. I disable all the sounds - I find them useless. There is a volume slider under Player Settings in System Notifications, as well.

---

### Post by loomsen on 2008-11-03
> **grotto said:**
> You can tweak the system sounds in System Settings -> System Notifications. I disable all the sounds - I find them useless. There is a volume slider under Player Settings in System Notifications, as well.

Not enough. Pulse was the problem here too, cause it's loaded at boot-time. 
Recently it hasn't been a problem for me anymore, but before any application using sound freezed to grey, and as soon as I killed pulseaudio all came up instantly again.

Method mentioned above using the enlightenment sound demon instead is probably best thing to do.

---

### Post by Corfy on 2008-11-03
> **jedimasterk said:**
>  This is also a solution to getting back your sound in flash with Ibex.

But... I haven't had any problems with sound in Flash, or any other sounds, for that matter, and I have been trying to put it through its paces. OK, when I first upgraded, I didn't have any sounds at all, but I found that was because of the settings in mixer. After a couple of tweaks with sliders, it worked perfectly... except for the shutdown sound.

I'm away from my Linux laptop, so I can't try your fix right now, but I will later. I will try the system notification thing first before I reinstall the audio, but I'll let you know how it turns out.

Thanks for the help.

---

### Post by Corfy on 2008-11-03
> **grotto said:**
> You can tweak the system sounds in System Settings -> System Notifications. ... There is a volume slider under Player Settings in System Notifications, as well.

That was indeed my problem... the volume slider was at 100%. I don't know why it doesn't use the system volume level, but that is a discussion for another thread, I guess.

I turned my sounds down to about 15 or 20%. That way if something does require my attention, I will still hear it, but it won't blow my ears out.

---

### Post by chengzi86 on 2008-11-03
**[Plastic valve](http://www.corrosion-resistant-valves.com)** special for controlling the corrosive media which features low weight, nonpoisonous and no pollution. It has wide temperature adaption, high mechanical stress and can take place of many kinds of expensive rare metal. It is high economic benefit. plastic valve [www.corrosion-resistant-valves.com](www.corrosion-resistant-valves.com)

---

