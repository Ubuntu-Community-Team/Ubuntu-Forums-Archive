---
title: "No video, even under safe mode"
date: 2007-01-13
forum: Development CD/DVD Image Testing
---

### Post by bronson on 2007-01-13
I tried booting Feisty Knot 2 on my brother's P4-based machine with an nVidia GeForce4 MX 440.  My monitor (Dell 2405FPW) complains about a bad video mode.  This is true both when I boot regular AND when I boot in safe video mode.

I got around this by doing this:

- Hit control-alt-F1
- type "sudo dpkg-reconfigure xserver-xorg"
- Accept all defaults except specify 59-61 for the vsync range.
- Hit control-alt-F7
- Hit control-alt-delete

And now I can see the desktop and continue the install.  I'll continue the report in the next post...  Just wanted to write this down while it's fresh in my head.

So, at the very least, it appears that automatic video mode selection needs a little work...

---

### Post by bronson on 2007-01-13
I saw [https://launchpad.net/ubuntu/+bug/78810](https://launchpad.net/ubuntu/+bug/78810) during install but just like everyone else, switching virtual terminals and back worked around that.

No other problems to report.  Went through the simple test and everything appears in order.

One thing: I don't see "Preferences" or "Aministration" menus anywhere.  Did they move?  I can't find any way to set preferences anymore...

One more thing: I had the Add/Remove application crash on me.

So, a few wrinkles, but things are looking very good so far!

---

### Post by bronson on 2007-01-13
Now I see Gnome Control Center in the System menu.  It wasn't showing up before.  It may be because of an apt-get upgrade, or because of a reboot.  Either way, it's there now and damn does it look good!

So, in summary, I ran into two problems:
- bad video mode during install (both regular and safe mode)
- the crasher in Add/Remove programs

Other than that, things look very good.  Far better than they should at this point.

I'm off to install Beryl...

---

### Post by Henrik on 2007-01-14
Hello, thanks for your report.

Please use the standard testing form in the future so that we know which install method you used which build ID, etc.

Screenshots of the broken menu items and and possibly log files would be great as well (best attached to bug reports and linked to here)

---

### Post by ionredline on 2007-04-20
I'm glad to see I'm not the only one using out dated equipment.  I'm have a similar issue here.  

I ran into boot up problems on my p4 Dell Latitude C840 nvidia ge4 440 card - Ubuntu 6.10.  The problems were with Pro/E trying to call the license server every time I booted my laptop.  Thus, I always had to be connected to the internet, to get a smooth, quick boot.  This became a hassle, so I pulled out my dapper 6.06 disk, wiped out the entire system, loaded 6.06, performed the updates, then updated to 6.10 (Edgy)...  Low and behold, there was the 7.04 update waiting, after I had performed the 6.10 updates.

After the Fiesty Fawn finally completed the setup, I rebooted, and everything worked great!!  I resumed with loading the video driver using: sudo apt-get install nvidia-glx nvidia-kernel-common  and sudo nvidia-xconfig

Then 

sudo gedit /etc/X11/XvMCConfig  with the text "libXvMCNVIDIA_dynamic.so.1"

Upon reboot (first reboot worked wonderful until I performed the above)

Now - all i get is a blank screen - nothing but black! 

any ideas?

---

### Post by K.Mandla on 2007-04-20
It might be an occasional problem between your 440 and the 9631 driver. I have an Inspiron 8000 with a transplanted 440 in it, and I also get a dead LCD with the 9631 driver.

There's a patch for the 8776 driver that makes it work against Feisty's kernel, which means your 440 (or 420 or 460 and certain Ti cards) is still workable without relying on the nv driver. I put together a howto [here]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386").

---

### Post by mjonyh on 2007-10-05
what is the user name and pass word for safe mode in ubuntu?

---

