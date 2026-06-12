---
title: "Vbox 5.2.18 crashes my prompt, etc on Xubuntu 19.04"
date: 2019-04-27
forum: Desktop Environments
---

### Post by winlundn on 2019-04-27
I am running Xubuntu 19.04 in a virtualbox.

It installed ok, but after I resize the display to something larger, install updates, and reboot I get a blank screen.

In another identical vbox instance on the same machine, I install/mount the vbox guest additions image. As soon as it loads my screen stops letting me type text in the command terminal and start menu of Xubuntu. When I reboot I get a blank screen, again.

I have 4G of memory assigned to these VMs. I am also using an NVIDIA video driver on the host, which may be an issue. Does that matter? Ideas?

---

### Post by cruzer001 on 2019-04-27
Why are you using a older version of VirtualBox? 5.2.28 was released this month, your version is dated August 2018. Each release of vBox has its own release of the guest extension pack, did you match them?  Last question, did you install from ubuntu software sources or from the vBox site?

I run ubuntu 18.04 and using the vBox 6.0.xx series, maybe you should give it a try.

---

### Post by winlundn on 2019-04-27
Thanks, I'll try vbox 6.0.x

---

### Post by winlundn on 2019-04-27
I installed vbox from Ubuntu software sources. Maybe I should download virtualbox 6 directly from the main VirtualBox site..? This could help me. Thanks, again cruzer001.

---

### Post by cruzer001 on 2019-04-27
I prefer the virtualbox site. It will have the latest version.

---

