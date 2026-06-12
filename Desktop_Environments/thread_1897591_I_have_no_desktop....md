---
title: "I have no desktop..."
date: 2011-12-19
forum: Desktop Environments
---

### Post by Howy on 2011-12-19
Hello there. I've been happy with my computer with my ATI graphics card and Unity. Until today.
I rebooted because there was a new kernel, and I had no idea about it before I was back in.
The fglrx driver was malfunctioning with X, again... -.-
On the drawables, I saw black boxes, and now I've got my way out of fglrx. Uninstalled, in other words. Now, I'm stuck without *any* OpenGL support whatsoever.
I don't understand the open source driver: where is it? I can't find it, and the "radeon" one certainly doesn't do a thing. I'm stuck in Unity 2D without compositing. I have no window decorator working, and everything is hell.
So please, tell me there is at least something I can do to make this work again?
I was running the fglrx-updates package, and the same results appeared with the fglrx package. (They're different versions, obviously) But both won't work with X, and I get the black boxes. I'm not able to provide a screenshot, because the desktop is unusable at the moment, and I'm bound to use a miserable Windows laptop. :(

The only thing that comes to my mind is downgrading the X server to the previous one, and sticking it till I know the coast is clear for fglrx.
Would this be a good or a bad idea to perform? I know what I'm going to do, only if I can find which package version it was previously.

Thanks in advance.

EDIT: Ok, now I've got the Radeon driver up and running, but only with 2D support and very scarce 3D support. Too scarce for me. (I could play Halo 2 in VMWare with fglrx.)
In addition I'm forced to use Unity 2D + Metacity, because GL_ARB thingys don't work. -.-
The desktop works, yes, but it's kinda useless to me because I can't play my favorite games at all now.
And I'm still considering to downgrade the X server.

I've just realized this topic belongs in General. (Plz move..?)

Ok, now I'm reallyreally confused here. In the past power-on, I've not even touched fglrx or X. The only new thing is the kernel and a couple of other applications, which seem harmless. (MyUnity and Shutter)
I don't understand this: would the kernel be able to make this much trouble..?



Turns out the issue was with fglrx. The version I had broke somehow, and the latest version, freshly from AMD and built on my desktop, worked perfectly. I think I'll rather do it this way in the future, because it really worked, and everything is back to normal. With a slightly upgraded OpenGL version. :)

---

