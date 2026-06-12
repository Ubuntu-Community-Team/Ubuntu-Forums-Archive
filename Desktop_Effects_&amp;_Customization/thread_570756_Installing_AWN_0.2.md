---
title: "Installing AWN 0.2"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by Unknownz on 2007-10-08
Hello everyone, new here, it's a great and helpful community here.

Ok let's get to the point:

I downloaded the recently released version of AWN which is 0.2 from :
[https://launchpad.net/awn/+download](https://launchpad.net/awn/+download)

When I try running the commands:
./configure && make && sudo make install

It goes for a couple of seconds, everything seems fine, then gets stuck in configure and gives me the following error message:
> checking for PYCAIRO... configure: error: Package requirements (pycairo >= 1.0.2) were not met:

No package 'pycairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYCAIRO_CFLAGS
and PYCAIRO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

The problem is I already have the latest version of python-cairo installed.
What could be the problem? Is there a missing package or something?

---

### Post by MrBordello on 2007-10-08
Hi!
check this:
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")
Theres already a repo! If you like som eye-candy, be sure to check out [Screenlets]("http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users")

---

### Post by MrBordello on 2007-10-08
Here's a little teaser, just to keep you motivated

---

### Post by usmanlinux on 2007-10-08
> **MrBordello said:**
> Here's a little teaser, just to keep you motivated

i would kill for my desktop to look like that, how did ya get those icons on the bottom? please advise as im slightly stoopid aka linux newb

---

### Post by MrBordello on 2007-10-08
You'll need working compiz (Gutsy works perfect)
[LIST=1]
[*]Install [AWN]("http://ubuntuforums.org/showthread.php?t=385981")
[*]Install [Screenlets]("http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users")
[*]Checkout [Screenlets Repository]("http://www.screenlets.org/index.php/Category:UserScreenlets")
[*]sudo apt-get install ubuntustudio-theme ubuntustudio-icon-theme
[/LIST]
That's it ;)

---

### Post by smartboyathome on 2007-10-08
Or, if compiz doesn't work, get xcompmgr.

---

### Post by Unknownz on 2007-10-08
Thanks all of you guys for all your help :) I'll be setting up all of this and get back at you with my results.

Hope it turns out like MrBordello's, it rocks!

EDIT: Well you can see my results in the screenshot. I didn't want to add the sidebar, because I want to keep the screen free and spacious. But I'm looking for some useful screenlets that I might add. :)

---

### Post by MrBordello on 2007-10-09
nice! :)

---

### Post by dmber on 2007-10-09
can i ask for a bit more specificity?  that thread is like 80-some pages long.  what page should i be reading?

---

### Post by smartboyathome on 2007-10-09
> **Unknownz said:**
> Thanks all of you guys for all your help :) I'll be setting up all of this and get back at you with my results.

Hope it turns out like MrBordello's, it rocks!

EDIT: Well you can see my results in the screenshot. I didn't want to add the sidebar, because I want to keep the screen free and spacious. But I'm looking for some useful screenlets that I might add. :)

If you are using Compiz Fusion, it now has a "Widget Layer" plugin that might be of use to you. It allows you to hide all widgets (screenlets can be set as Widgets via the right click > window menu), and then show you them on a key press (default is F9). I do this and like it. :)

---

### Post by MrBordello on 2007-10-10
> **dmber said:**
> can i ask for a bit more specificity?  that thread is like 80-some pages long.  what page should i be reading?
For AWN I guess ...? This is the important part:
Repository:

NOTE: Repository is for Feisty and Gutsy 32-bit and 64-bit.
If you are using Gutsy, this is the recommended method of installation.
NOTE TO FEISTY USERS: The feisty debs are no longer updated.

Just add the appropriate lines to your /etc/apt/sources.list:

Feisty:
Code:

```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```

Gutsy:
Code:

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

Then do this in a terminal:
Code:

```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg 
sudo apt-key add 8434D43A.gpg
rm 8434D43A.gpg
sudo apt-get update
```

Then install AWN:
Code:

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

