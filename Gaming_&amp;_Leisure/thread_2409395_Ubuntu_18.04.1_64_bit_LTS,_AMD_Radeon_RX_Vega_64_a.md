---
title: "Ubuntu 18.04.1 64 bit LTS, AMD Radeon RX Vega 64 and Steam"
date: 2019-01-01
forum: Gaming &amp; Leisure
---

### Post by Welly Wu on 2019-01-01
I installed Ubuntu 18.04.1 64 bit LTS GNU/Linux on my mid-2017 AVA Direct. Here are some but not all of the PC hardware components installed:

ASUS ROG Crosshair VI Hero (EFI firmware revision version 6401) x370 AM4 motherboard
AMD Ryzen 5 1600X CPU
ASUS ROG STRIX AMD Radeon RX Vega 64 HBM2 8GB GPU
Kingston Savage 32 GB DDR4 CL13 2,666.00 MHz (4 X 8 GB) DIM RAM
Intel 6000p 512 GB PCIe NVMe TLC SSD
2x WD Black 1 TB HDDs using mdadm in RAID-0
1x WD Black 6 TB HDD
AOC G2460PF 24" 1920 X 1080P 1 ms 144 hZ AMD FreeSync gaming monitor via DisplayPort 1.2

I added the Padoka stable PPA and restarted without issues. I installed Ubuntu Kernel Update Utility and I tried Linux kernel versions 4.18.20, 4.19.13 and 4.20.0 64 bit.

The default Linux kernel installed is 4.15.0-43 generic AMD64. That works just fine. Linux kernels 4.18.20, 4.19.13 and 4.20 boot up fine, but whenever I run Steam, my gaming desktop PC freezes and locks up and this is repeatable. I am not sure why.

Can someone help me to troubleshoot this problem so I can pinpoint what is causing it and find a solution? What technical information do you need from me to help you?

I hope this gets enough attention and someone here or elsewhere can help me to find a solution.

The reason why I installed the Padoka stable PPA is because I run Steam using Steam Play and Proton to play Sniper: Ghost Warrior 3 Season Pass. After I installed the Padoka stable PPA, this PC game title runs, but there is a lot of lag, judder and the gameplay is jerky. I researched that I need a newer Linux kernel version to go along with the Padoka stable PPA, but I can't figure out why running Steam keeps locking up my gaming desktop PC.

For what it is worth, I own an ASUS ROG STRIX GL702ZC gaming notebook PC. Here are the technical specifications:

AMD Ryzen 7 1700 CPU
32 GB 2,400 MHz DDR4 SO-DIM RAM
AMD Radeon RX 580 4GB GDDR5 GPU
256 GB SATA-III 6 GB/s SSD
Seagate FireCuda 2 TB SSHD
17.3" 1920 X 1080P 60 hZ IPS AMD FreeSync screen

I installed Linux kernel 4.20.0 64 bit, Padoka stable PPA and everything works just great. Sniper: Ghost Warrior 3 Season Pass runs and it plays much smoother than with the stock Linux kernel version.

I hope someone can help me to find a solution for the repeatable freezes and lockups on my AVA Direct gaming desktop PC. Thanks.

---

### Post by oldrocker99 on 2019-01-02
Probably you didn't do it, but check if your mobo is overclocking the CPU.

---

### Post by Welly Wu on 2019-01-02
```
wellywu@AVADirect:~$ Xorg -version
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
wellywu@AVADirect:~$ sudo Xorg -version

X.Org X Server 1.19.6
Release Date: 2017-12-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
Current Operating System: Linux AVADirect 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-4.15.0-43-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=1
Build Date: 25 October 2018  04:11:27PM
xorg-server 2:1.19.6-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.34.0
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
```

This is my current XOrg server version. Let me ask a question: do I need to upgrade my XOrg server version when I installed the stable Padoka PPA and I plan to upgrade my Linux kernel version as well? How do I upgrade my XOrg server version safely for Ubuntu 18.04.1 64 bit LTS?

As far as I can tell, I did not dial in any overclock of my CPU or GPU, but my RAM is running at the rated 2,666.00 MHz speed. Is there anything else that can help me figure out what is going wrong?

Let me ask a new question.

Ubuntu 18.04.2 64 bit LTS should be released on February 7th, 2019. It will have a newer Linux kernel version, XOrg server and MESA stack. Should I do a ppa-purge of the stable Padoka PPA prior to its release and then follow the instructions to install the Hardware Enablement stack in hopes that these newer software package versions may allow me to use Proton and Steam Play to play Sniper: Ghost Warrior 3 Season Pass with improved performance? I would like to stick with the 18.04.x 64 bit LTS release if possible. What do you think?

I found this website, but I would like to know if anyone else has any thoughts about it:

[https://github.com/M-Bab/linux-kernel-amdgpu-binaries](https://github.com/M-Bab/linux-kernel-amdgpu-binaries)

If I follow these instructions, then will it fix my problem?

I solved it.

I removed the stable Padoka PPA using sudo apt install ppa-purge aptitude followed by sudo ppa-purge ppa:paulo-miguel-dias/pkppa and I removed the Vulkan drivers by typing in sudo apt remove libvulkan1 mesa-vulkan-drivers vulkan-utils. I restarted my AVA Direct gaming desktop PC. I used the Ubuntu Kernel Update Utility to install Linux kernel version 4.20.0 64 bit and I added and I installed the semi-official Ubuntu X-Swat Updates PPA by typing in sudo apt-add-repository ppa:ubuntu-x-swat/updates. Finally, I installed the Vulkan drivers by typing in sudo apt install libulkan1 mesa-vulkan-drivers vulkan-utils. I also added amdgpu.dc=1 to my /etc/default/grub and I typed in sudo update-initramfs -u followed by sudo update-grub. I restarted my AVA Direct gaming desktop PC. Everything works now. I can  run Steam just fine and I just played Sniper: Ghost Warrior 3 Season  Pass using Proton and Steam Play. Performance is pretty decent at around  60 FPS with some screen tearing, judder and lag, but it is quite  playable.

---

