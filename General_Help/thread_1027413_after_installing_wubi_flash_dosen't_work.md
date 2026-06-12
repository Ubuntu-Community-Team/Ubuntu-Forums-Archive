---
title: "after installing wubi flash dosen't work"
date: 2009-01-01
forum: General Help
---

### Post by pizzaguy on 2009-01-01
hello all:After installing wubi i tried to install flash and everything installed properly it even allowed me to  open it wit package installer after all the steps i visited  a flash based site  and was now able to view video wats wrong.

---

### Post by risu_vk on 2009-01-01
which flash player you have installed ??


try removing it from synaptic package manager and select flashplugin-nonfree

regards

---

### Post by pizzaguy on 2009-01-01
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) This one

---

### Post by pizzaguy on 2009-01-01
still dosent work

---

### Post by risu_vk on 2009-01-01
hi, just remove it completely and try installing via synaptic manager which used to work well. Also it can be checked in firefox by : choose Help > About Plug-ins from the browser menu which shows installed plugins.

---

### Post by pizzaguy on 2009-01-01
ok i went to: tool> add-ons> plugins and i see no plugins

---

### Post by risu_vk on 2009-01-01
In synaptic package manager is it like the attached image ? also assuming that all installations are done with root (sudo) previlages.

[http://medicalsignals.googlepages.com/synaptic.png](http://medicalsignals.googlepages.com/synaptic.png)

---

### Post by ithanium on 2009-01-02
take this and istall it
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb")

---

### Post by skuunk on 2009-01-17
I had the same problem and I got around it by installing the 32 bit version of wubi.

You need to uninstall your current version and then reinstall wubi from the command line in Windows with the 32bit parameter

i.e.

wubi --32bit

---

