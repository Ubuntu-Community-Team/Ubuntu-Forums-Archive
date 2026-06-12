---
title: "Misc settings applied at boot (which file?)"
date: 2005-08-11
forum: Desktop Environments
---

### Post by blueturtl on 2005-08-11
I'm starting to gather up bunch of settings I have to apply manually everytime I boot, because I have no idea where these things are supposed to go. Currently the ones I'd most like automated are enabling DMA to my DVD drive **(hdparm -d1 /dev/hdc)** and uploading a standard soundfont **(asfxload sndfont.sf2)** for midi functionality. Is there a settings file I can just write down all these commands to that would be run at startup?

---

### Post by tommie-lie on 2005-08-11
[QUOTE=blueturtl]Currently the ones I'd most like automated are enabling DMA to my DVD drive **(hdparm -d1 /dev/hdc)**[/quote]Have a look at /etc/hdparm.conf.

[quote=blueturtl]and uploading a standard soundfont **(asfxload sndfont.sf2)** for midi functionality.[/QUOTE]Most manpages point to a configuration file in the FILES section, maybe one of the manpages from the awesfx package also does so.

---

### Post by blueturtl on 2005-08-12
> Have a look at /etc/hdparm.conf.

Thanks, this solved the problem with my DVD drive.

> Most manpages point to a configuration file in the FILES section, maybe one of the manpages from the awesfx package also does so.

/etc/sfxloadrc is indicated, but the instructions for it's use are a bit vague or non comphrehensible for someone who's native tongue isn't English. My sfxloadrc currently looks like this and it isn't working:

[INDENT]#
# awesfx configuration file
#

default --path=/usr/share/sounds/sf2/
default 8MBGMSFX.SF2[/INDENT]

the command asfxload 8MBGMSFX.SF2 works just fine when entered from commandline. I know midi's aren't that trendy, but every now and then there is a file to be played and it would be nice having it "just work".

---

### Post by tommie-lie on 2005-08-12
[QUOTE=blueturtl]/etc/sfxloadrc is indicated, but the instructions for it's use are a bit vague or non comphrehensible for someone who's native tongue isn't English. My sfxloadrc currently looks like this and it isn't working:

[INDENT]#
# awesfx configuration file
#

default --path=/usr/share/sounds/sf2/
default 8MBGMSFX.SF2[/INDENT][/quote]As far as I understand the manpage, this should not work. "default" can be seen as the name of all fonts together. So you can specify some parameters for all fonts as you like it. "default 8MBGMSFX.SF2" is not supposed to work, as there is not commandline parameter "8MBGMSFX.SF2" that can be applied to all fonts.
I don't know for sure (don't have awefsx installed, good thing there are manpages in HTML format in the net ;-)), but maybe a single line "8MBGMSFX.SF2" in the sfxloadrc may help.
If it does not, I found a mail in the german debian mailinglist suggesting something like this in /etc/modules.conf:
[indent]post-install awe_wave /usr/bin/asfxload 8MBGMSFX.SF2[/indent]
I don't know if the module is still named awe_wave, the mail is from 1999 (!) and the problem concerned kernel 2.2, but the principle of post-install directives for modules is still the same, but especially the names may change over the years ;-)

The original mail can be read here: [http://lists.debian.org/debian-user-de/1999/04/msg00780.html](http://lists.debian.org/debian-user-de/1999/04/msg00780.html)

---

