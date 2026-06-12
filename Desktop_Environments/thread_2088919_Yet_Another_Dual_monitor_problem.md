---
title: "Yet Another Dual monitor problem"
date: 2012-11-27
forum: Desktop Environments
---

### Post by Nebelhom on 2012-11-27
Hi folks,

I am trying to use a wide screen monitor as main and a normal one as secondary in ubuntu 12.04 in Classic Gnome (I dislike Unity greatly). Twinview would mess up the resolution on the second monitor, which is why I tried for the separate X version. This only gave a white screen on the second monitor, so I reverted back to TwinView.

Ever since that restart it seems like I have two screens in one monitor and the secondary is just the background (see screenshot). Reverting to default from nvidia-settings and restarting unfortunately doesn't give me back the original settings, so I am a little stumped as to what to do.

Has any got any ideas about this one?

I would like to get it to work so that both Monitors can be used. It doesn't matter if in TwinView or separate X.

Thanks for the help and hopefully I was able to articulate this problem reasonably well. If not, please don't be afraid to ask again.

-------------------------------
here's the screenshot:

---

### Post by Nebelhom on 2012-11-27
I found an unsatisfactory solution myself which consisted of deleting the file ~/.config/dconf/user

This takes away all other previous configurations of my GNOME classic setup and is thus a bit annoying. If anyone else knows of a better way, please tell me in case it happens again.

As for now, I shall leave this thread open, in case someone can enlighten me.

Thanks for any input.

---

### Post by Malsasa on 2012-11-27
I have same problem in 12.04 but in Unity. The piicture is similiarly same with that.

---

