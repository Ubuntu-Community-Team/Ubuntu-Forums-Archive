---
title: "Kubuntu 11.10 opengl compositing issue"
date: 2011-10-21
forum: Desktop Environments
---

### Post by Montblanc_Kupo on 2011-10-21
I searched a bit and found some similar issues described but nothing exactly like this... and none of the suggestions in them really applied.

I'm having a weird issue with a specific machine running KDE. Clean and updated install of Kubuntu 11.10. nvidia 5500 graphics card. I am able to run desktop effects, but there is visual corruption. I changed the compositing to xrender, which fixes the corruption but I can't do half the effects and it's much slower / laggier than opengl. 

Here's a picture of what happens when I enable opengl:

[img]http://i.imgur.com/Pt6cy.png[/img]

I haven't seen this issue with My other computers, so I'm not sure what I could check. I have the nvidia 173 drivers installed via "additional drivers" and it says it's activated. Opengl enables with no errors and runs smoothly, with the exception of the visual corruption.

---

### Post by froghopper on 2011-10-22
This can be fixed with the commandline

```
kwin --graphicssystem=native --replace &
```

It is due to the new raster graphics system used as default in kde 4.7. This bug report explains it [https://bugs.kde.org/show_bug.cgi?id=282882](https://bugs.kde.org/show_bug.cgi?id=282882)

---

### Post by Montblanc_Kupo on 2011-10-23
> **froghopper said:**
> This can be fixed with the commandline

```
kwin --graphicssystem=native --replace &
```

It is due to the new raster graphics system used as default in kde 4.7. This bug report explains it [https://bugs.kde.org/show_bug.cgi?id=282882](https://bugs.kde.org/show_bug.cgi?id=282882)

Nope... still broken. When I apply it, it fixes the top of the graphics dialog itself... but other windows stay broken. Any newly generated windows are also broken. If I reboot, everything is borked again. Are there any other things I should / could check?

---

### Post by froghopper on 2011-10-23
Hmm worked fine for me, follow the instructions in comment #10 on the bug report to replace /usr/bin/kwin and reboot, see if that fixes it permanently.

---

### Post by Montblanc_Kupo on 2011-10-23
> **froghopper said:**
> Hmm worked fine for me, follow the instructions in comment #10 on the bug report to replace /usr/bin/kwin and reboot, see if that fixes it permanently.

After following the instructions in the linked page, it doesn't even fix the settings dialog page anymore. There is no change, it's still broken, and it tells me that "kwin" can be found in multiple packages and I should use apt-get to download it.

---

### Post by schnelle on 2011-10-24
You can try with resetting kwin to its defaults. Delete kwin config file ~/.kde/share/kwinrc and then alt+f2 and type ```
kwin --replace
```

You can also try solution from kubuntu forum: [http://kubuntuforums.net/forums/index.php?topic=3118839.0](http://kubuntuforums.net/forums/index.php?topic=3118839.0)

---

### Post by Montblanc_Kupo on 2011-10-24
> **schnelle said:**
> You can try with resetting kwin to its defaults. Delete kwin config file ~/.kde/share/kwinrc and then alt+f2 and type ```
kwin --replace
```

You can also try solution from kubuntu forum: [http://kubuntuforums.net/forums/index.php?topic=3118839.0](http://kubuntuforums.net/forums/index.php?topic=3118839.0)

Booted up to try this, and whatever the last commands did took away all the title bars completely... and the mouse would no longer select things. Windows weren't redrawing either so there were ghost versions of menus when I could get them brought up via keyboard. 

I dropped to CLI entirely and I wasn't able to locate the files you described at all where you specified. When I try to invoke kwin --replace, it gives me the "use apt-get" response again.

Weird error is weird and not worth debugging... I'm just gonna reinstall the os. It's a second computer I'm setting up for someone else, so I'll just let it sit in the corner and do it's thing.

Still doesn't get Me any closer to having functional opengl compositing though... :(

I appreciate the help... if anyone has any other ideas, please let me know.

---

### Post by schnelle on 2011-10-24
Hmmmm... very weird. Did you delete kwinrc file? You can do it from command line: ```
rm ~/.kde/share/config/kwinrc
``` and then reboot.

Kwinrc is just a config file. I did remove it a lot of times without any issues.

---

### Post by Montblanc_Kupo on 2011-10-24
> **schnelle said:**
> Hmmmm... very weird. Did you delete kwinrc file? You can do it from command line: ```
rm ~/.kde/share/config/kwinrc
``` and then reboot.

Kwinrc is just a config file. I did remove it a lot of times without any issues.

That's what I was saying... I went there... and I saw no "kwinrc". I tried rm and it said there was no such file.

Something must have gotten broken somewhere along the way. It's 30% done with the reinstall. It doesn't take much time to do a full install of kubuntu off usb stick. Since I'm not a guru, I use that solution a lot of times. ;)

---

