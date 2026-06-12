---
title: "Unable to get sound working on Dell Mini 9 in Maverick."
date: 2011-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bpraveen on 2011-01-17
Hi,
I am running Xubuntu 10.10 from a usb stick (with persistence enabled) on Dell Mini 9. I am unable to get hear any sound.

Here is the link to alsa information:
[http://www.alsa-project.org/db/?f=c4f665f531fe99c1d5822a58345534fabd34a06f](http://www.alsa-project.org/db/?f=c4f665f531fe99c1d5822a58345534fabd34a06f)

I have another usb stick which has Xubuntu 10.04 (with persistence enabled) and with 10.04 I have no sound problems at all. Sound works perfectly.

I am attaching a screenshot of Totem which popped up a couple of errors when I tried to play a video. The video works fine, but there is no sound.

Another observation is that 'PCM Control' in the mixer is behaving very strangely. When I mute and un-mute PCM, quit the mixer & re-open the mixer, PCM shows its level way too low (close to zero). But even after moving the sliders (of both PCM and Master) all the way up, I am unable to hear sound on Maverick.

Can someone please let me know how can I diagnose this problem, which is particular to Maverick, further?

Thanks,
Praveen

---

### Post by bpraveen on 2011-01-17
Doh! The sliders for Headphones and Speakers were muted. When I unmuted them, sound worked like a charm. gnome-alsamixer showed all the controls and that is where I found that these two controls were muted.

Sorry for the noise.

---

### Post by davepoth on 2011-01-17
Out of interest, did you still have the same issues with Totem? I've been involved with a bug that causes that problem for some months, it would be a little mad if just turning the volume up fixed it!

---

### Post by bpraveen on 2011-01-20
No. I do not have those issues with Totem anymore.

Now, the problem with Totem is that at first video is playing (very slow fps) and audio is not. When I move the slider and re-start the video, then everything is fine (video is playing as it should and I am also getting sound).

Vlc does not have any problems at all. It is working fine.

I do remember a state where vlc worked fine as always, but Totem gave the problems (errors popped) that I mentioned. This is not happening now.

Hope that helps. If I see the problem again (errors popping up out of Totem), I will update this thread. I have attached my Totem Version.

Please let me know if you need any additional information.

---

