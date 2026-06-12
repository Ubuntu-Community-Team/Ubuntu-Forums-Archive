---
title: "Want To Try Openbox..."
date: 2009-07-17
forum: Desktop Environments
---

### Post by izizzle on 2009-07-17
I want to try out Openbox, but I had a few questions. I know that it will be a little harder to set up (than KDE), but in what way? Also, I read somewhere that my external media devices (USB, CDROM...) would not be automounted and that I would have to mount them myself? 

Can you guys recommend some good distros that use Openbox?

Thanks. I'll keep asking questions here as I go.

---

### Post by b.a.w on 2009-07-17
crunchbang is the big openbox distro right now. If you just want to try it out, you can install openbox from Ubuntu. It will show up as a session in your login manager. The Arch Linux Wiki has some very good documentation on configuration at [http://wiki.archlinux.org/index.php/Openbox](http://wiki.archlinux.org/index.php/Openbox). Most if not all the packages mentioned should be avaliable on Ubuntu also. Be ready to configure, but you can make a very nice system with it.

---

### Post by XubuRoxMySox on 2009-07-17
You said you wanted to *avoid* a hassle with setting it up? Then *don't* even *attempt* Arch. It's not difficult as long as you can read and follow directions precisely, but if you want an awesome Openbox distro that is ready right "out of the box," you definitely want [Crunchbang]("http://crunchbanglinux.org")!

It's Ubuntu-based (therefore much more "hardware friendly" than anything else out there (including the codecs preinstalled), so it should be somewhat familiar (Synaptic etc, plus the awesome depth of Debian and the vast repositories and support community of Ubuntu). Supercharged, lightweight, Openbox-ready. Install, right-click on the desktop, and off you go!

-Robin

---

### Post by ~sHyLoCk~ on 2009-07-17
Arch Linux is definitely a good distro to try with any WM/DE. I personally use openbox with Arch. As mentioned above as long as you read the wiki, everything will be almost easy to setup.

---

### Post by b.a.w on 2009-07-17
I was offering the Arch wiki page as a guide to openbox. Not suggesting you should install Arch to use it. Arch users are very knowledgeable and you can learn alot from their wiki. I also suggest crunchbang since it has a very good default configuration. You will probably want to change it eventaully though.

To answer your automount question, if you read the wiki link you can see that running a file manager in daemon mode will cover your automount issues. I suggest thunar because it is lighter and doesn't take over the desktop like nautilus does.

---

### Post by Wiebelhaus on 2009-07-17
Install in a Virtual box , So there's no commitment until you feel comfortable enough with the installation and configuration process.

---

### Post by izizzle on 2009-07-18
Thanks guys. I think I'll try installing arch in Virtual Box.

---

### Post by izizzle on 2009-07-18
Alright I'm up to the arch install step where I configure my internet and I am totally lost. My IP is 192.168.1.2  the SSID is ZRES  and the password is 10c21d2669 I am on a wireless network. Now how do I configure the internet?

Please help!

---

### Post by snowpine on 2009-07-18
> **izizzle said:**
> Alright I'm up to the arch install step where I configure my internet and I am totally lost. My IP is 192.168.1.2  the SSID is ZRES  and the password is 10c21d2669 I am on a wireless network. Now how do I configure the internet?

Please help!

Hi Izizzle, a few things:

1. if you are running Arch in virtualbox, you don't need to configure wireless... it uses the host computer's networking... should just show up in arch as a wired connection
2. I highly recommend this document: wiki.archlinux.org/index.php/Beginners_Guide
3. there are some arch users on these forums, but mostly they are for ubuntu. arch has its own forum. :)

---

### Post by izizzle on 2009-07-18
I set eth0="dhcp" for the network, I hope it works.

Well, I installed it and I rebooted and I'm in. Now what? I've never used pacman before so I don't know the commands. I want to install Openbox. Can someone help me out?

---

### Post by snowpine on 2009-07-18
> **izizzle said:**
> I set eth0="dhcp" for the network, I hope it works.

Well, I installed it and I rebooted and I'm in. Now what? I've never used pacman before so I don't know the commands. I want to install Openbox. Can someone help me out?

READ THIS!!!

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by ~sHyLoCk~ on 2009-07-18
Don't mean to be rude, but when it comes to arch, you do have to read the wiki. All of us did. :P

---

### Post by izizzle on 2009-07-18
Ah thanks for the link. I was actually using a Youtube video as a guide to installing, the Wiki is very helpful. The internet works and I'm upgrading the system right now, but I'm only getting about 100 kbps when I should be getting around 315 kbps. I pinged google and it said that I had 33% packet loss.

I even took out all the mirrors that were not close to me, all I have is USA and Canada mirrors.

---

### Post by ~sHyLoCk~ on 2009-07-18
> **izizzle said:**
> Ah thanks for the link. I was actually using a Youtube video as a guide to installing, the Wiki is very helpful. The internet works and I'm upgrading the system right now, but I'm only getting about 100 kbps when I should be getting around 315 kbps. I pinged google and it said that I had 33% packet loss.

I even took out all the mirrors that were not close to me, all I have is USA and Canada mirrors.

I don't think that's related to arch though. Maybe just a temporary ISP issue?

---

### Post by izizzle on 2009-07-18
Well, it doesn't really matter anymore. I was able to install arch and do all the configuration (kinda), but I just couldn't get alsa installed and working properly and it just went downhill from there (installation of xord, openbox...). Like I said before, I WILL be an arch user SOON, but not today. I am currently installing Ubuntu Minimal and plan on building my system from that. I guess it's kinda like arch...

---

