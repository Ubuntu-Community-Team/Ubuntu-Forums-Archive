---
title: "x86_64 Feisty: &quot;your hardware does not need any restricted drivers&quot;"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by chrisstankevitz on 2007-08-02
Hi,

I have a Dell M90 with a Quadro FX 2500M.  32 bit Feisty installed my nvidia driver with the restricted drivers manager (RDM); however, 64 bit Feisty's RDM says "your hardware does not need any restricted drivers".  Why?

Thanks,

Chris

---

### Post by Theimon on 2007-08-02
Same thing here, RDM tells me my system doesn't need any restricted drivers........still my Club3d nVidia 8500GT is using the binary 100.14 drivers from nvidia.com.......
Don't know why....

Sure it doesn't really _need_ them, but if I want full 3D support and all that good stuff......the nv driver won't cut it ;)

---

### Post by chrisstankevitz on 2007-08-02
Theimon,

Are you using 64 bit Feisty?  FYI, I want nvidia drivers for their multiple monitor support -- convenient when switching in and out of the docking station.  Works great in 32 bit Feisty.

Chris

---

### Post by Theimon on 2007-08-02
Nope, I'm using the 32bit version, I don't see any benefit in 64bit (yet). However, the "error" message is the same.
But why not install the drivers through apt/Synaptic?

---

### Post by chrisstankevitz on 2007-08-02
Okay, thanks.  My case is a little different because 32 bit RDM sees my nvidia, while 64 bit RDM does not see my nvidia.

---

### Post by Theimon on 2007-08-02
My Ubuntu recognizes the video card but with the wrong amount of memory (it claims 512MB while it physically has 256MB). It's a 8500GT, fairly new so it's not that big a problem. And as said it thinks the card doesn't need restricted drivers, well.........we all know better now do we :)

---

### Post by phenest on 2007-08-14
> **chrisstankevitz said:**
> Hi,

I have a Dell M90 with a Quadro FX 2500M.  32 bit Feisty installed my nvidia driver with the restricted drivers manager (RDM); however, 64 bit Feisty's RDM says "your hardware does not need any restricted drivers".  Why?

Thanks,

Chris

I have an M90. I thought these were 64-bit processors? I which case, doesn't the installer automatically install Feisty as 64-bit? I thought the 64 version of Ubuntu was for AMD's?

---

### Post by chrisstankevitz on 2007-08-14
1. The M90 is 64 bit, but you can use 32 bit if you prefer
2. You need to select beforehand which Feisty installer to use: 32 or 64 bit.
3. "AMD64 ubuntu" works on 64 bit Intel processors. I do not know why they call it by the name "AMD".

---

### Post by Theimon on 2007-08-14
> **chrisstankevitz said:**
> 1
3. "AMD64 ubuntu" works on 64 bit Intel processors. I do not know why they call it by the name "AMD".

Maybe to even it up a little, x86 is patented by Intel so now they both got a trademark in the downloadlist.

I'm just bullshitting you guys, I haven't got a clue why they chose AMD64. It does provide some clarity on the different versions though.....

---

### Post by phenest on 2007-08-15
Thanks for the info guys.

To get back on topic then, my M90 says I require restricted drivers (wireless and video) on both 32 and 64 bit.

---

### Post by dptxp on 2007-08-15
> **Theimon said:**
> Maybe to even it up a little, x86 is patented by Intel so now they both got a trademark in the downloadlist.

I'm just bullshitting you guys, I haven't got a clue why they chose AMD64. It does provide some clarity on the different versions though.....

AMD64 was released much before Intel brought out the 64 bit one with the current architecture.
The one that is backward compatible with 32 bit. So in 64 bit AMD64 is the standard, not Intel.

---

### Post by Theimon on 2007-08-15
> **dptxp said:**
> AMD64 was released much before Intel brought out the 64 bit one with the current architecture.
The one that is backward compatible with 32 bit. So in 64 bit AMD64 is the standard, not Intel.

Ah it all comes back to me now, I knew it but forgot.......thx for the info :)

---

