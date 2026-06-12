---
title: "Ubuntu 18.04 VM_L2_PROTECTION_FAULT_STATUS Error"
date: 2019-01-07
forum: Desktop Environments
---

### Post by bstewart on 2019-01-07
I installed ubuntu 18.04 Desktop on a thinkpad A485. 

Every now and then my laptop will freeze, and nothing will happen. I've let it sit for 30mins~ and it never un-froze. Today alone this has happened 6 times.

Any insights or help on how to solve this would be amazing! As having to force restart my laptop multiple times a day via the power button is annoying.

I checked /var/log/syslog and at the time of freeze here are the logs:

> brandon@bstewart ~ $ cat /var/log/syslog | grep -w "Jan 7 16:26:04"
Jan 7 16:26:04 bstewart kernel: [25446.119868] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119872] amdgpu 0000:06:00.0: in page starting at address 0x0000000105601000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119874] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119881] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119882] amdgpu 0000:06:00.0: in page starting at address 0x0000000105604000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119884] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119890] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119891] amdgpu 0000:06:00.0: in page starting at address 0x0000000105605000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119892] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119898] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119900] amdgpu 0000:06:00.0: in page starting at address 0x0000000105600000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119901] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119907] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119908] amdgpu 0000:06:00.0: in page starting at address 0x0000000105601000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119909] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119915] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119917] amdgpu 0000:06:00.0: in page starting at address 0x0000000105603000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119918] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119923] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119925] amdgpu 0000:06:00.0: in page starting at address 0x0000000105606000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119926] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119932] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119933] amdgpu 0000:06:00.0: in page starting at address 0x0000000105607000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119934] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119940] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119941] amdgpu 0000:06:00.0: in page starting at address 0x0000000105602000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119942] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071
Jan 7 16:26:04 bstewart kernel: [25446.119948] amdgpu 0000:06:00.0: [gfxhub] VMC page fault (src_id:0 ring:56 vmid:5 pasid:32768, for process Xorg pid 1807 thread amdgpu_cs:0 pid 1808)
Jan 7 16:26:04 bstewart kernel: [25446.119949] amdgpu 0000:06:00.0: in page starting at address 0x0000000105603000 from 27
Jan 7 16:26:04 bstewart kernel: [25446.119950] amdgpu 0000:06:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x005C0071



I have attached my pc specs using to the pastebin below ***sudo******lshw***[B][I] | less
[/I][/B][https://pastebin.com/V6KPw1G8](https://pastebin.com/V6KPw1G8)

---

