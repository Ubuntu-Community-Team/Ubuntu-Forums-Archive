---
title: "Is It Possible To Play Audio CD's In Kubuntu?"
date: 2009-05-10
forum: General Help
---

### Post by jlacroix on 2009-05-10
My efforts today are telling me that this won't work. I am using Kubuntu Jaunty 64-bit, and I've tried Totem, KsCD, and Audacious and none of them will play a CD. When I try it in Totem, I get "Totem was no table to play this disc. No reason". (It literally said "no reason").

I've tried other CD's as well. Has anyone else had any luck?

---

### Post by paydaydaddy on 2009-05-10
Yes, it is possible. I use Amarok. I just upgraded to 9.04 which includes an upgrade to Amarok that is not as user friendly as the older version, but I did get it to work. Have you added the medibuntu repositories and added the restricted extras? In the older version of Amarok you needed to go to Amarok preferences and make sure that your cdrom drive was the default device. I haven't found that option in the newer version. Please post back if you need help with specifics.

---

### Post by jlacroix on 2009-05-10
> **paydaydaddy said:**
> Yes, it is possible. I use Amarok. I just upgraded to 9.04 which includes an upgrade to Amarok that is not as user friendly as the older version, but I did get it to work. Have you added the medibuntu repositories and added the restricted extras? In the older version of Amarok you needed to go to Amarok preferences and make sure that your cdrom drive was the default device. I haven't found that option in the newer version. Please post back if you need help with specifics.

I did the Medibuntu stuff. I usually avoid Amarok for audio cd playback because in the past playing an audio cd has always wiped out my playlists. Besides, I want a single purpose cd player like KsCD which should work. :(

---

### Post by 686plus on 2009-05-11
I am having similar problems with ubuntu jaunty 64-bit. I have tried totem, amarok, and audacious. None can play an audio cd.

Totem reports it can't find the location and suggests I don't have the right permissions. If I run totem using sudo, it reports I don't have the right codec/plugin (pretty sure I do). It then searches and cannot find a suitable one.

I'm not at that computer now, so I'll have to post again with the specific error messages.I have been searching a day and a half for solutions. This is the only post I've seen with the same problem.

---

### Post by 686plus on 2009-05-13
Totem now reports audio cd playback is not supported!? I can however play audio cds using rythmbox. WTF

Perhaps its time to downgrade.

---

### Post by jlacroix on 2009-05-13
This doesn't work on any of my computers, and I'm very shocked that something as simple and braindead as CD playback wouldn't be a big deal in a modern OS...

---

### Post by Bauldrick on 2009-05-27
I just came across this problem. The only player that could 'see' my cd was vlc.
However, looking at it, I notice kscd was looking for my cd at /dev/cdrom. I didn't have /dev/cdrom, only /dev/cdrom2 so ln -s /dev/cdrom2 /dev/cdrom fixed my problem, don't know if it helps you at all, maybe someone.

---

