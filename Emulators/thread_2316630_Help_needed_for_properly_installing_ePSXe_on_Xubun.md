---
title: "Help needed for properly installing ePSXe on Xubuntu 15.10 amd64"
date: 2016-03-09
forum: Emulators
---

### Post by jrtarsoly on 2016-03-09
Hi guys,

I have an Acer AOD255 netbook running an Intel Atom N450 CPU, with integrated GMA 3150 graphics. I've installed a fresh copy of Xubuntu 15.10 AMD64 on this thing and made all the updates to it using the "sudo apt-get update, upgrade & dist-upgrade" commands.

I've then proceeded to download the linux 1.9.25 version of the ePSXe emulator and extracted the archive. Initially, when I tried to open the "epsxe" program, it did nothing; running the program through the terminal (using ./epsxe) told me "command not found", or something similarly sounding. From this point I went on and searched the internet on how to properly install ePSXe, and all I found is that I needed to install a bunch of repositories in order for this program to work under Linux.

And so I did, I have installed these repositories : libgtk2.0-0:i386, libsdl-image1.2:i386, libsdl-ttf2.0-0:i386. I've also made some modifications to "/etc/apt/sources.list.d", by adding "echo "deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) raring main restricted universe multiverse" >ia32-libs-raring.list" line to the file.
I then went on, following the tutorial on the internet, and installed the following repositories : ia32-libs, lib32z1 and libx11-6:i386. After all this, I also ran the "apt-get update" command once again.

From this point on, I can open ePSXe, it no longer tells me that whole "command not found" nonsence, and when running ePSXe from the terminal, using ./epsxe, before opening the program, the terminal prompts me a lot of messages, as following :

```
 * Running ePSXe emulator version 1.9.26. 

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(epsxe:1673): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


```

Now, the problem is, although the program is opening, as soon as I try to edit the video, or audio settings - it closes. With the BIOS loaded, if I try to run a Bios test - it closes. I should mention that I did NOT achieved installed the ia32-libs repository. When I try to "apt-get install ia32-libs", it tells me something about broken packages, and it tells me that this repository depends on the "ia32-libs-multiarch" repository. I then proceed to "apt-get install ia32-libs-multiarch". It tells me once again something about broken packages ("Unable to correct problems, you have held broken packages"), and that "ia32-libs-multiarch" depends on "bluez-alsa:i386". Again, "sudo apt-get install bluez-alsa:i386" = broken packages, it needs "bluez:i386".

The "bluez:i386" I did manage to install using apt-get install, no problem. But when trying to install "bluez-alsa:i386" - it still tells me that this repository depends on "bluez:i386" - I'm basically stuck in some sort of perpetual repository loop.

So, how do I get around all of this and succesfully install ePSXe on my netbook running Xubuntu 15.10_AMD64 ?

If there's any other info I should share in order to sort this out, just ask me and I'll gladly offer.

Thanks guys !!

---

