---
title: "Will I be able to NOT run Compiz under Natty?"
date: 2011-03-22
forum: Desktop Environments
---

### Post by andrei_1 on 2011-03-22
I read that Natty will use Unity as the preferred desktop environment, together with Compiz.

I found that on my system Compiz - while very neat - will cause instability so I'd rather not use it.

How would the desktop stack look for a user not wanting to run Compiz under Natty?

Can I use Mutter with Unity? Or maybe I should replace Unity with Gnome? Will my Ubuntu like this (replacing Unity with Gnome)? Will Ubuntu make it easy for users to dump Compiz if they want to do so?

---

### Post by Copper Bezel on 2011-03-22
There is a Unity 2D implementation that uses Mutter, and while it's set up as an automatic fallback when Compiz isn't able to run, you should also be able to force the system to use it. 

You can also still use the classic Gnome desktop as a login session option, simply by logging out and selecting it after you select your name from the user list. (The login screen will save your preference.)

For future reference, Unity isn't a replacement for Gnome, but rather a plugin for it.

---

### Post by andrei_1 on 2011-03-22
> **Copper Bezel said:**
> There is a Unity 2D implementation that uses Mutter, and while it's set up as an automatic fallback when Compiz isn't able to run, you should also be able to force the system to use it. 

You can also still use the classic Gnome desktop as a login session option, simply by logging out and selecting it after you select your name from the user list. (The login screen will save your preference.)

For future reference, Unity isn't a replacement for Gnome, but rather a plugin for it.

Thanks, so I understand I will have options. Also, Wikipedia says: "But Unity-2D will not be shipped on the Ubuntu 11.04 CD, instead the classic GNOME desktop will be the fall-back."

Can you please elaborate on this though "Unity isn't a replacement for Gnome, but rather a plugin for it" ?

From all I've read, Unity looks like a replacement, and certainly, considering that one has to choose to either run Gnome or replace it with Unity it does look like a replacement...

---

### Post by Copper Bezel on 2011-03-22
Nope, under the hood, it's all Gnome. It's a panel app and a Compiz plugin (or, in 2D, a panel app and some Mutter settings.) It's listed as a separate session because it doesn't load some services required by the Classic desktop.

---

### Post by andrei_1 on 2011-03-22
> **Copper Bezel said:**
> Nope, under the hood, it's all Gnome. It's a panel app and a Compiz plugin (or, in 2D, a panel app and some Mutter settings.) It's listed as a separate session because it doesn't load some services required by the Classic desktop.

Ah, OK, actually I should have read Wikipedia's entry on Unity - [http://en.wikipedia.org/wiki/Unity_(desktop_environment](http://en.wikipedia.org/wiki/Unity_(desktop_environment)) - that would have cleared my confusion.

---

### Post by JRV on 2011-03-22
Here is the link to Unity2d installation instructions:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

---

### Post by anilcr on 2011-04-13
I'm able to get compiz running via the terminal but cant get it to run on startup. Anyway I can do that? make compiz default instead of Metacity?

---

### Post by andrei_1 on 2011-04-13
> **anilcr said:**
> I'm able to get compiz running via the terminal but cant get it to run on startup. Anyway I can do that? make compiz default instead of Metacity?

System/Preferences/Appearance/Visual Effects: anything else here other than "None" will run Compiz.

---

### Post by anilcr on 2011-04-13
> System/Preferences/Appearance/Visual Effects: anything else here other than "None" will run Compiz.
not on Natty, it doesn't have that option for some reason

---

