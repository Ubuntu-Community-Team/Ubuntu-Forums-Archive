---
title: "Plymouth stuck. Two splash screens at boot! Can't remove one! Can change the other."
date: 2015-03-21
forum: Desktop Environments
---

### Post by ahears on 2015-03-21
I have a system I just set up and was managing the splash screen at boot, installed a Burg manager and changed the default plymouth. Everything works great but the Plymouth splash. I used the command:

 ```
 [COLOR=#0000ff]sudo update-alternatives --config default.plymouth[/COLOR]
```

Which produces the output:

> Selection    Path                                                               Priority   Status
------------------------------------------------------------
 *0            [COLOR=#ff0000]/lib/plymouth/themes/ubuntu-logo/ubuntu-logo-gnome.plymouth[/COLOR]               100       auto mode
  1            /lib/plymouth/themes/solar/solar.plymouth                                  10       manual mode
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo-gnome.plymouth               100       manual mode 

Then:

```
[COLOR=#0000ff]sudo update-initramfs -u[/COLOR]
```

The Problem seems to be that this does in fact work but that there is a splash that loads before the plymouth and won't unload through these commands. If I press the ESC key to see the text output at boot, then press ESC _again_*..(this restores the graphic).* the plymouth changes to the splash I have set! The stuck splash has the purple background and the animation that fills a small white circle and prints the word "Bizcom". On shutdown everything is fine and the Plymouth loads (unloads) as it should. I used Synaptic to completely remove the unwanted Plymouth Theme packages but it is stuck. I can't get it out. It is not the splash I wanted I was just testing different themes when it happened. To be a little more clear, after pressing escape the second time at boot the graphic does appear from the "ubuntu-logo-gnome" theme. The Solar theme is never seen nor used. The unwanted theme has been uninstalled but is still stuck. I do want the "ubuntu-logo-gnome" theme. How do I replace the unwanted graphic that loads before my theme but after the Burg Loader?

---

### Post by dino99 on 2015-03-22
is it Burg still maintained ? I've already seen some complaints about it  in the past weeks.
why not purging it ?

---

### Post by ahears on 2015-03-22
Your post prompted me to check the Burg loader and update it as well as the Grub loader:

These were the commands that fixed it for me:

```
 [COLOR=#008000]sudo update-alternatives --all[/COLOR]
```

> Changed my choice from [COLOR=#0000cd]Gawk to Mawk[/COLOR], then changed my Plymouth selection to my new choice (ubuntu-logo-gnome), _all other selections at defaults_.

```
 [COLOR=#00ff00]sudo update-burg && sudo update-grub[/COLOR]
```

Problem SOLVED! Not sure why this "un-stuck" my graphic, but it did:)

UPDATE:

Now I went back and made these changes: *Thought this may not be relevant, this was the entire process I used*:

Again I executed this command:

```
 [COLOR=#008000]sudo update-alternatives --all[/COLOR]
```

> Change my choice from [COLOR=#0000cd]Mawk back to Gawk.[/COLOR][COLOR=#0000cd]

Reboot and all is as it should be. Now I can change themes without getting "stuck" again.
[/COLOR]

---

