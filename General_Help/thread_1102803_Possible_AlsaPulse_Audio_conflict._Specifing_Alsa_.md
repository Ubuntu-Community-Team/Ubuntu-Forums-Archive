---
title: "Possible Alsa/Pulse Audio conflict. Specifing Alsa per application generally works."
date: 2009-03-22
forum: General Help
---

### Post by adaemox on 2009-03-22
Hello, I'm running Xubuntu 8.10. I'm having some finicky audio issues. In programs that I can select alsa as the default audio driver I'm having pretty consistent results. In programs I cannot select the default driver I get absolutely no audio.

That's the big problem. But, I am also intermittently loosing audio when (this is what I'm guessing) a program not using alsa tries to use pulse or something else and alsa is no longer able to send audio to my receiver.

So, that's what I suspect is going on, I'm just not quite sure how to resolve this issue. I have read how to install pulse audio in Xubuntu 8.10, but not sure if that's the solution, or just a route to further problems. I'm also not opposed to uninstalling Pulse audio. At this point I'd simply like to force all apps to use alsa, but I also want to be able to use multiple audio sources at once so I'm not sure if that's going to be an issue with that route.

As reported by lspci my audio device is 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA). I'm connecting it via pcm to a receiver.

Anyway, hoping someone can get me headed down the right path with this. 

Cheers,
Adaemox

---

