---
title: "Defining a compose key conflicts with media keys"
date: 2007-07-07
forum: Desktop Environments
---

### Post by ib80 on 2007-07-07
Hi,

Kubuntu 7.04 had the media keys on my Logitech "Media Keyboard" (an actual model name) working out the box. It is so sweet. When I hit the media key, Amarok launches. And I can control it with the other keys. However, because I have a US keyboard and I live in France, I do need a compose key. I went to System Settings -> Regional & Language -> Keyboard Layout -> Xkb Options and switched on "Right Alt is Compose" under "Compose Key Position".  The compose key worked like a charm. But I lost the use of the media keys.

I don't mind editing config files if I know where to look. But here, I have no clue of why the compose key overrides the media key configuration.

By the way, if I switch off the compose key and reboot, the media keys work again.

Thanks,
ib

---

### Post by bapoumba on 2007-07-07
I'm not too familiar with the media keys. Have you tried other keys for "compose"? (ie right windows or menu if you have one).

---

### Post by ib80 on 2007-07-07
Thx bapoumba for the reply.

Yea, I just tried a few other keys as the compose key, same results. I think that it's when I turn the xkb options on that I lose the use of the media keys no matter what i set in it. I also tried other options than the compose key.

ib

Edit : I guess it's when setxkbmap is run that the media keys lose their mappings.

---

### Post by ib80 on 2007-07-14
Ok. Since I'm not getting any help here, let me change my question.

Anyone knows where or how the media keys are mapped by default in Kubuntu ?

Thanks,
ib

---

### Post by ldrn on 2007-07-14
Sorry -- I'd love to help, but I don't know anything about the compose key. I think your media keys are being set up by your keyboard layout, and the new layout is hosing the mappings that make them trigger XF86AudioPlay and so on.  Can you use xmodmap to get them back?

---

### Post by der_joachim on 2007-07-15
Try [this howto]("http://ubuntuforums.org/showthread.php?t=27039&highlight=howto+multimedia+keys").

---

