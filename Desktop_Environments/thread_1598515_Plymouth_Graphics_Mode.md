---
title: "Plymouth Graphics Mode"
date: 2010-10-16
forum: Desktop Environments
---

### Post by LinuxPhreak on 2010-10-16
I installed Ubuntu 10.10 Alternate Command Line mode. Then I added gnome core and and added the graphical plymouth theme. However I can't seem to get the graphical plymouth theme to work. It still uses the text mode. How can I change it to boot with the graphical mode?

---

### Post by inobe on 2010-10-16
make sure you have plymouth themes installed, search for them in synaptic, install the ones you like.

close synaptic and run

```
sudo update-alternatives --config default.plymouth
```

a list will appear, select your theme then run

```
sudo update-initramfs -u
```

now restart to see if the theme is working.

---

### Post by LinuxPhreak on 2010-10-17
> **inobe said:**
> make sure you have plymouth themes installed, search for them in synaptic, install the ones you like.

close synaptic and run

```
sudo update-alternatives --config default.plymouth
```a list will appear, select your theme then run

```
sudo update-initramfs -u
```now restart to see if the theme is working.

I've already have done that. I'm on my friends computer which is Windows right now. But on my Ubuntu machine I get something that says something along the lines of it can't display anything because their is only one theme. This is true. But it doesn't show up. Only the text mode theme shows up. When I get back to my house I will post exact details.

---

### Post by LinuxPhreak on 2010-10-17
When I type 

```
sudo update-alternatives --config default.plymouth
```

I get the following message.

```
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.

```

However the plymouth doesn't show up. It only shows the plymouth text mode instead of the graphical mode.

---

### Post by lridium on 2010-10-17
> **LinuxPhreak said:**
> However the plymouth doesn't show up. It only shows the plymouth text mode instead of the graphical mode.

I just wanted to +1 this.  I have multiple themes installed however the graphical is being ignored (despite the FRAMEBUFFER=y switch) and only the text is displayed.

---

### Post by inobe on 2010-10-17
okay this may be the result of 

```
High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```

in the kubuntu tutorial in my sig it states you may even see text replacing a splash if you have a proprietary driver installed.

however if you don't have nvidia's driver and at least nouveau's i suspect you will see text.

---

### Post by lridium on 2010-10-17
> **inobe said:**
> *SNIP*

```

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```


I've followed Alberto's text as I found it on Pastebin (which you have above, too) including the video switch and the framebuffer line.  This hasn't changed my results.  I'm running the nvidia binary, just for the record.

It's also worth mentioning that the start of this coincided with my switch to 10.10 (correlation is not causality, but just something to keep in mind).

---

### Post by garvinrick4 on 2010-10-17
Are the graphic drivers hitting before the mountall package hits. This works for me on all plymouth versions of Ubuntu
540801 launchpad:
```
sudo -i
``````
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

---

### Post by lridium on 2010-10-17
I've got that there and the images are updated, but I don't know when the driver is loading (that's probably the real question on this one for my personal case).

---

### Post by inobe on 2010-10-17
i have the nvidia proprietary driver installed and i get text too.

my problem is i need to deactivate nvidia's drive and use nouveau's to even see a splash, i think this is key.

[click to watch my splash screen]("http://www.itsyourpc.org/duane/files/splash.swf")

---

### Post by lridium on 2010-10-18
> **inobe said:**
> i have the nvidia proprietary driver installed and i get text too.

my problem is i need to deactivate nvidia's drive and use nouveau's to even see a splash, i think this is key.

[click to watch my splash screen]("http://www.itsyourpc.org/duane/files/splash.swf")

And I had a feeling that was going to be necessary down the road, but some of the reading made it sound like it may be possible to get a splash up and running with "nvidia".  I had run nouveau previously under Lucid and received the splash so I suppose this is just going to be a drawback to the nvidia driver unless the two can handoff somehow (which would surprise me).

---

### Post by inobe on 2010-10-18
i certainly wouldn't sacrifice my 3-d desktop for a colorful splash screen :lol:

---

### Post by LinuxPhreak on 2010-10-19
You guys are saying it is a propriotory driver. Does Ubuntu Ship with such drivers. Because I didn't install one and to be honest my Jockey-GTK doesn't show ones that are needed.

---

### Post by lridium on 2010-10-19
> **inobe said:**
> i certainly wouldn't sacrifice my 3-d desktop for a colorful splash screen :lol:

lol, amen to that one.  Though I now have the high-res splash running on shutdown, just not on boot.  I'm not done yet, but I'm sure not going to break anything just for the sake of a warm-fuzzy (which lasts under 10 seconds right now anyway).  I'll update if I find anything of value.

---

### Post by lridium on 2010-10-19
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

That got it working for me.  It's not crazy fast in terms of appearance on boot, but I'll worry about that later.  At least this gets me a working plymouth boot splash.

---

