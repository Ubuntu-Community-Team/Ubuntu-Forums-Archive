---
title: "[SOLVED] How good is Beryl?"
date: 2006-10-27
forum: Desktop Environments
---

### Post by CatKiller on 2006-10-27
A friend has entrusted his computer to my care, since he doesn't have much room for it at his place at the moment. I use it to SSH into my computer if mine is occupied, and when he's round we use it for multiplayer Unreal Tournament. I upgraded it to Edgy for him last night, and it's working well.

He's expressed a liking of some of OSX's visual effects, although I've not seen them. I've not seen him for a little while, but I thought it might be nice if next time I did I could show him his computer doing some cool things. I do have some reservations, though.

Firstly, I understand that Beryl is beta. How beta is it though - is it buggy beta, or just unpolished beta? Also, is it necessary to install beta drivers to get it working well? The howtos I've looked at say that you should, but not - as far as I can tell - that you must. I feel a bit bad for installing the nvidia-glx drivers rather than the nvidia-glx-legacy ones I installed for him before - I'd rather not install beta drivers if I don't have to.

Secondly, I've read that Compiz/Beryl turns off the GLX/OpenGL that 3D applications use. Will it be **easy for him** to turn off Beryl, run Unreal Tournament for a while, then go back to how it was? I don't mind fiddling with stuff, and I have **some** idea of what I'm doing with Ubuntu having used it for a while. He's only had a computer for a couple of months, and he's been using XP on a laptop while he hasn't been here.

Thirdly, how cool is it, really? In particular, how cool would it be on an GeForce2 MX? It seems to run the OpenGL screensavers fine, and Unreal Tournament wonderfully, but will Beryl make everything else a bit unpleasant with a graphics card this weak? Is it fantastic enough to have a go regardless?

Thank you for sharing your Beryl experiences with me, and hopefully we can impress my friend with some gratuitous eyecandy :)

---

### Post by skymt on 2006-10-27
1. It is a buggy and unpolished beta. If you only run the core set of plugins, it's only an unpolished beta. However, most people enable all the eye candy, and suffer through the bugs. As for the driver issue: it's not worth running through GLX on an nVidia card. There are a few things that aren't supported by the stable nVidia drivers, so they go through software (slow). AIGLX won't work at all on nVidia with stable drivers. On the other hand, the beta drivers are more stable than Beryl, so...

2. You can switch between Beryl and plain Metacity with a tray icon (beryl-manager). However, I've found that (with my setup) it takes a change to xorg.conf and a restart of the X server to re-enable GLX. Your mileage will vary.

3. Beryl is really, really cool. Just search Youtube to see just how cool. A lot of people report good performance on weaker cards than yours, so your frame rate should be pretty good.

---

### Post by lixy on 2006-10-27
I just did a clean Edgy install on a relatively old machine (Inspiron 8600), and installing Beryl was a total breeze (Too bad they don't include it in Automatix2 though).
It beats the pants out off OSX and I'm pretty sure I can convince previously reticent people, to switch to Linux now.

Try it! You can easily revert to metacity with the click of a mouse if any issue arises.

---

### Post by CatKiller on 2006-10-27
Thanks guys. I've installed it for him. I hope he'll like it.

It seems to run really well - much better than I was expecting - although some of the effects are fugly to my eyes. I've turned off all the "Dream" transitions, since they seemed the worst, but who knows, perhaps he'll love them and want them on again. He is a funny boy.

Actually, I just tried it, and Unreal Tournament works, even if I forget to turn Beryl off. Not **well**, mind, but it does work. Actually, having beryl-manager open seems to have more of a detrimental effect on performance than using Beryl. I am now a convert and, since my computer is marginally better specced than his, I shall probably install it on mine when I upgrade mine to Edgy.

---

### Post by CatKiller on 2006-11-16
Well, I've **finally** managed to get him round to look at it (don't ask :roll:) and he was *very* impressed. As was my other half actually, and I wasn't expecting that. So thanks again guys for persuading me to do it even though it wasn't my computer, and thanks to all the Compiz and Beryl devs that have done such freakishly good things.

---

### Post by didobuntu on 2006-11-16
Beryl is finer and finer, in my opinion.

---

