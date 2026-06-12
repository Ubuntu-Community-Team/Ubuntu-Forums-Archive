---
title: "How works gnome on a very old pc?"
date: 2012-07-01
forum: Desktop Environments
---

### Post by ayozito on 2012-07-01
Hi!

I have a laptop Acer Aspire 1640. Today I installed on it a Lubuntu but I think I don't like it. I installed it because people say it is lighter than other distributions.

I'm wondering, if I install Ubuntu using Gnome, will have a great perfomance? Actually with Lubuntu it's fine.

---

### Post by raja.genupula on 2012-07-01
whats the configuration of your Laptop ? 

Actually Lubuntu is good for Less memory laptops or PC's for better performance .

---

### Post by Rodney9 on 2012-07-01
Try [Xubuntu ]("http://xubuntu.org/")

> Xubuntu is an elegant and easy-to-use operating system. Xubuntu comes with Xfce, which is a stable, light and configurable desktop environment.

Xubuntu is perfect for those who want the most out of their desktops, laptops and netbooks with a modern look and enough features for efficient, daily usage. It works well on older hardware too.

Rodney

---

### Post by claracc on 2012-07-02
You have to give us the pc specifications in order to get advice.

My experience is, with a ten years old pentium III laptop, 512 MB RAM, 64 MB for the sis 630/730 graphics card, 20 GB HDD, I installed ubuntu 10.04  with gnome desktop and the pc worked but it was a little slow, and spent very much CPU. The fan were working almost all the time.

The worst was to watch flash videos, but I have to blame adobe flash plugin for it.

So I installed lubuntu 11.04 and the laptop was very much responsive, things were better with lubuntu 11.10 and now I have lubuntu 12.04. This is a very light OS and allows to use this ancient laptop to surf the web, playing music or doing office tasks. 

The CPU and RAM consumption is reasonable with lubuntu and the laptop remains usable.

---

### Post by ayozito on 2012-07-02
[http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire1640/Aspire1640sp2.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire1640/Aspire1640sp2.shtml)

---

### Post by sudodus on 2012-07-02
> **ayozito said:**
> [http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire1640/Aspire1640sp2.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire1640/Aspire1640sp2.shtml)
OK,
CPU: Pentium M
RAM: ?

If 512 MB RAM, I'd definitely recommend Lubuntu, if more, Xubuntu will also perform well. I mean, you need not only run the operating system and the desktop environment, there should also be space enough in the RAM for application programs, for example the web browser.

Please check the RAM: Post the output of the following command
```
sudo lshw -class memory
```

Edit: Ubuntu with Gnome 3 and Unity or gnome-fallback etc. will probably be too slow. And if you try Ubuntu 12.04, it needs pae, which is probably lacking in your CPU. But Lubuntu 12.04 and Xubuntu 12.04 are distributed with non-pae kernels. If you are not happy with Lubuntu or Xubuntu, feel free to try some other distro, for example Knoppix or Linux Mint.

---

### Post by kansasnoob on 2012-07-02
> **ayozito said:**
> [http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire1640/Aspire1640sp2.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire1640/Aspire1640sp2.shtml)

Those specs are rather non-specific so it would be helpful to see the full output of these commands:

```
cat /proc/cpuinfo
```

```
free -m
```

I'm particularly curious if that Pentium M CPU has the pae flag :)

---

### Post by ayozito on 2012-07-02
It runs at 2 GHz and has the PAE flag. 2MB L2 Cache, 1 GB RAM.

Actually I haven't nothing against Lubuntu, just that I'm more used to Gnome than Lxde. For example in pcman I miss more shortcuts in the place zone, such as Music, Pictures, Video... Not only my home directory. I tried install Nautilus but it was very bad.

---

### Post by Lyfang on 2012-07-02
Try to get used to Lubuntu. See also Debian 6 Squeeze "stable" with GNOME 2.30, it should work better on older hardware rather than GNOME 3.

---

### Post by sudodus on 2012-07-02
> **ayozito said:**
> It runs at 2 GHz and has the PAE flag. 2MB L2 Cache, 1 GB RAM.

Actually I haven't nothing against Lubuntu, just that I'm more used to Gnome than Lxde. For example in pcman I miss more shortcuts in the place zone, such as Music, Pictures, Video... Not only my home directory. I tried install Nautilus but it was very bad.
Since your cpu has pae capability, you can choose without restrictions among the Ubuntu flavours :-)

But still, I think Lubuntu will work well. You can also install ***Thunar*** (a file browser with specs between Pcmanfm and Nautilus.

With 1 GB RAM it's also worth trying Xubuntu with a more complete and nice-looking desktop environment.

---

### Post by MG&amp;TL on 2012-07-02
> **ayozito said:**
> It runs at 2 GHz and has the PAE flag. 2MB L2 Cache, 1 GB RAM.

Actually I haven't nothing against Lubuntu, just that I'm more used to Gnome than Lxde. For example in pcman I miss more shortcuts in the place zone, such as Music, Pictures, Video... Not only my home directory. I tried install Nautilus but it was very bad.

You can add those. I believe it's under the bookmarks menu in PCManFM (sorry, can't test, not running Lubuntu at present).

---

### Post by sudodus on 2012-07-02
[QUOTE=MG&TL12070271]You can add those. I believe it's under the bookmarks menu in PCManFM (sorry, can't test, not running Lubuntu at present).[/QUOTE]
Yes, I can confirm: When you have selected a directory or a network address, Click on 'Bookmarks' and select 'Add bookmark' to make a bookmark on the left panel. Later on you can edit the bookmark, for example rename it.

---

