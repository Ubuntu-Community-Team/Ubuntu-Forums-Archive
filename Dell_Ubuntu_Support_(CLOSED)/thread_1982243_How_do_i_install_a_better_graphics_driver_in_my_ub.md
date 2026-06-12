---
title: "How do i install a better graphics driver in my ubuntu"
date: 2012-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rpupa on 2012-05-18
I was doing animation in blender and i realized that rendering in ubuntu takes more time then in windows seven with blender. I think it might be because of the Video-Driver, Or Graphics-Driver whatever, and I think the default driver that comes with ubuntu-12.04 is not so efficient as it is not specific with my driver. Can anybody suggest what to do?

---

### Post by sikander3786 on 2012-05-18
Press the <Super> (Windows logo) key and search the Dash for 'Additional Drivers' and start it. If the drivers for your graphics card show up there, simply install the most recent version and your problem will be solved, hopefully.

If there aren't any drivers available, search the Dash for 'Terminal' and start it and post the output of this command:

```
lshw -c video
```

---

### Post by mikewhatever on 2012-05-18
Can you tell us the model of your graphics card. The only non-specific driver I know of is vesa. Are you should it is in use? Do you know what driver is in use?
Can you post the output of **lspci | grep -A1 VGA**.

Generally, no matter what graphics card you use, a Windows driver will be more efficient then the Linux one. Windows graphics drivers are just better.

---

### Post by rpupa on 2012-05-18
> **sikander3786 said:**
> Press the <Super> (Windows logo) key and search the Dash for 'Additional Drivers' and start it. If the drivers for your graphics card show up there, simply install the most recent version and your problem will be solved, hopefully.

If there aren't any drivers available, search the Dash for 'Terminal' and start it and post the output of this command:

```
lshw -c video
```
*-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:fc000000-fc3fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc400000-fc4fffff

---

### Post by rpupa on 2012-05-18
> **mikewhatever said:**
> Can you tell us the model of your graphics card. The only non-specific driver I know of is vesa. Are you should it is in use? Do you know what driver is in use?
Can you post the output of **lspci | grep -A1 VGA**.

Generally, no matter what graphics card you use, a Windows driver will be more efficient then the Linux one. Windows graphics drivers are just better.
The output of command is--->
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by rpupa on 2012-05-18
By the way, the "Additional Drivers" has not listed any drivers for my system

and my laptop is Dell studio 1555

---

### Post by mikewhatever on 2012-05-18
You have an Intel GPU, and the correct driver, i915, is in use.

Additional graphics drivers are only available for Nvidia and AMD.

---

### Post by rpupa on 2012-05-18
Thanks guys , thanks for help. I think now that the problem is not with my driver and it is the normal time such a heavy program takes.

---

