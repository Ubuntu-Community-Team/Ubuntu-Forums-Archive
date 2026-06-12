---
title: "Windows in VirtualBox for gaming?"
date: 2008-12-24
forum: Gaming &amp; Leisure
---

### Post by Wisp558 on 2008-12-24
Is this a feasable thing to do? Will I take a huge performance hit from running a VM? Comments in general? (this would be XP)

---

### Post by dannytatom on 2008-12-24
I'm not 100% sure on this, but I don't think VirtualBox can render the 3D graphics most (newer) games require.  There's a more technical way of saying that, but I can't think of 'em. ;D

---

### Post by damis648 on 2008-12-24
Due to how a VM works, 3D hardware acceleration is currently not possible. Sorry. :(

---

### Post by namdung on 2008-12-24
Graphic intensive games may not function properly in Virtualbox. I'm unable to even use Advanced Desktop Effects in Virtualbox.

---

### Post by eragon100 on 2008-12-25
> **damis648 said:**
> Due to how a VM works, 3D hardware acceleration is currently not possible. Sorry. :(

Haven't you been following [www.phoronix.com](www.phoronix.com) ? Since two weeks, virtualbox has full opengl 3d graphcs acceleration for windows vm's. It is experimental, so it runs in debug which slows down performance, but games like warcraft 3 work fine in opengl mode. When it goes out of debug, you should be able to play other games with opengl renderers with it, such as homeworld 2 and unreal tournament 3. Direct3d support is planned for the (near) future.

---

### Post by crazyfuturamanoob on 2008-12-25
Yea as mentioned above, no 3D hardware acceleration, no 3D games.
I tried even tried it with winXP, only some boring 2d chess games work. :(

Because most games work on windows only, and no 3d acceleration for VM, 
there's no reason to use windows VM, as linux does everything better and with 3d acceleration.

Edit: Oh wait eragon100 told about a VM with 3d acceleration :D

---

### Post by Greyed on 2008-12-25
> **eragon100 said:**
> Haven't you been following [www.phoronix.com]("http://www.phoronix.com") ? Since two weeks, virtualbox has full opengl 3d graphcs acceleration for windows vm's.

Uhm, nope.  And since the front page has nothing about that going back to Dec 8th care to link the specific story instead of making us dig for it?

---

### Post by eragon100 on 2008-12-25
> **Greyed said:**
> Uhm, nope.  And since the front page has nothing about that going back to Dec 8th care to link the specific story instead of making us dig for it?

From [www.virtualbox.org](www.virtualbox.org) :

New Dec 17, 2008
VirtualBox 2.1.0 released!
Sun today released VirtualBox 2.1.0, a major update with exciting new features: among them better 64-bit support, hardware virtualization on the Mac, **3D acceleration**, easier networking on Windows and Linux plus full VMDK/VHD support including snapshots. See the ChangeLog for a detailed list of changes.

---

### Post by Greyed on 2008-12-25
I meant the article on the first site you mentioned but thanks anyway.

---

### Post by damis648 on 2008-12-25
> **eragon100 said:**
> From [www.virtualbox.org](www.virtualbox.org) :

New Dec 17, 2008
VirtualBox 2.1.0 released!
Sun today released VirtualBox 2.1.0, a major update with exciting new features: among them better 64-bit support, hardware virtualization on the Mac, **3D acceleration**, easier networking on Windows and Linux plus full VMDK/VHD support including snapshots. See the ChangeLog for a detailed list of changes.

Hm... I am using closed-source vbox from their repos and it's not up yet. :(

---

### Post by fela on 2008-12-25
> **eragon100 said:**
> Haven't you been following [www.phoronix.com](www.phoronix.com) ? Since two weeks, virtualbox has full opengl 3d graphcs acceleration for windows vm's. It is experimental, so it runs in debug which slows down performance, but games like warcraft 3 work fine in opengl mode. When it goes out of debug, you should be able to play other games with opengl renderers with it, such as homeworld 2 and unreal tournament 3. Direct3d support is planned for the (near) future.

Yes but it would still suffer a performance hit compared with running windows natively (although the mere mention of that makes my skin crawl :P).

---

### Post by obsrv on 2008-12-25
I use WINE for windows gaming and it is OK. I seen that VBOX has 3D Acceleration but I use it only for testing other Linux distros :)

---

### Post by eragon100 on 2008-12-25
> **obsrv said:**
> I use WINE for windows gaming and it is OK. I seen that VBOX has 3D Acceleration but I use it only for testing other Linux distros :)

It only works for windows guests (host doesn't matter) right now, so you won't be able to use 3d acceleration in it if you use it to test other linux distributions :(

---

### Post by Wisp558 on 2008-12-26
Hmmm... So, to consolidate...

The repo version is old, and I'd need to compile from source...

Does it supposrt 3d accel with OpenGL AND DX or just OpenGL?

How much of the performance hit would be from things like, say, compiz and gnome? Mostly because for something like this I would be running it in Fluxbox anyways.

3d accel works only for virtual windows boxes, and not virtual linux boxes...

---

### Post by eragon100 on 2008-12-26
> **Wisp558 said:**
> Hmmm... So, to consolidate...

The repo version is old, and I'd need to compile from source...

Does it supposrt 3d accel with OpenGL AND DX or just OpenGL?

How much of the performance hit would be from things like, say, compiz and gnome? Mostly because for something like this I would be running it in Fluxbox anyways.

3d accel works only for virtual windows boxes, and not virtual linux boxes...

You don't need to compile from source, sun has .debs on the webpage.

According to forum posts I've read, you can easily play warcraft 3 in opengl mode with compiz on, so no problem if you would run it.

Only opengl 3d works right now, DX is planned for the (near) future. A lot of windows only games, such as unreal tournament 3, homeworld 2, oblivion, knights of the old republic 1 and 2 for example, have opengl renderers, so they should all work. (you might have to provide a "use opengl" sort of argument from the commandline, they might default to using direct 3d. But they should work without problems.)

enjoy :wink:

---

### Post by Dedoimedo on 2008-12-26
I've tested the functionality ... gonna post a short review soon.
It works well with opengl games, especially if the host is linux, the guest must be windows. But it gives reasonable performance.

Wait a week and you'll get the review uploaded :)

Dedoimedo

---

