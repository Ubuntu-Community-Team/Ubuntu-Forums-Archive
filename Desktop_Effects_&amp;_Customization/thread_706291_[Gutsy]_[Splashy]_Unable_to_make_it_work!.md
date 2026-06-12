---
title: "[Gutsy] [Splashy] Unable to make it work!"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by microfi on 2008-02-24
Hello! :)
I've been trying to customize my bootup splash using Splashy, but I just can't make it work properly. I'm using Ubuntu Gutsy Gibbon.
Some details are provided below:
- I've fixed the **vesafb** issue (as I can successfully enter TTY by pressing Ctrl+Alt+F1)
- I Installed splashy through Synaptic, from the **archive,ubuntu.com/universe** repository.
- I've tried **vga=791**, **vga=792** and even hexadecimal values in **/boot/grub/menu.lst** (I was able to see the bootup texts smaller, due to the resolution change)
- I completely removed **usplash** from Synaptic, deleted all the folders naming **usplash** in /etc/
- I've already installed **libdfb++-0.9-25** and **libdirectfb-0.9-25**
- I can successfully see the penguin by typing **splashy test** in a Root Terminal, or **sudo splashy test** in a TTY after pressing Ctrl+Alt+F1,
- When I restart my computer, instead of seeing the image, i get [COLOR="Red"]*System is restarting, please wait...*[/COLOR] in red, as if I was in verbose mode.
- Right after choosing **ubuntu** in GRUB, I get a message like this **Re(generating) splash steps:sed: can't read /etc/inittab: no such file or directory**, and the system starts in verbose mode

I'd really appreciate some help :)
PS: if there's another way to customize bootup images, I'd be interested in knowing!

Thanks, Filipe

---

### Post by microfi on 2008-02-24
[I was to report an error on the post above, but I edited it - please remove this]

---

### Post by joeamined on 2008-03-03
Hi man, remove splashy packages you installed from the official repositories and download and install libsplashy1_0.3.8-2_i386.deb THEN splashy_0.3.8-2_i386.deb from here [http://splashy.alioth.debian.org/ubuntu/](http://splashy.alioth.debian.org/ubuntu/). Then, just add splash vga=791 in your menu.lst file. That's all you have to do to get it work (no vesafb or anything..)

---

### Post by psm22 on 2008-03-10
Hi,
I was having issues with splashy, but that last suggestion solved them all (thanks!) 
All? no: one issue still remains: there are little lines like flashing cursors along the top of the screen (see attached screenshot). Perhaps it is something to do with  /boot/grub/menu.lst? (I've got "splash vga=791" in the line where the kernel is specified, as suggested).

Thanks for any suggestions
Peter

---

