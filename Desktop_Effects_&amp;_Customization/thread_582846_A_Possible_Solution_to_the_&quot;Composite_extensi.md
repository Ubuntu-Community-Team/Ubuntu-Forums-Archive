---
title: "A Possible Solution to the &quot;Composite extension is not available&quot; Problem"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by ahetland on 2007-10-20
Greetings!

It seems that I am not the only person to encounter problems when attempting to enable the "Extra" option under System -> Preferences -> Visual Effects

In my case I got the error "Composite extension is not available", which I have seen reported a few other places while trying to dig up a solution to this problem.

Since quite a few people are having this problem, I thought I'd share the solution that worked for me here.

All it took was to simply enable the composite extension in the xorg.conf file (located in /etc/X11/).

To enable the composite extension first open a terminal and type:
```
sudo gedit /etc/X11/xorg.conf
```

This will open the xorg.conf in Gedit while allowing you to edit it (hence the passoword promt). Find the following section:
```
Section "Extensions"
    Option         "Composite" "Disabled"
EndSection
```

It can also look like:
```
Section "Extensions"
    Option         "Composite" "0"
EndSection
```

Either way, change it to:
```
Section "Extensions"
    Option         "Composite" "Enabled"
EndSection
```

Now save the file and close whatever apps you have running. Restart your X session by hitting ctrl+alt+backspace.

It should now be possible to enable the "Normal" and "Extra" visual effects.

I hope it worked for you aswell. The visual effects are great :)

---

### Post by modest moose on 2007-10-21
It fixed the problem of it saying composite extension unavailable, but now it just says desktop effects could not be enabled.

---

### Post by Tachyon1000 on 2007-10-21
Yeah, I have "Composite" "0" and all effects work fine for me, so I don't think that is it.  Depending on your graphics cards, there are various fixes that people have proposed but my system has worked from the get-go with Gutsy so I can't say that I have had to troubleshoot much of anything.

---

### Post by oregonbob on 2007-10-21
I also received this error on U 7.10. I have an HP with onboard Nvidia 6150 SE GeForce.

My /etc/X11/xorg.conf had composite set to disable. After enabling I no longer got error and enhanced screen stuff seems to work now.

Thanks

---

### Post by latheesan on 2007-10-21
you are awsome man!!!

this worked on my feisty :)

---

