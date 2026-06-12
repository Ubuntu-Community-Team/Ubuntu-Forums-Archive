---
title: "Ubuntu 17.10 - How to skip first login screen (with username only)"
date: 2018-03-17
forum: Desktop Environments
---

### Post by PBear.SF on 2018-03-17
Since switching from Unity back to Gnome with the recent Ubuntu update, I am being driven crazy by the totally unnecessary preliminary login screen that forces me to choose my user name before I can progress to the actual login screen (where I can type my password).  This was much better handled in Unity.

I simply want to see my user name _and_ password field as the first screen when I boot into Ubuntu (like I always used to).  Since I am the only user that exists in this Ubuntu 17.10 installation, why on earth do I have to choose my user name _before_ I can even see my password entry field?

Any way around this?

---

### Post by nlee2 on 2018-03-18
My setup is the same. To login I hit spacebar and enter my password. Does that not work for you?

At any rate you can just install lightdm and choose it as default login during installation.

---

### Post by PBear.SF on 2018-03-18
> **nlee2 said:**
> My setup is the same. To login I hit spacebar and enter my password. Does that not work for you?

At any rate you can just install lightdm and choose it as default login during installation.
Yes, that's exactly how I log in now.  The extra step of hitting the spacebar just seems unnecessary and annoying to me, as does seeing that big wasted-space opening screen with just a box containing my name on it.  Previously (as well as in macOS), the very first screen showed the user name and password field together, so all you had to do was start typing your password.

I don't know anything about lightdm.  I don't want to change my entire desktop environment (in all other respects, I like the Gnome desktop very much), so what other changes would lightdm make?

---

### Post by nlee2 on 2018-03-18
Lightdm is the previous login screen that you are used to. Can switch default back to gdm3 default anytime after installing lightdm. I have both installed no problems. Frankly, I just go with the flow and use gdm3.

---

### Post by PBear.SF on 2018-03-18
Thanks, nlee2, I'll try it out.

Follow up:  Installed lightdm; it works fine.  Now I have the login screen I like again.  Thanks much.

---

