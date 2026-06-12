---
title: "can't uninstall nvidia binary v185 driver"
date: 2011-04-28
forum: Desktop Environments
---

### Post by rocket777 on 2011-04-28
How can I remove from a command line the nvidia binary v185 driver that I installed using the software center under supported software. I can't do anything gui, so I need to remove this using a command line.

I have a pci card geforce 6200 and it was experiencing some problems with video display so I installed the binary accelerated driver v185. After rebooting the gui became nearly unusable; moving the mouse was acting like a paintbrush erasing the screen, the resolutions were messed up etc.

I was able to get the software center on screen long enough to click on the remove button. I rebooted but the system is still in the same non-functioning state, as though the remove didn't work at all.

---

### Post by ankspo71 on 2011-04-28
Hi,
It appears to me that in Ubuntu 11.04 that the Nvidia 185 drivers are transitional packages for upgrading purposes. The dependencies of the nvidia 185 packages are nvidia-current, which is the nvidia 270 driver in Ubuntu 11.04.

Here's an easy command to run to see which nvidia packages are installed:
```
dpkg --get-selections | grep nvidia

```

You will seee results that look something like this:
```
james@Kubuntu-Natty:~$ dpkg --get-selections | grep nvidia
nvidia-173                                      deinstall
nvidia-common                                   install
nvidia-current                                  install
nvidia-settings                                 install
```
(deinstall means it was installed but already removed)

Then I would run this command to remove them:
```
sudo apt-get remove [COLOR="Red"]package[/COLOR]
```
(replace "package" with the appropriate nvidia packages.)

Hope this helps. PS: If you see nvidia-current is installed remove that too. I recommend leaving nvidia-common installed.

---

