---
title: "Help starting ubuntu w/o Compiz"
date: 2009-04-12
forum: General Help
---

### Post by monkeyKata on 2009-04-12
I was checking out compiz effects videos on youtube, enabling different things under the compiz effects manager thinking of how unique everything looked when I rendered by system unbootable.  Enabling magnify, I foolishly clicked to ignore other settings conflicts (I realize now it shared an initiate key combination with another enabled effect) and my screen went half blank half glitchy.  

Now I cannot boot up as normal, each time the screen goes out of wak and spits me back to the login screen.  The gnome failsafe something-or-another mode made no difference.

Luckily I'm booting and accessing the 'net off the boot CD.  I think all I have to do is find a way to boot back into Ubuntu with compiz disabled, at which point I can uncheck the effect that gave me this trouble before turning compiz back on.

I'd greatly appreciate any help anyone can offer.  I'm thinking maybe I can access a file on my drive, or somehow boot into a terminal mode...?

---

### Post by Universal344 on 2009-04-12
I don't know how you'd do it from the disk.  However, if you restart the machine, press escape when GRUB is loading (it should count down from 3) and then boot the newest kernel in recovery mode.  Once there, drop to a root terminal and run apt-get remove --purge ccsm compiz-gnome.  Then run shutdown -r 0.  The next time you log in Compiz should be uninstalled and everything should be fine.  At this point just reinstall compiz and reconfigure the settings.

---

### Post by monkeyKata on 2009-04-12
> **Universal344 said:**
> I don't know how you'd do it from the disk.  However, if you restart the machine, press escape when GRUB is loading (it should count down from 3) and then boot the newest kernel in recovery mode.  Once there, drop to a root terminal and run apt-get remove --purge ccsm compiz-gnome.  Then run shutdown -r 0.  The next time you log in Compiz should be uninstalled and everything should be fine.  At this point just reinstall compiz and reconfigure the settings.

Hey thanks so much for your quick reply.  Just one thing...

drop to a root terminal --> I'm not certain how to get to a root terminal.  Could I just add 'sudo' to the command you gave?  And purge is the equivalent in synaptic to 'complete remove,' right?

Edit:  And it's good to know at GRUB you can access a recovery mode.  I wasn't even aware.

---

### Post by Universal344 on 2009-04-12
When I have selected recovery mode in the past there has been a list of options one of which was drop to root shell.  If you are just getting a shell it is probably root already.  If there is a # in the prompt it is root and you don't need to run sudo, if there is a $ then it not root and you should run sudo.

---

### Post by monkeyKata on 2009-04-12
> **Universal344 said:**
> When I have selected recovery mode in the past there has been a list of options one of which was drop to root shell.  If you are just getting a shell it is probably root already.  If there is a # in the prompt it is root and you don't need to run sudo, if there is a $ then it not root and you should run sudo.

Yeah I used root shell, already had the #

I took out the 'ccsm' from the command you noted because it said no 'ccsm' found, then it worked and deleted both 'compiz' and 'compiz-gnome.'

However, starting back up produced the same problem, display blacking out after showing the desktop wallpaper for about a second, kicking me back to the login screen.

I looked in synaptic to have an idea of what else might be associated with compiz, and found different things: 'compiz-core, libdecoration0, conpiz-fusion-plugins-main, compiz-fusion--plugins-extra, compiz-plugins, compiz-wrapper, compiz-backend-gconf.'

Could it be I need to purge some of these other packages, too?  Thanks again for the help.

---

### Post by Universal344 on 2009-04-12
Yes they should all be removed.  I though that uninstalling compiz-gnome would cause it to remove the rest but if it didn't than just remove them manually.  Also, if this doesn't work you can try reinstalling GNOME (is ubuntu-desktop in repos).  And if you want to troubleshoot from graphical environment you can try installing a different desktop environment or window manager like IceWM or XFCE.

---

### Post by monkeyKata on 2009-04-12
ok yeah I'll try removing any other packages I find.  And if I were to reinstall Gnome, could this be in any way problematic?  I guess it already is. :p  Would the code on that be 

"apt-get reinstall gnome"

or perhaps "apt-get reinstall ubuntu-desktop"

is reinstall even the word you'd use?  Sorry for my terminal ignorance.

---

### Post by Aizawa on 2009-04-12
Type "sudo apt-get --purge remove ubuntu-desktop" and then "sudo apt-get install ubuntu-desktop" to reinstall it.

---

### Post by Universal344 on 2009-04-12
You shouldn't loose any data since you're just uninstalling the Desktop Environment.  On reinstall, everything should be fine except that your settings in GNOME may have to be set again manually.

---

### Post by monkeyKata on 2009-04-13
Thanks again for the help.

So I purged all of those other compiz packages and I was able to log back in to my setup.  Just one last thing, my windows no longer have borders and don't seem to show up on the bottom panel under the windows list.  I had to uninstall something related to emerald as well, which is probably the cause, though I thought without compiz it would default back to using metacity for the windows borders.

Is there a way to reset this without reinstalling compiz?

---

### Post by monkeyKata on 2009-04-13
Nevermind, everything's back to normal now.  I just needed to replace the old windows decoration command and restart.

Thanks for the help, I wouldn't have known how to go about it otherwise.  I didn't know compiz could be so dangerous... or perhaps it's the curious tinkering that in reality is more harmful.

---

### Post by RuleMaker on 2009-04-13
Of course, many ways and solutions. Maybe you should try metacity...not too eye-candy but does it purpose.
It's probably already installed on your system.

```
sudo apt-get install metacity
metacity --replace
```

---

### Post by DeMus on 2009-04-13
> **monkeyKata said:**
> Thanks again for the help.

So I purged all of those other compiz packages and I was able to log back in to my setup.  Just one last thing, my windows no longer have borders and don't seem to show up on the bottom panel under the windows list.  I had to uninstall something related to emerald as well, which is probably the cause, though I thought without compiz it would default back to using metacity for the windows borders.

Is there a way to reset this without reinstalling compiz?

Yes, there is:
Right-click on your panel and select "Add to panel"; then fill it out with (from left to right): Show Desktop, Window List, Workspace Switcher, and Trash.

---

