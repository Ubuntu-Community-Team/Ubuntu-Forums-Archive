---
title: "x-server doesn't start properly after beryl removal"
date: 2007-10-02
forum: Desktop Environments
---

### Post by Exonimus on 2007-10-02
Hello everyone,

I've recently removed Beryl from my desktop. I wanted to do an experiment and it said the beryl files could be in the way,so I removed them. I went to the synaptic package manager, removed all files associated with beryl and rebooted. Now, xserver doesn't start properly. I though I might've deleted some important files, so I did: apt-get install beryl emerald-themes beryl-manager

it reinstalled everything. Rebooted, same problem. Now, I tried  sudo dpkg-reconfigure xserver-xorg to no avail(at first). However, when I selected vesa instead of NVIDIA, it worked. However, every time I reboot my pc, I have to re-enter that command. Is there any way I can get that command to work at boot? or is there a way I can re-select that nvidia? at least, I though I needed to use nvidia since I've got a Geforce 4 MX460(I already installed the drivers for it) forgive me if this is a stupid question or if I posted this in the wrong section.

---

### Post by Exonimus on 2007-10-02
sorry. Forgot to add I'm runny Feisty

---

