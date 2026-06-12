---
title: "Much higher power usage under gdm"
date: 2014-07-27
forum: Desktop Environments
---

### Post by andrewhlin on 2014-07-27
I've been using the default ubuntu unity desktop environment for the past two months since installing 14.04. Recently, a few days ago I decided to try using the Gnome shell, and overall have had very few issues with it. 
One of my main issues with unity was that the lightdm default greeter screen still showed some horribly unscaled icons and with a hidpi screen it made it both and eyesore and pretty difficult to see. Additionally, having the unity greeter and then being plucked into gnome shell is quite visually distracting as well, so following some recommendations from online I tried switching to using GDM. The problem is that under GDM, I seem to have a > 10 W increase in system power compared to lightdm, regardless of whether any windows are open, which problems, etc. I run at the lowest screen brightness for both, so it's not that. Since this is a laptop, having much higher power draw is obviously pretty problematic, but nothing I've changed seems to affect the powerdraw. Looking through powertop, very little is different between the two desktop managers. The power draw for each device is mostly the same, but comes up with usually 10W higher draw. I'd appreciate any help figuring out what's going on, because trying to do searches on google has led to very few results. Does anyone know of any particular reasons why GDM would draw so much more power?

I'm running ubuntu 14.04 with gnome shell, went ahead and removed most of the unity-specific packages since I don't plan on using unity anymore.
The computer is a Dell XPS 15 9530, with a haswell i7, and nvidia discrete graphics card which I disable using nvidia-prime.

Thanks!

---

