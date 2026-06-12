---
title: "Possible error in Restricted Formats Wiki (Flash): Please Confirm"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Q4U on 2006-06-27
I'm using Kubuntu with Firefox 1.5.04, which was installed following [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

In order to make Flash work with the newly installed Firefox, one needs create a couple of symlinks as explained in [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) (chapter 10: Macromedia Flash)

"[I]Note to users of non-Ubuntu versions of Firefox: If you are using Ubuntu 5.10 or prior and installed a non-Ubuntu version of FireFox 1.5.x (following the instructions on FirefoxNewVersion for example), you will need to make a new symlink for the flash plugin. To do so, invoke the following command:

sudo ln -s /usr/lib/mozilla-firefox/*flash* /opt/firefox/plugins"
[/I]

This does not work. It should be:

sudo ln -s /usr/lib/mozilla/*flash* /opt/firefox/plugins

In addition, I use Breezy (6.04), and yet had to do this - possibly because I apt-get upgrade'd the system instead of reinstalling from scratch.

Can someone using Firefox with Kubuntu confirm that this is indeed a mistake (as opposed to a weirdness of my system) so that we can change the wiki? 

Thanks. Q

---

### Post by rai4shu2 on 2006-06-27
[QUOTE=Q4U]In addition, I use Breezy (6.04)...[/QUOTE]

You use what?

---

### Post by Q4U on 2006-06-27
Pardon me, small mistake: I use Kubuntu 6.06

Q

---

