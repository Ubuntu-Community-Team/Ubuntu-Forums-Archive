---
title: "Colorful, verbose bootup like Gentoo?"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by MicroChris on 2007-10-31
I don't really like the Ubuntu uSplash, at all. I'm one of those Linux users that LOVES specific distros (especially Ubuntu), but when it comes to onscreen flavors, I get rid of any distro-specific logos, etc.

I booted a Gentoo LiveCD before. The bootup was colorful and verbose, and in my native resolution (1280x1024). Can this easily be done in Ubuntu? I know how to boot into verbose, and with the 791 option in grub for 1280x1024. I just LOVE the colors and the cleanliness to it.

Thanks!

---

### Post by MicroChris on 2007-10-31
Bump, please help!

---

### Post by Zorael on 2007-10-31
You'll likely not get a whole lot of responses after only an hour. ;)

While I've not seen the Gentoo boot splash you're describing, couldn't you up the resolution by adding the flag in GRUB (as you mentioned), and install a custom usplash theme?

I believe there are some over at kde-look.org and gnome-look.org. Search for usplash on gnome-look, and browse the Bootsplash category on kde-look.

---

### Post by MicroChris on 2007-10-31
That's the thing, I don't want usplash at all. I want a completely verbose, colorful boot screen that is in my native resolution.

Like this:

[http://www.linux-user.de/ausgabe/2005/05/068-gentoo/gentoo_boot_02.png](http://www.linux-user.de/ausgabe/2005/05/068-gentoo/gentoo_boot_02.png)

Except, I wouldn't really need the bar at the bottom and all that.

---

### Post by Zorael on 2007-10-31
Oh. Oh I see.

Well then, I retract my advice and instead humbly ask you to update this thread when and if you do find something.

That looks awesome. I want it.

---

### Post by MicroChris on 2007-10-31
> **Zorael said:**
> Oh. Oh I see.

Well then, I retract my advice and instead humbly ask you to update this thread when and if you do find something.

That looks awesome. I want it.

Will do! :)

---

### Post by Zorael on 2007-10-31
Is this it?

[http://dev.gentoo.org/~spock/projects/fbsplash/shots.php](http://dev.gentoo.org/~spock/projects/fbsplash/shots.php)

> fbsplash (formerly gensplash) is a userspace implementation of a splash screen for Linux systems. It provides a graphical environment during system boot using the Linux framebuffer layer.

fbsplash follows a design policy of being simple, lightweight and fast. To reduce bloat, it uses only a few most important libraries and does not require X11. The code is optimized to have minimal impact on boot-up time.

fbsplash is distro-neutral and can in principle be used on any Linux system which supports the framebuffer, but integration of fbsplash with the initscript system requires writing customized code for different Linux distributions. A reference implementation for Gentoo's baselayout-2 is provided on this site.

[http://ubuntuforums.org/showthread.php?t=178439](http://ubuntuforums.org/showthread.php?t=178439) <-- old though

---

### Post by MicroChris on 2007-10-31
Yeah, I saw that thread. It is old and I didn't want to try it lol.

---

### Post by Zorael on 2007-10-31
But it is fbsplash, then?

---

### Post by MicroChris on 2007-10-31
Seems to be. I know I clicked F-something for verbose which put it into the colorful verbose mode (like I had linked). There's gotta be another way to do it though, with no splash. I don't want to build fbsplash just to not really utilize it.

---

### Post by darkazurka on 2008-06-19
Look at the colors of Knoppix, and you'll freak out: [http://en.wikipedia.org/wiki/Image:Knoppix-3.8-boot.png](http://en.wikipedia.org/wiki/Image:Knoppix-3.8-boot.png)

:lolflag:

---

