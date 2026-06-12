---
title: "Regnum online black screen"
date: 2010-01-30
forum: Gaming &amp; Leisure
---

### Post by knighthaq on 2010-01-30
everything installed and updated etc but just get a black screen?
 any ideas 

ronnie@ronnie-desktop:~$ sudo lshw -C display
[sudo] password for ronnie: 
  *-display               
       description: VGA compatible controller
       product: GT200 [GeForce GTX 260]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dc000000-ddffffff ioport:bf00(size=128) memory:dff80000-dfffffff(prefetchable)
ronnie@ronnie-desktop:~$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
ronnie@ronnie-desktop:~$

---

### Post by knighthaq on 2010-01-30
found the answer myself since i manually installed my video driver i had to go install the envyngcore all works now.  I also had to change my shader model under options.it was trying to lode shader model 4 default, so i dropped it to shader 2 or 3 and that helped :p

---

