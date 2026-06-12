---
title: "ATI binary X.org driver problem.(ubuntu 9.04)"
date: 2009-04-23
forum: General Help
---

### Post by Demonizer on 2009-04-23
first I would like to thank the developers && the staff for the release && the community. 

Hi, I am having a problem with ATI binary X.org driver. after the installation of Ubuntu 
I installed the driver and as soon as I restarted my computer Ubuntu loaded with totally screwed up display (Horizontal orange lines,half black with some weird coloured here and there...)
impossible to do anything. I had no choice but to reinstall Ubuntu. now I'm asking you guys to help me out.

here are some of my specs:
cpu:
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits

          1gb RAM
video card:
             description: VGA compatible controller
             product: RV380 0x3e50 [Radeon X600]
             vendor: ATI Technologies Inc

Thanks ahead of time.:)

---

### Post by EmgpJt on 2009-05-13
> **Demonizer said:**
> first I would like to thank the developers && the staff for the release && the community. 

Hi, I am having a problem with ATI binary X.org driver. after the installation of Ubuntu 
I installed the driver and as soon as I restarted my computer Ubuntu loaded with totally screwed up display (Horizontal orange lines,half black with some weird coloured here and there...)
impossible to do anything. I had no choice but to reinstall Ubuntu. now I'm asking you guys to help me out.

here are some of my specs:
cpu:
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits

          1gb RAM
video card:
             description: VGA compatible controller
             product: RV380 0x3e50 [Radeon X600]
             vendor: ATI Technologies Inc

Thanks ahead of time.:)

I am also having this problem, i installed driver then after a reboot i got the same screen and i had to re-install ubuntu as the only option.

---

### Post by Dimarchi on 2009-05-14
Did you do sudo aticonfig --initial -f right after you had installed the driver?

---

### Post by rizman on 2009-05-14
Did you install the proprietary drivers from ATI (fglrx)? If so, I'm afraid your graphics card (Radeon X600) is not supported. ATI recently declared a lot of cards (including mine, a Radeon Mobility X700) as legacy cards. See [here.]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86")

There are a lot of threads in the ubuntuforums about this, but here's a quick rundown of the problem.

Ubuntu 9.04 uses the version 1.6 of the X server.
X 1.6 only works with catalyst 9.4 drivers.
Catalyst 9.4 drivers do not support your card any longer.

So either you keep using the open source ati drivers. Those work really well for me as long as I don't do any fancy 3D stuff, or revert back to Ubuntu 8.10/8.04.

---

### Post by EmgpJt on 2009-05-15
> **rizman said:**
> Did you install the proprietary drivers from ATI (fglrx)? If so, I'm afraid your graphics card (Radeon X600) is not supported. ATI recently declared a lot of cards (including mine, a Radeon Mobility X700) as legacy cards. See [here.]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86")

There are a lot of threads in the ubuntuforums about this, but here's a quick rundown of the problem.

Ubuntu 9.04 uses the version 1.6 of the X server.
X 1.6 only works with catalyst 9.4 drivers.
Catalyst 9.4 drivers do not support your card any longer.

So either you keep using the open source ati drivers. Those work really well for me as long as I don't do any fancy 3D stuff, or revert back to Ubuntu 8.10/8.04.

Well Compiz works great its just that I cant run 3D games. But I all Linux users had to loose at least one fav game to run on their distro. But for me I can play Nexuiz, Tuxracer, Sauerbraten and Tremulous. I have been planning on dual booting with xp for some time now. I have an extra CD of xp laying around in my house. Just because i cant run 3D games, it doesn't mean I will leave Ubuntu 9.04 behind.

---

### Post by rizman on 2009-05-15
> **EmgpJt said:**
> Well Compiz works great its just that I cant run 3D games. But I all Linux users had to loose at least one fav game to run on their distro. But for me I can play Nexuiz, Tuxracer, Sauerbraten and Tremulous. I have been planning on dual booting with xp for some time now. I have an extra CD of xp laying around in my house. Just because i cant run 3D games, it doesn't mean I will leave Ubuntu 9.04 behind.

Then you must be using the open-source drivers already. Because when I tried to install the catalyst drivers from ATI, I had the same issue as the OP: garbage screen when X starts. You said in your first post that you had the same issue. So that is definitely because of the proprietary drivers.

Now with the open-source drivers, Compiz works great, I tried Nexuiz and it runs OK, just like you reported. So you must be using those too.
Anyway, I'm playing mostly on my Xbox 360, so games don't matter that much to me on my Laptop and I'm going to keep Ubuntu 9.04. Just yesterday, I reformatted my last NTFS partition from XP to ext4 and moved /home to there. So now I have completely moved over to Linux. w00t :-)

---

### Post by Demonizer on 2009-11-19
Well.. thank you all but this topic is irrelevant now cause I bought a new card(nvidia) so everything is working fine now.

---

