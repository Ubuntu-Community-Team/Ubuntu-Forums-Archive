---
title: "LILO 22.8 Loading Linux... takes two minutes"
date: 2008-12-14
forum: General Help
---

### Post by infinitejones on 2008-12-14
I recently re-installed Intrepid on my HP Pavilion dv6000 laptop. I formatted the / partition as XFS - no real reason why, I just thought I'd give it a go.

Towards the end of the installation process it advises you, if you've installed /boot files on XFS, to use LILO instead of GRUB because it says GRUB often fails with an XFS partition. So I let the installer install LILO.

Now, when I boot up, the first thing that appears on the screen is "LILO 22.8 Loading Linux" and the first three lines fill up with dots, followed by a message about the completed BIOS check. After that everything boots as normal. However, it takes about two minutes for the three lines of dots to appear, which is annoying, obviously.

The obvious answer is to re-install with a / partition (or a /boot partition) formatted to something other than XFS but that's a pain and I can't be bothered unless it's my only option.

I've tried googling with very little luck, apart from one post on a weird forum that started talking about compiling a custom kernel, but then tailed off.

Any ideas how can I skip the BIOS check? Or, can I somehow create a new non-XFS partition for the /boot files, remove LILO, and install GRUB? That second option sounds actually sounds more hassle than just re-installing on a non-XFS partition...

Thanks!

---

