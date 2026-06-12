---
title: "If Windows = Registry and OS X = .plist...then what is Ubuntu?"
date: 2009-02-23
forum: General Help
---

### Post by hashbrowns on 2009-02-23
So, as a computer teacher, I find this question quite interesting. My students are starting a lesson on the differences between Windows, OS X, and Linux, and I want to figure out how the other two store their settings.

I know the most about windows, being its longest user, but I have some idea about how Mac uses plist files in the application support folders to store settings in lists.

But what does Ubuntu use for such things? In fact, how does Linux in general deal with settings? Is it the same with all distros, or is each one different? I'd love to hear more information :)

---

### Post by lykwydchykyn on 2009-02-23
Generally, global system settings are stored under /etc in discrete config files.  User-specific settings are stored in a user's home directory in "dotfiles" (files with names beginning with "." so they are hidden).

Gnome has a system called "gconf" that is a little more "registry-like" in some people's opinions, though it is still made of discrete files.  Most everything else uses XML or ".ini-style" configs.

---

### Post by jbrown96 on 2009-02-23
Linux has very strong text processing tools. Things like grep, sed, vi, perl, and python make dealing with text files very easy. Naturally, Linux uses plain text files for configuration files. There are basically two types of configuration files: system and user. Most system files are stored in the /etc/ directory. you can find lots of configuration files. The most famous as far as support goes is /etc/X11/xorg.conf. This is the configuration for the x-server. The user configurations are stored in a user's home folder. They are generally hidden (i.e. in files/folders with a . at the beginning). 


Windows used to use plain text files as well, but the organization was very poor. An application could place it's files anywhere because there weren't good folder permissions. This lead to a very chaotic system; config files would not be deleted when an application was uninstalled, or multiple configuration files with the same name would overwrite one another when placed in the same directory. The registry was supposed to create a very organized method for configuration options. however, there are serious performance problems. While a text file takes up space on a hard drive, it doesn't use much space; this file only needs to be accessed when its program was launched. Consequently, there was no performance impact from having old config files on the system. The registry does not behave like this. Since the entire registry must be read on each boot, it needs to be keep small and organized; however, applications frequently don't cleanly remove their registry "keys", so the system becomes cluttered and slow over time. The Linux system works on Linux because programs can only place files in specific areas, so the oraganization is kept clean and performance remains great because there is no registry database to load and read.

---

### Post by trash.eighty on 2009-02-23
Actually, while GConf is organized like the Windows Registry, everything is stored as XML.

---

### Post by hashbrowns on 2009-02-23
So, for my other question (sorry, just wanted a clarification) Linux in general works this way, with .conf files in folders below the /etc level? Or just ubuntu?

Yeah, I remember those "good ol'" win95 days with the .ini and .dll hell. Ironically that future windows versions will (probably) do away with it, and go back to separate, but specifically placed config files.

Thanks for the input, folks!

---

### Post by Slim Odds on 2009-02-23
> **hashbrowns said:**
> So, for my other question (sorry, just wanted a clarification) Linux in general works this way, with .conf files in folders below the /etc level? Or just ubuntu?

Lots of Unix, in general, use this method.

Also, the files don't generally end in .conf
They vary. Like /etc/hosts

---

### Post by mb_webguy on 2009-02-23
For the most part, Linux is Linux.  Different distributions just package different software with the OS, and maintain their own repositories.  Almost all Linux distributions use the [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), which defines the directories where different files are located, including configuration files.  (I've seen [one distribution]("http://www.gobolinux.org/") of Linux that used a different file hierarchy, but it was actually just an overlay on the standard filesystem.)  That means system-wide configuration files are typically located in the /etc directory, and user configuration files are located in hidden files and directories in the user's home directory.

The comments about gconf only apply to the Gnome desktop environment, though other desktop environments store settings similarly.

---

### Post by lykwydchykyn on 2009-02-23
Most Linux distros work this way, though I find Debian (and thus Ubuntu) is a little more consistent than others about keeping global configs in /etc.  Certain distros I've had to work with (which I won't name in order to avoid going on a distro-war tangent) have been known to stick certain configs under /usr or /var or /opt (grr).  

Don't let your remembrances of DOS/win 3.x/win9x color your opinons of config files.  There are a lot of non-obvious advantages to using discrete text config files over, say, a registry database.

---

