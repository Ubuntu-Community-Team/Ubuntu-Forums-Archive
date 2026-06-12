---
title: "qemu windows 98 and network?"
date: 2006-03-20
forum: Desktop Environments
---

### Post by crixtiano on 2006-03-20
Hi,

I'm running a Windows 98 under Qemu under Ubuntu Breezy. But I can't configure the network. Please, how to configure the network?

2nd Question: 

is it possible to ssek a windows 98 folder to a Linux system file fonder? Example: I want "/home/cris/projects" come to be "F:\" in Windows 98 under Qemu. Is it posible?

Thanks.

Cristiano M. Magalhaes

---

### Post by dragomirov on 2006-03-20
For using qemu there's a good guide here [https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo]("https://wiki.ubuntu.com/WindowsXPUnderQemuHowTo")

Then for the network issue: [http://www.h7.dion.ne.jp/~qemu-win/HowToNetwork-en.html]("http://www.h7.dion.ne.jp/~qemu-win/HowToNetwork-en.html")

For sharing folders from and to a virtual machine, share your linux folder with samba and mount them in windows

h&k

---

