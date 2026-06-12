---
title: "Can't configure proper shortcuts"
date: 2008-12-14
forum: Desktop Environments
---

### Post by El Rogueo on 2008-12-14
Hi all,

tl;dr, What desktop environment makes it easy to use static shortcuts (similar to Launcher in standard ubuntu) that can be created or configured from command line?

Or, the long version:

I'm running an old 486 pentium 2 with about 256 of RAM, with minimal ubuntu server installed as the base system for this project.

I've been in the process of creating my own live CD/DVD, in accordance with [http://ubuntuforums.org/showpost.php?p=4887531&postcount=65](http://ubuntuforums.org/showpost.php?p=4887531&postcount=65) and [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872) , but I've run into a snag.

The applications I want to run either run better on windows, or have linux installations which are not from .deb packages, and thus suffer from obscure dependency errors (missing libraries that I've already installed, etc). For this reason, I chose to run them through Wine, something which has been going surprisingly well for me, with two qualms:

When I start Wine, I cannot get it to open in a GUI to save my life. It will always have to be called in the form ```
wine [PROGRAM]
``` and won't ever show me the directory structure unless I look through the folders by hand in CLI. This is acceptable. However, the people I want to provide this disc are less than linux literate, and I don't want them to have to use any brainpower to run the applications.

But making symlinks isn't really what I want, and I can't open the Xorg server inside chroot (part of the guide involves manipulating the system-to-be in chroot) so I can't see what I'm doing very well.

Is there a very easy to use desktop environment I can install, and then just edit some sort of menu configuration file and add my own application tabs using nano or vi?

Thanks,
El Rogueo

---

