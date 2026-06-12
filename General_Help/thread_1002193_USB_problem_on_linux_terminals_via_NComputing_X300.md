---
title: "USB problem on linux terminals via NComputing X300 terminals"
date: 2008-12-04
forum: General Help
---

### Post by Aleks` on 2008-12-04
Well, our government did a good job and gave every kid a computer. Yeah I'm talking about the Macedonian government.... Never mind that, computers arrived, Edubuntu 7.04 installed on them, NComputing x300d server, terminals and all.

Now the only problem I noticed so far is the USB *showing* problem. There are 7 monitors hooked up to 1 server (call it a mini server) 6 via X300 terminals connected to the server via ethernet cables on a special NIC and one monitor connected directly to the mini server.

Whenever someone hooks up an USB flash drive it only appears on the monitr/user that is connected directly to the miniserver and it's not visible for others.

I tried changing the permissions in /etc/udev/ for the removable driver to "777" but again, the UFD is mounted by the user that is on the monitor directly connected to the miniserver.

If I umount-it and mount it as the root user on a pre-made "/media/USB/" dir, everyone can access it.

So my question is, how can I make it visible to the other users if its auto-mounted by udev, or how can I make udev mount the USB like the root user and give it 777 permissions so the other users can have rw permissions on it ?


Thanks in advance.

-Aleks

---

### Post by jnyabicha on 2010-03-01
NComputing now have released L-series vSpace software for Linux. This Linux software runs on a standard installation of Ubuntu 8.10 and includes all the powerful desktop virtualization capabilities of our award-winning vSpace for Windows. It also
includes all of our software protections and uses the same registration process as vSpace for Windows.


Also, this new version supports USB and microphone on the L230 (features not available)). Future versions of vSpace for Linux (both L-series and X-series) will normally have their initial releases available for installation on an Ubuntu distribution.


You can download this new Linux release and the documentation from [www.opencodesystems.com/downloads](www.opencodesystems.com/downloads)

NComputing's multi-user technology enables greatly expanded computing capabilities by allowing up to 30 users to simultaneously access a single PC. This multi-user desktop experience supports simultaneous users at lower costs in an easy to use, set-up and maintain environment that is eco friendly. The result is a significantly lower cost of computing, on-going management and power usage that is many times better than a
traditional networked PC model.

Since most users only utilize a few percent of today’s powerful PCs, NComputing leverages this power with small access terminals and proven software that enables a single PC or server to support up to 30 users at once. The goal in the multi-user environment is to maintain the performance of the host computer across many users; and as long as the host CPU, memory or LAN performance is not constrained, each access terminal should operate at a speed similar to the host.

NComputing supports both Linux and Windows. From Windows 2000, Windows XP to Windows Server 2000 and Windows Server 2003. Linux distributions supported include Ubuntu/Edubuntu/kubuntu, SUSE, FEDORA, DEBIAN, CENTOS, REDHAT and others. What I like about the company is their R&D, they are always researching and improving on their products. Remember the Office Station L100? Then came the NComputing L100, and NComputing L1200, and now NComputing L130,NComputing L230. Not to forget the NComputing Xtenda X300.

In East Africa (Kenya, Uganda, Tanzania, Rwanda, Burundi, Congo, Ethiopia, Somalia) you can contact OPENCODE SYSTEMS at [www.opencodesystems.com](www.opencodesystems.com). Their telephone is +254-020-3560507/8, +254-722-681971, +254-721-219190

---

