---
title: "Has anyone else had KDE go weird on them in the last few days?"
date: 2020-05-11
forum: Desktop Environments
---

### Post by Scary Rob on 2020-05-11
I've been getting some odd behaviour recently, and I'm not sure what's causing it. I'm running 18.04.

Since 8th or 9th May, I've stopped getting a pop-up notification about my audio devices when I connect my bluetooth speaker.

On 10th May, a maximised Chrome window wouldn't respond to the unmaximise button.

Today (11th May) I booted up and the various system notification popups I get as my wifi connects wouldn't close. This preceded a complete crash of my desktop - everything stopped responding a few seconds later. I rebooted by system request. Now I've got screen tearing - a common problem with the NVidia GTX 1050 that I thought I'd fixed.

And I've just tried to get a hardware list in Yakuake with "lshw", only to have it briefly flash the password request before going blank but for the typing carrot square (not even a command prompt). Even thought the input square is there, it's still unresponsive.

Has there been a duff update, or is this just me?

Latest apt log for what it's worth:

```

Start-Date: 2020-05-01  19:39:17
Commandline: apt full-upgrade
Requested-By: rob (1000)
Upgrade: libnvidia-compute-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-compute-390:i386 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-encode-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-encode-390:i386 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), nvidia-kernel-common-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), xserver-xorg-video-nvidia-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-gl-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-gl-390:i386 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-fbc1-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-fbc1-390:i386 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-decode-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-decode-390:i386 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-cfg1-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), nvidia-utils-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), nvidia-dkms-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libxnvctrl0:amd64 (390.77-0ubuntu0.18.04.1, 440.44-0ubuntu0.18.04.1), nvidia-compute-utils-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), chromium-codecs-ffmpeg-extra:amd64 (80.0.3987.163-0ubuntu0.18.04.1, 81.0.4044.122-0ubuntu0.18.04.1), libnvidia-ifr1-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-ifr1-390:i386 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), nvidia-driver-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), libnvidia-common-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), nvidia-kernel-source-390:amd64 (390.116-0ubuntu0.18.04.3, 390.132-0ubuntu0.18.04.1), nvidia-settings:amd64 (390.77-0ubuntu0.18.04.1, 440.44-0ubuntu0.18.04.1)
End-Date: 2020-05-01  19:41:01

Start-Date: 2020-05-05  08:35:04
Commandline: apt full-upgrade
Requested-By: rob (1000)
Upgrade: mysql-client-core-5.7:amd64 (5.7.29-0ubuntu0.18.04.1, 5.7.30-0ubuntu0.18.04.1), libmysqlclient20:amd64 (5.7.29-0ubuntu0.18.04.1, 5.7.30-0ubuntu0.18.04.1), mysql-server-core-5.7:amd64 (5.7.29-0ubuntu0.18.04.1, 5.7.30-0ubuntu0.18.04.1)
End-Date: 2020-05-05  08:35:14

Start-Date: 2020-05-06  05:02:05
Commandline: apt full-upgrade
Requested-By: rob (1000)
Upgrade: google-chrome-stable:amd64 (81.0.4044.129-1, 81.0.4044.138-1)
End-Date: 2020-05-06  05:02:15

Start-Date: 2020-05-07  10:28:56
Commandline: apt full-upgrade
Requested-By: rob (1000)
Upgrade: libldap-2.4-2:amd64 (2.4.45+dfsg-1ubuntu1.4, 2.4.45+dfsg-1ubuntu1.5), firefox-locale-en:amd64 (75.0+build3-0ubuntu0.18.04.1, 76.0+build2-0ubuntu0.18.04.1), libldap-common:amd64 (2.4.45+dfsg-1ubuntu1.4, 2.4.45+dfsg-1ubuntu1.5), firefox:amd64 (75.0+build3-0ubuntu0.18.04.1, 76.0+build2-0ubuntu0.18.04.1), linux-firmware:amd64 (1.173.17, 1.173.18)
End-Date: 2020-05-07  10:29:59

```

---

### Post by CatKiller on 2020-05-11
Still working fine for me, with none of the symptoms you've described. I use the 440 driver, though.

---

### Post by Scary Rob on 2020-05-11
I wonder if it might be the driver, then. What I found when I went into the Nvidia Xserver settings today was that my xorg.conf file had disappeared. I know it existed once because it was how I fixed the screen tearing when I installed my current setup in 2018.

Before that I had a brief flirtation using Debian with XFCE. I gave up because literally every time the Nvidia driver updated it would break a load of dependencies, at one point leaving me having to reinstall XFCE manually. The only reason I don't use Nouveau instead is because the graphics card refused to wake up from sleep on that driver, and I bought my current computer while the old one was still running fine because I was having a similar problem with its A Series motherboard.

Are graphics driver updates security critical? Is it possible to blacklist them?

---

### Post by CatKiller on 2020-05-11
> **Scary Rob said:**
> Are graphics driver updates security critical? Is it possible to blacklist them?

In principle they could be, but in practice I think it's largely bug fixes that get backported. They're just a package, so you can do your normal package management things with them. 

Until 19.10 the driver branch that you got was whatever was current when that version of Ubuntu was released: to get newer you needed to use the graphics drivers PPA (which is how I'm on the 440 branch). For 19.10 and 20.04 those drivers can go through the Stable Release Update process that browsers go through, so newer branches will become available from the standard repositories.

Updating either the kernel or the driver independently is mostly painless with DKMS. I guess you weren't using that when you were flirting with Debian. 

Having xorg.conf isn't necessary these days, so it's fine not to have one. You can put whichever options you need as snippets in xorg.conf.d rather than having to specify the full monty.

If your proprietary driver isn't working that could explain at least some of your symptoms. It's a place to start.

---

### Post by SeijiSensei on 2020-05-11
I've used Kubuntu 18.04, 19.04, 19.10 and now 20.04.  They've all been pretty smooth out-of-the-box.  I recommend taking 20.04 out for a test drive. You can choose the Try Ubuntu option if you boot it from a disc or USB drive.

[http://cdimage.ubuntu.com/kubuntu/releases/20.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/20.04/release/)

---

### Post by Scary Rob on 2020-05-11
> **CatKiller said:**
> Having xorg.conf isn't necessary these days, so it's fine not to have one. 

Oh, I believe you. My point was that I'd fixed the screen tearing by creating xorg.conf 18 months ago and something's gone and deleted that file since. I've used that filename to save the settings I fixed in the Nvidia GUI today and it seems to be working okay.

Thanks for the advice; I might try adding the graphics driver PPA. However, if the issue is that the 390 drivers are somehow deleting things when they update, the damage is already done. If Kubuntu 20.04.1 is out by the time I do my next file backup, I might just upgrade.

---

