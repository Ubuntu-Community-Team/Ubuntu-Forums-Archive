---
title: "wireless adpater connection"
date: 2005-12-27
forum: Desktop Environments
---

### Post by dsjas297 on 2005-12-27
How do I setup Ubuntu so that it recognizes my wireless adapter? It is an Airlink101 PCI adapter, if that helps.

---

### Post by Lambert on 2005-12-27
More info is needed. run these commands and post back their  output

```
sudo lspci -v | grep -A 8 Ethernet
```

```
 sudo lshw -C network
```

---

### Post by dsjas297 on 2005-12-28
Here is the output:

Didn't get any noticeable out put for the first command:

```
sudo lspci -v | grep -A 8 Ethernet
Password:
```

The second one came up with this:

```
sudo lshw -C network  
      *-network UNCLAIMED       
      description: Network controller
      product: RaLink
      vendor: RaLink
      physical id: b
      bus info: pci@01:0b.0
      version: 00
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list
      resources: iomemory:f4110000-f4117fff irq:5
```

Hope it helps.

---

### Post by 0MG on 2005-12-29
try running the first command again and post the output after entering your user password.

Looks like you might need ndiswrapper for this, don't quote me though, I'm still a newb myself. It got my wireless up, that's all I know

---

### Post by dsjas297 on 2005-12-29
Ok, I know I entered my password the first time, but I tried it again anyways. Still had no output. So I tried it without pipelining through the "grep" command. It showed the list of pci devices, including my card, but listed that as an unknown device.

So I tried using ndiswrapper. Driver was installed successfully and I used the "-m" option to to tack it on as a kernel module.

However, when I restarted my computer, the card still did not appear on the list of network devices.

---

### Post by dsjas297 on 2005-12-29
Oops. I didn't read the ndiswrapper stuff well enough. Used the wrong driver. Trying the one I should have used.

---

### Post by dsjas297 on 2005-12-30
Googling around for drivers for my chipset, I found that they will not be available until next month. Ah well, I'll just have to wait until then.

---

