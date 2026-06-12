---
title: "creating a distro"
date: 2008-12-02
forum: General Help
---

### Post by callum97 on 2008-12-02
:guitar:
say...
would anyone know how to create your own linux distro?

---

### Post by Izek on 2008-12-02
[http://ubuntuforums.org/showthread.php?t=852868](http://ubuntuforums.org/showthread.php?t=852868)

---

### Post by loomsen on 2008-12-02
Couple of ways, however, I'd prlly always prefer getting a basic system, where common things most likely are safe. 

So, I think you're more up to creating a custom GUI rather than a whole distro right?

That's not too hard actually, get a base system, for instance ubuntu-server or rootstrap a debian system or so. The rest basically happens now, when the display manager is to be chosen. For instance xdm/ldm/sdm whatever. This will give you a kick off. Then on it goes, I'd prlly configure my nvidia-settings to be load directly after the display manager started. For a basic desktop you probably can imagine what you need, like an application/script to draw your background window, sth menu-aware, a terminal and so on. After chosing the display manager everything else will ask for attention simply because of it's elementary means to a GUId session.

But as I said, if you wanna "build" (chose and install apps yourself more likely, rather than starting off with like 1.5K pkges or so installed) your custom sys, give [www.instalinux.com](www.instalinux.com) a try.
Don't chose any package when asked (ubuntu, kubuntu ...). Simply go on, your generated iso will be about 10MB in size and basically give you a netinstallation CD/USB/image. Very handy it is. Then, after install, think good which metapackages to pull in. I usually choose gnome-core, ubuntu-minimal or ubuntu-standard and sometimes gnome-common. This is enough to get started for my needs.


*edit*
Forgot to mention unetbootin. Actually advanced to my favorite app. You can create a whole lot of different (Live)ISO/install images of nearly every linux out there. 
Really worth a shot.

---

### Post by Izek on 2008-12-02
instalinux says:

"Distro, Rev, and Arch is a Required field!
Go back and set it!"

So how can I NOT choose "Ubuntu, etc."?

---

### Post by loomsen on 2008-12-02
Sure you can, and you have to chose your base system. I was up to the metapackages to pull in any desktop environment, libe gnome-desktop-environment. This metapackage will bloat itself up as much as possible, while gnome-core will still provide everything you basically need for a gnome-session, but no apps installed. For instance, I didn't have any, not a single application installed in Applications-->Internet. No Firefox, no evolution, just no such things I usually prefer choosing myself. And thus, no dependency problems when uninstalling.

Usually I spent about 3-4 hrs removing pkges I didn't want after a common ubuntu installation.

Using unetbootin or instalinux.com it feels like the other way round, which I not only prefer, but enjoy. Handling apps switched from removing pkges I don't want to choosing pkges I DO want. And, hence I decide which pkges to grab rather than remove, usability incresed by loads imho, cause now I know which pkges ARE installed rather than WERE installed.

Here's a shot of unetbootin which offers about 25 different options, every option offering common versions. 
[[img]http://www.ubuntu-pics.de/thumb/6697/screenshot_29_875W77.png[/img]](http://www.ubuntu-pics.de/bild/6697/screenshot_29_875W77.png)
For instance if you choose ubuntu, you may choose a daily_amd64_live CD of jaunty if you feel like.

[[img]http://www.ubuntu-pics.de/thumb/6698/screenshot_31_9HC1MP.png[/img]](http://www.ubuntu-pics.de/bild/6698/screenshot_31_9HC1MP.png)

And the biggest plus, imho, it takes about 2 mins if you chose a netinstall option from launching unetbootin till being prompted to reboot. Well, I use an external usb drive as install medium, might take a lil longer if you want to burn it to a CD. But actually there's no use for burning if you have any external drive, usb-hd/flash/doesn't really matter.
I think I don't have to mention that there won't be a GUI driven ubiquity installer, but I don't even want it. Just a basic, nice 8bit VGA installer. The ones which make you feel like actually installing an operating system :)

---

