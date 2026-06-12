---
title: "Firewire (new stack) permission problem"
date: 2010-11-10
forum: Desktop Environments
---

### Post by veger on 2010-11-10
I have updated my computer to Kubuntu 10.10 (which has the new firewire stack enabled by default) and now my firewire application is giving permission related problems.

I try to read CSR_CHANNELS_AVAILABLE_HI (defined in libraw1394 which is used by the application) to see which isochronous channels are available to use:

```

octlet_t channels;
raw1394handle_t handle = raw1394_new_handle_on_port(port);
nodeid_t irm_node = raw1394_get_irm_id(handle);
raw1394_read(handle, irm_node, CSR_REGISTER_BASE + CSR_CHANNELS_AVAILABLE_HI, sizeof(octlet_t), (quadlet_t *) &channels);

```

With the old stack (raw1394) there are not problems and it runs fine and I get the octlet back containing the information about the free channels.

But with the new stack (firewire_core and friends) I get a 'permission denied' (errno = 1) error. I do have permission to read/write /dev/fw* and I even tried running the application as root without any luck.

If I read the config rom of a node (located at CSR_CONFIG_ROM) there are no permission problems and I am able to get the information/

What am I doing wrong? Did something change with the new stack (even though libraw1394 should be compatible with both stacks)? Is it a bug?

---

### Post by Chame_Wizard on 2010-11-10
what does *dmesg* says?

---

### Post by veger on 2010-11-10
It looked fine to me, so I did not post it earlier, but here it is:

*dmesg | grep firewire*
[    0.944931] firewire_ohci 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.110330] firewire_ohci: Added fw-ohci device 0000:15:00.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    1.591344] firewire_core: created device fw0: GUID 00061b032a31099d, S400
[    1.612255] firewire_core: created device fw1: GUID 000b9900835d5802, S400
[    1.633166] firewire_core: created device fw2: GUID 000b9900835e180a, S400
[    1.633170] firewire_core: phy config: card 0, new root=ffc2, gap_count=7

---

### Post by veger on 2010-11-12
I (accidentally) stumbled upon the answer when implementing some other firewire related stuff:
It is not allowed to read more than 1 quadlet (4 bytes) of data at once. The IRM (implemented by the new firewire stack) returns the permission denied error.

So by splitting the raw1394_read() call of the example code into two separate raw1394_read() calls, the problem gets solved...
I suppose this is some (new) firewire protocol specification, which is not implemented in the old stack (raw1394)..?

---

