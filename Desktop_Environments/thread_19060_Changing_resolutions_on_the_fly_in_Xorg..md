---
title: "Changing resolutions on the fly in Xorg."
date: 2005-03-10
forum: Desktop Environments
---

### Post by tvlad on 2005-03-10
I remember some time ago, an extension was introduced that enabled you to change resolutions on the fly, same as with windows, and i was in Xorg, and i tried CTRL ALT +/-, and nothing changed, perhaps i don't have that extension installed i wonder ?

---

### Post by eternity on 2005-03-10
You must define wich resolutions you want to switch between in you /etc/X11/xorg.conf. On my computer it looks like this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768"
        EndSubSection
EndSection

```

add the resolutions you want to this line:
Modes           "1400x1050" "1024x768"

---

### Post by scoon on 2005-03-10
[QUOTE=tvlad]I remember some time ago, an extension was introduced that enabled you to change resolutions on the fly, same as with windows, and i was in Xorg, and i tried CTRL ALT +/-, and nothing changed, perhaps i don't have that extension installed i wonder ?[/QUOTE]

Hey there, 

If you have other resolutions defince in your xorg.conf file then you can change them with CTRL ALT KEYPAD(+/-).  Your keypad's +/- are the keys that do that. 


scoon

---

### Post by kevanf1 on 2005-03-10
Hmmm, I was told that.  So I tried it on my newly installed Ubuntu tin.  It didn't work.  No change at all in resolution.  I have about three resolutions defined and the graphics card does support them so does the monitor.  I've also noticed that I cannot change the refresh rate.  It seems stuck at 60hz which is not nice on the eyes.  I tend to have it set to 70 or 72 hz normally.  So any ideas abou that?

---

### Post by bigzak on 2005-03-10
[QUOTE=kevanf1]Hmmm, I was told that.  So I tried it on my newly installed Ubuntu tin.  It didn't work.  No change at all in resolution.  I have about three resolutions defined and the graphics card does support them so does the monitor.  I've also noticed that I cannot change the refresh rate.  It seems stuck at 60hz which is not nice on the eyes.  I tend to have it set to 70 or 72 hz normally.  So any ideas abou that?[/QUOTE]
 It sounds as if X is throwing away your other graphics modes and leaving you with a 'vesa' (60Hz ick) mode instead. Check your /var/log/XFree86.0.log /or /var/log/xorg.0.log and see what it says about valid mode lines. It could be that your card has been detected to use the vesa driver rather than one specific to your card.

---

### Post by tvlad on 2005-03-10
I know that you can edit the xorg.conf, or the xf86 one, i was talking about on the fly resolution changing, i remember an extension was added some time ago, i tried ctrl-alt +/-, though i've got to restart to see if it works, because on the fly it most certainly doesn't.

I think it's the randr extension, i seem to have it, but i think it's an xf86 version, gonna upgrade to the xorg one and see what comes of it. :P

---

### Post by tvlad on 2005-03-10
I was correct, it's the randr extension, now i can change resolutions on the fly, wheee.  8)

---

