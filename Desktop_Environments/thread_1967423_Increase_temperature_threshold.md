---
title: "Increase temperature threshold"
date: 2012-04-28
forum: Desktop Environments
---

### Post by DeceptiveHornet on 2012-04-28
Hello,

I have been using kubuntu 12.04x64 for a week or two since the beta became available. It works wonderful. I have but one small problem. The laptop (HP Pavilion G-7 1110so) tends to get a bit hot. It runs at about 70c when idle or just browsing the net without any graphical loads. 

When it hits 80c the fan kicks in and the temperature drops like a stone to roughly 70c. I would like to try and keep the laptop from never coming close to 70 in the first place. How can i set the Kubuntu installation to activate the fan when the laptop hits maybe 57-60c? The noise issues won't be an issue for me. I just don't want to wear'n'tear the hardware more then necessary due to heat exposure.

---

### Post by DeceptiveHornet on 2012-04-28
Bump

---

### Post by DeceptiveHornet on 2012-05-01
As much as i love the *Buntu linux, it seems impossible to even get one lousy answer. I have googled me *** off but not found anything helpful. Ignoring people is one idiotproof way of scaring people off.

So i assume that either nobody knows anything or nobody can be bothered to either tell how to fix it or direct me to some other resource that can.

Good to know how the linux support works.

---

### Post by mips on 2012-05-01
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)
[http://ubuntuforums.org/showthread.php?p=11509638](http://ubuntuforums.org/showthread.php?p=11509638)
[http://forums.debian.net/viewtopic.php?f=16&t=62579](http://forums.debian.net/viewtopic.php?f=16&t=62579)
[https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+power+management&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=pzB&channel=fs&sclient=psy-ab&q=kubuntu+power+management&oq=kubuntu+power+management&aq=f&aqi=&aql=&gs_l=serp.3...13002.13002.0.13370.1.1.0.0.0.0.0.0..0.0...0.0.NWaTE4yM8LE&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=f3feea7f18c4f341&biw=1432&bih=803](https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+power+management&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=pzB&channel=fs&sclient=psy-ab&q=kubuntu+power+management&oq=kubuntu+power+management&aq=f&aqi=&aql=&gs_l=serp.3...13002.13002.0.13370.1.1.0.0.0.0.0.0..0.0...0.0.NWaTE4yM8LE&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&fp=f3feea7f18c4f341&biw=1432&bih=803)
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by schnelle on 2012-05-01
> **DeceptiveHornet said:**
> As much as i love the *Buntu linux, it seems impossible to even get one lousy answer. I have googled me *** off but not found anything helpful. Ignoring people is one idiotproof way of scaring people off.

So i assume that either nobody knows anything or nobody can be bothered to either tell how to fix it or direct me to some other resource that can.

Good to know how the linux support works.

You didn't specify what CPU and GPU your laptop has.

If you have ATI graphic card, opensource drivers have bad power management. Install proprietary drivers from Additional drivers and your card should be much colder/cooler.

---

### Post by mips on 2012-05-01
> **schnelle said:**
> You didn't specify what CPU and GPU your laptop has.

If you have ATI graphic card, opensource drivers have bad power management. Install proprietary drivers from Additional drivers and your card should be much colder/cooler.

I just google his laptop model and he seems to have one of those laptops with dual GPUs, Intel & AMD Radeon HD 6470M.

These things can be finicky with linux as far as I'm aware.

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I would do specific searches for that setup regarding linux, for example Ubuntu dual GPU Intel AMD   (also add the hp model in there as another option as some of them you can switch on off via a mux)

[http://ubuntuforums.org/showthread.php?t=1786618](http://ubuntuforums.org/showthread.php?t=1786618) I would disable the amd if you don't do heavy 3d stuff in ubuntu as it generates heat and uses battery power

---

