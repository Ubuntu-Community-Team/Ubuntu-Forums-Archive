---
title: "Manual opacity option for compiz gone. Different version of ccsm?"
date: 2008-03-29
forum: Desktop Effects &amp; Customization
---

### Post by Smatt454 on 2008-03-29
NOTE: I AM USING KUBUNTU 7.10 WITH KDE. I AM NOT USING UBUNTU OR GNOME


Today adept updater gave me some updates for compiz and emerald. 
if i was to update emerald, adept said that it would break. 
running through the CLI said i need a newer version of libwnck18. adept said that this would not be installed when i updated emerald (obviously)so i had to get it from source

before i had gotten the new version of libwnck18, i uninstalled compiz and emerald. after i installed the new libwnck18, installing compiz and emerald worked fine. However, when i ran ccsm, i got an error. 
i received two solutions from ubuntuforums. one said to reinstall ccsm from a different repository (they didnt give another repository to get it from) the other said to comment out this line from /usr/
> #idle = ccm.IdleSettingsParser(context)

commenting out this line fixed my error. However it seems i have a different version of ccsm than i did before. i have a bunch of new plugins. (such as snow, cube atlantis,reflection,and others) all of these new plugins crash compiz, except for reflection. everything else seems to work fine.

there is one exception. before in general options, i had the option to change keybindings for changing the opacity of windows. for example, before i had ctrl+alt+f increase the opacity, and ctrl+alt+h lessen the opacity. this was an EXTREMELY useful option for me, and i would like to  be able to get it back.

 i have a computer at school with this option, so if there is a config file i can copy, i can do that.  but i do not know how to edit compiz through the command line (i would very much like to!)

as i stated, this option was very useful to me. 

also, if anyone can help me get the new options i have to work (like the snow option) i would appreciate that to. but i would like to solve my initial problem first.

thanks!

---

