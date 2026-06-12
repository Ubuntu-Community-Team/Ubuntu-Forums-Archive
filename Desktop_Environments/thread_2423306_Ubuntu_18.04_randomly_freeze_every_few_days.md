---
title: "Ubuntu 18.04 randomly freeze every few days"
date: 2019-07-20
forum: Desktop Environments
---

### Post by thumper76 on 2019-07-20
Ubuntu 18.04 randomly freeze every few days. Mouse and keyboard not responsive. Screen is still visible, but clock stopped.
AMD Athlon 200ge, Asus A320M-K, Corsair DDR4 8G. Is this a hardware or software problem?

This is from the sys.log at the exact time:

```
Jul 20 14:28:58 Power-System kernel: [10838.318516] gmc_v9_0_process_interrupt: 31 callbacks suppressed
Jul 20 14:28:58 Power-System kernel: [10838.318524] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318531] amdgpu 0000:07:00.0:   at page 0x0000000101402000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318536] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00101031
Jul 20 14:28:58 Power-System kernel: [10838.318544] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318548] amdgpu 0000:07:00.0:   at page 0x0000000101401000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318551] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318559] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318563] amdgpu 0000:07:00.0:   at page 0x0000000101407000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318566] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318574] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318578] amdgpu 0000:07:00.0:   at page 0x0000000101406000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318581] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318589] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318592] amdgpu 0000:07:00.0:   at page 0x0000000101405000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318595] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318603] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318607] amdgpu 0000:07:00.0:   at page 0x0000000101403000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318610] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318619] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318623] amdgpu 0000:07:00.0:   at page 0x000000010140a000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318626] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318634] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318638] amdgpu 0000:07:00.0:   at page 0x0000000101409000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318641] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318649] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318652] amdgpu 0000:07:00.0:   at page 0x000000010140d000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318655] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:28:58 Power-System kernel: [10838.318664] amdgpu 0000:07:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:1 pasid:32769)
Jul 20 14:28:58 Power-System kernel: [10838.318668] amdgpu 0000:07:00.0:   at page 0x000000010140b000 from 27
Jul 20 14:28:58 Power-System kernel: [10838.318671] amdgpu 0000:07:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
Jul 20 14:29:08 Power-System kernel: [10848.434013] [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx timeout, last signaled seq=212996, last emitted seq=212998
Jul 20 14:29:08 Power-System kernel: [10848.434019] [drm] GPU recovery disabled.
```

---

### Post by Autodave on 2019-07-21
Since no one else has jumped in, let me try.  From what I see, there might be an issue with your graphics card.  Does this setup have a separate graphics card or are you using the onboard graphics?  If you have a separate graphics card, I would remove it and try using the onboard graphics to see if the problem persists.  If the problem goes away, the card may not have been seated fully, it could be a bad card, or you could have a weak/failing power supply.

---

### Post by CatKiller on 2019-07-21
> **thumper76 said:**
> 
AMD Athlon 200ge
The AM4 motherboards benefit from upgraded firmware - the launch versions were generally a bit rough around the edges - and AMD graphics benefit from being on the newer versions of their drivers. There is the Hardware Enablement Stack, and there are PPAs, for the newer stuff. I would try updating all of that and see if the situation improves.

---

### Post by thumper76 on 2019-07-21
Reply to Autodave

Thanks for the reply. I am using the integrated graphics processor. it's a brand new 400w EVGA power supply. Could be that the 200ge is faulty. I guess I'll have to wait and see if the freezes get worse.

---

### Post by thumper76 on 2019-07-21
Reply to CatKiller

Thanks for the reply. I updated the BIOS a few weeks ago. I checked and I have the latest HWE. I'll have to see if the freezes get more frequent. I thinking possibly a faulty GPU.

---

### Post by Autodave on 2019-07-22
Make sure that all of your electrical connections are secure.

---

### Post by him610 on 2019-07-23
There are certain combinations of MB, GPU, and PSU that are incompatible. It could be an issue that requires a good bit of investigation.
Good luck.

---

### Post by Tom_Williams on 2019-07-31
I am running on a Dell Optiplex 745; some time ago, this machine started freezing randomly, and I was not sure what was the cause; I increased the RAM from 4 GB to 8 GB.  Now, instead of freezing several times a day, it freezes rarely, and only when I have many tabs open in the browser. Some times, as I am opening more tabs, I can see the machine slowing down; as long as I start dealing with all the open pages before I get too many open, the machine just keeps going;  if I am not paying attention, and open too many taps, or have too many other things running, things just stop responding, and I must reboot.

---

### Post by guiverc on 2019-07-31
> **Tom_Williams said:**
> I am running on a Dell Optiplex 745.  ..


This may not be related to your issue, but I'd firstly suggest a ramtest of your system to ensure you don't have ram issues.

I've had 3 of 6 dell 745 & 755's die in the last 12-18 months because they started to 'freeze', and on a cap-check the reason was pretty obvious (ie. swallen capacitors).  Your description reminds me of the issues I detected in mine in the early stages (in my case the freezes got more frequent, and then on occasion they started to refuse to boot finally getting me to open the cases for cap-check).

---

### Post by thumper76 on 2019-08-16
A follow up to my problem with ubuntu 18.04 freezing up. The problem has  seemed to have gone away. No more freeze ups. Two things were changed.  The Ubuntu kernel was upgraded to 5.0.0-25-generic and I turned off performance settings and hardware acceleration in Firefox. I'm not sure what solved the problem, but I'm glad it's gone!!

---

