---
title: "Which flavor is right for me?"
date: 2015-05-15
forum: Desktop Environments
---

### Post by sypher2 on 2015-05-15
Im currently running a 2011 macbook pro with 500GB HD , 4GB RAM, and i dont know what flavor to install along side OSX. Im currently running Kubuntu 15. It feels a little heavy though. After not to long, my macbook's fan ( i think) kicks in and stays on for about a minute and it makes me nervous. aha.. Im wondering which flavor of linux i should be using. In my desired environment, it would be lightweight-average, i like having multiple workspaces, i NEED to be able to import tools from either backbox or kali, and i would want a sleek design for the desktop layout. any suggestions?

---

### Post by wildmanne39 on 2015-05-15
Sounds like you might would like xubuntu, you have enough resources to run whatever ubuntu version you want too.
Lubuntu is also light but xubuntu is more polished.
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by sypher2 on 2015-05-15
i really like your Xubuntu suggestion now that im looking at it! It actually looks just like Backbox. Only reason im not using backbox is because i kept noticing small bugs that wouldnt go away even when i installed a fresh backbox. Im sure most kinks will be fixed or being worked on on the LTS trusty version. Thank you!

---

### Post by bapoumba on 2015-05-15
That wont answer your question I know. I use Ubuntu in a VM (VirtualBox) on the OSX host. Fans and video are the two stoppers for me for now to install Ubuntu alongside OSX. VB works really well, is maintained, video works with the guest additions, and all the machine resource is handled by the OSX host. Ubuntu can be installed directly from the iso file. I gave 2GB base memory to VB, 25GB space, 128 MB video memory (I do not recall if this was a default or if I tried different values).

I'm currently running ubuntu-mate, which I like much, without any resource issue. The only one thing that does not work is the MBP webcam that I cannot have recognized.

---

### Post by buzzingrobot on 2015-05-15
I tried Ubuntu with Unity and Fedora Gnome on a 2011  Macbook Pro 8,2 a while back. I found fan control was often an issue. The 8,2 has Apple's version of hybrid video:  A discrete Radeon video card and onboard Intel video.  OS X uses a proprietary hardware mechanism to very transparently switch those cards. (It defaults to the Intel video and switches to the Radeon when demand increases.) Since the hardware that enables that is proprietary, the Linux kernel can't use it.  I found that *any* use of the Radeon would instantly max out the fans. (I believe this is a precaution:  Developers can't control the fans so they ensure they run at maximum to protect the machine.) Meanwhile, on the Intel, the fans did not run at all, which was also worrying. 

In addition, the system would not boot unless one or the other of the video cards was disabled *before the kernel took control* during the boot process.

MacBook's can vary in large and small ways from minor release to minor release.  That means that how-to guidance found on the web may only work with that person's specific model.

---

