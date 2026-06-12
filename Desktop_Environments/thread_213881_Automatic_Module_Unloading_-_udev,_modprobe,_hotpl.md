---
title: "Automatic Module Unloading - udev, modprobe, hotplug?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by wickwire on 2006-07-11
Hi,

After a lot of google-digging, forum-digging and headaches, I'm stuck with this one:

Whenever I plug a new USB device, the system automatically loads the necessary kernel modules.

Afterwards, when I unplug the device, the modules remain loaded.

I'd like to be able to set things up so that the system also performs automatic module unloading, whenever a given module and its dependencies aren't being used anymore.

I've been reading about hotplug, udev and modprobe - but I still can't figure it out.

Hotplug shows up in Synaptic, but when I try to install it, it says:
hotplug:

Package hotplug has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

I then read somewhere that the new udev replaced hotplug in Ubuntu. I'm with dapper drake.

Can anyone help me? Thanks in advance!

---

