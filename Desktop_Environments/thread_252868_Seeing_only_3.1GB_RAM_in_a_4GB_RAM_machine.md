---
title: "Seeing only 3.1GB RAM in a 4GB RAM machine"
date: 2006-09-07
forum: Desktop Environments
---

### Post by bartek on 2006-09-07
I have found some posts complaining about similar problems, however none provided a definite answer or a confirmed solution. Here is my story:

Mobo: ASUS P5W DH Deluxe, 4GB RAM, latest BIOS that correctly reports 4096 MB of RAM.

Kernel: 2.6.15-26-686

```
bartek@raptor: free
             total       used       free     shared    buffers     cached
Mem:       3103640    2622832     480808          0     101056    2070456
-/+ buffers/cache:     451320    2652320
Swap:      5960072          0    5960072
```

dmesg output at [http://www.bartek.ws/dmesg.txt](http://www.bartek.ws/dmesg.txt)
kernel config file at  [http://www.bartek.ws/config.txt](http://www.bartek.ws/config.txt)
(those links will be deleted after a while)

While booting up, grub reports 3103640 RAM - I tried booting with mem=4096M argument, but no soup. I'm hesitant to use a 64GB kernel because of the overhead (and it just feels like overkill), but I'm not thrilled about 896 MB of rather expensive RAM not being seen. 

Ideas?
tx!

---

### Post by Toxicity999 on 2006-09-07
Oh adurrr... I misread the title... I had quoted that dmesg reported only 4g usable. Then looked again and realized you mentioned it end all using 3.1 Sorry multi tasking with no caffeine can be a bad hting. I'll look more.

---

### Post by Toxicity999 on 2006-09-07
alright I skimmed the config, I'm no kernel magician but to me that seemed alright. More dmesg bits stuck out at me though:

[17179569.184000] 3200MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.

3200 translates to a natural 3.125 gig. It doesn't really though out any red alert errors thoug hwhich is really weird. It's more silent than you would think.

You may wish to experiment for arguements sake with a Highram environment. If you find the bite of that gets to you more so than that of having some unusable ram so be it.

---

### Post by ceefour on 2008-04-25
My God. This happens to me!

My computer has 4 GB of RAM. It got detected flawlessly in Ubuntu Gutsy Gibbons 7.10 but after I fresh-installed Hardy Heron 8.04 it detects 3.1 GB like you said... TWO YEARS AGO!!! :(

Something isn't right :-((


root@pawn:/etc/bind# free
             total       used       free     shared    buffers     cached
Mem:       3236844    1706384    1530460          0     488492     678120
-/+ buffers/cache:     539772    2697072
Swap:      5108628          0    5108628
root@pawn:/etc/bind# dmesg | grep MEM
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[   16.945601]   MEM window: efb00000-efbfffff
[   16.945613]   MEM window: ef900000-ef9fffff
[   16.945624]   MEM window: ef700000-ef7fffff
[   16.945634]   MEM window: efd00000-efdfffff
root@pawn:/etc/bind# lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)

---

### Post by FredB on 2008-04-25
Just use a 64 bits distro if you want your 4 Gb to be recognized.

---

### Post by sdennie on 2008-04-26
Right.  You will only see your full 4G of RAM if you use a 64bit flavor of Ubuntu or if you use a 32bit kernel with PAE enabled (I believe the 32bit server kernel has PAE enabled but, you may have to compile your own kernel if you choose to stick with 32bit).

---

### Post by FredB on 2008-04-26
The simpler to use is Ubuntu 64 bits if your computer is powered by a 64 bits CPU.

---

### Post by csyeung on 2008-05-01
Hello, I am new to ubuntu. My box has 4GB of ram therefore I go for the 64BIT version of Ubuntu 8.04 Server.

However after installation the system report only 3.1GB of ram.
here is some dump:
root@earth:/etc/apt# uname -r
2.6.24-16-server
root@earth:/etc/apt# uname -a
Linux earth 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2
008 x86_64 GNU/Linux

root@earth:/home/repository# free
             total       used       free     shared    buffers     cached
Mem:       3345032     772704    2572328          0      13644     655164
-/+ buffers/cache:     103896    3241136
Swap:      1044152          0    1044152

root@earth:/etc/apt# dmesg |grep MEM
[   23.826777]   MEM window: fd700000-fd7fffff
[   23.826788]   MEM window: fde00000-fdefffff
[   23.826802]   MEM window: fdc00000-fdcfffff
[   23.826814]   MEM window: fd900000-fd9fffff

it is so weired that I was already using a 64bit distro where I expect it would recognize all of my ram after installation. 
May I ask what should I do to claim back the missing memory?
thank you so much!

---

### Post by jwsohn on 2008-05-17
I am yet to try it, but installing server version of the kernel image might help. It includes compilation options related to memory management. Try installing linux-image-2.6.24-16-server from synaptics.

---

### Post by kerry_s on 2008-05-17
you can recompile your kernel for the large memory support.
in debian they always have the bigmemory kernel available.

---

