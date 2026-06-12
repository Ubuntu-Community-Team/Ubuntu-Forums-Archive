---
title: "VirtualBox"
date: 2009-03-17
forum: General Help
---

### Post by MikeBasilico on 2009-03-17
Say i load up Vista in virtualbox, should i have any trouble running high powered games like gears of war, and a high powered editor like premeire cs4

All without any compromise

---

### Post by Vince4Amy on 2009-03-17
It wouldn't run anywhere as near as good as it would on a proper install. I suggest you do a dual boot install.

---

### Post by bodhi.zazen on 2009-03-17
Virtualization does NOT directly use your videocard and that is likely to be your biggest limitation.

---

### Post by DGortze380 on 2009-03-17
> **Vince4Amy said:**
> It wouldn't run anywhere as near as good as it would on a proper install. I suggest you do a dual boot install.

It won't run at all due to lack of support for 3D rendering. (ie. no DirectX).

Sorry. Dual Boot. Only Option.

---

### Post by ene_dene on 2009-03-17
OpenGL games should work, but that is a poor subset.

---

### Post by Nano_ext3 on 2009-03-17
You should be able to run simple games that run on say integrated graphics, but because of the VBox limitations , you wont be able to run any of those games.  Your best bet is to Setup a dual boot, or use CrossOver Games (not free, unless they run their annual free keys giveaway, I got mine last year), wine probably wont work.  Nothing is guaranteed.

Cheers!

-Nano

---

### Post by MikeBasilico on 2009-03-18
Crap, not the answer I wanted, I guess ill just go for the mac, I didnt want to, but the premium is worth it if i can run everything without the BS

---

### Post by MikeBasilico on 2009-03-18
but how come ive seen call of duty in virtual windows?

would i have better luck with other virtualization software, i like ubuntu, but cant justify keeping it without this, and i plan on using the internet, so i cant use windows alone, the 8 core mac sounds nice though ;]

---

### Post by fieroboom on 2009-03-18
> **bodhi.zazen said:**
> Virtualization does NOT directly use your videocard and that is likely to be your biggest limitation.

Actually, if I read the options correctly, the [closed source version of VirtualBox](http://www.virtualbox.org/wiki/Linux_Downloads) supposedly supports 3D rendering...

I just installed the closed source today in order to have USB supported in my guest, and I noticed that option in the configuration... But I haven't tried it. I don't see how it could properly support it, since the video card is virtual, but it's something I'm planning to check into/test.
I agree that it still won't be as good as an install on physical H/W, but it's worth looking into I guess.
:D
-Paul

---

### Post by DGortze380 on 2009-03-18
> **fieroboom said:**
> Actually, if I read the options correctly, the [closed source version of VirtualBox](http://www.virtualbox.org/wiki/Linux_Downloads) supposedly supports 3D rendering...

I just installed the closed source today in order to have USB supported in my guest, and I noticed that option in the configuration... But I haven't tried it. I don't see how it could properly support it, since the video card is virtual, but it's something I'm planning to check into/test.
I agree that it still won't be as good as an install on physical H/W, but it's worth looking into I guess.
:D
-Paul

Not good enough to support DirectX. I've tried it, it allowed me to enable some shakey, glitchy, compiz effects. No games though.

---

