---
title: "Monitor &quot;out of range&quot; after primary installation, VGA connection"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Xaeos on 2005-06-24
Hello everyone, so far I've had the easiest and most painless linux install ever - I am a true newbie and Gentoo has effectively taught me I'm not ready for primetime so I've come to Kubuntu. 

Anyhow, when Kubunto tries to start X (I think?) It basically frells my monitor. I am using a Viewsonic VX2000 using the Analog imput, and it tells me it is out of range.  Is there some way during bootup I can specify the resolution to use?  This has never happened to me using a DVI setup, as DVI operates at 60hz by default.  My native resolution is 1600x1200, 60hz.  A little help would be appreciated!

---

### Post by skoal on 2005-06-24
In your '/etc/X11/xorg.conf' file, under Section "Device" add teh following:

Option "ConnectedMonitor" "DFP"

and see if that don't fix it.  Using an analog connection on a Flat LCD?  Maybe you need to add your Monitor specs in there too (under Section "Monitor"):

HorizSync        30-82
VertRefresh     50-75

\\//_

---

### Post by Xaeos on 2005-06-24
This occurs right during bootup after Ubuntu runs a bunch of self checks, so I can't seemingly edit anything (no cmd prompt). I can hit esc to load GRUB's menu though. I am using an analog connection on a flat panel because the windows box I'm typing on is using the DVI one and I've had nothing but problems with digital KVM's. 

Thanks for your answers.

---

### Post by skoal on 2005-06-24
Eventually after Ubuntu runs those "self checks" (<- do you mean init scripts?), GDM will try to start the X server, and after a while (even though the screen may be black), it should take you to a command prompt.  However, it may be asking you with a prompt to "view the contents of log file" and you just can't see it.  That X server is tricky, ain't it?  If that may be the case, just hit CTRL-ALT-F1 to get to a console tty login.

Can you login that way?

And if that fails, do you have another partition running Linux that you can safely boot into and then mount the Ubuntu root partition and make those changes from there?

\\//_

---

### Post by Firetech on 2005-06-24
[QUOTE=Xaeos]This occurs right during bootup after Ubuntu runs a bunch of self checks, so I can't seemingly edit anything (no cmd prompt). I can hit esc to load GRUB's menu though. I am using an analog connection on a flat panel because the windows box I'm typing on is using the DVI one and I've had nothing but problems with digital KVM's. 

Thanks for your answers.[/QUOTE]
 The recovery mode (available in GRUB) won't start X, so from there you should be able work on the configurations. nano is a great and easy to use console editor. The recovery mode will login as root, so be careful with what you do...

---

