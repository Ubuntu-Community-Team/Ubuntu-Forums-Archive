---
title: "Steam Game Problems Ubuntu 14"
date: 2014-07-19
forum: Gaming &amp; Leisure
---

### Post by Axioen on 2014-07-19
Hey everyone. I'm having some problems with Steam. I've had an Inspiron N5110 for maybe 4 years now or so, and for 80% of  that time I had Windows 7 on it, it came preloaded. A few months ago I  switched to Ubuntu 14.04. I removed Unity and lightdm and replaced them  with i3 Window Manager. Playing Garry's Mod was great, it worked fine. I was able to play on the highest graphics settings  (which I wasn't able to do when I ran Win7) presumably due to OpenGL (I'm not really sure, I don't know that much about it),  but now I try to play it and it's to the point where I cant move. 1  frame will hang for maybe 10 seconds. Htop is telling me it's maxing out  my cpu and ram. I don't understand why this is happening all of a  sudden, when just recently it was working fine. Exiting Gmod, everything  returns to normal. 

Hardware:

4 gb ram
i3-2330M @ 2.2ghz
1gb Intel HD integrated

Appreciate the help.

---

### Post by billdozor on 2014-07-20
Do you experience this in any other games?
Was there any kernel or graphics driver updates in between when it worked and didn't?

---

### Post by oldrocker99 on 2014-07-20
> **billdozor said:**
> Do you experience this in any other games?
Was there any kernel or graphics driver updates in between when it worked and didn't?

Exactly; I had a kernel update this weekend. It's quite prudent to do this:

```
sudo apt-get install dkms
```

This (**D**ynamic **K**ernel **M**odule **S**upport) will keep your current driver linked to any new kernel that might get installed. 

Not that this is necessarily your problem, but having dkms installed is a good idea.

---

### Post by Axioen on 2014-07-23
I dont remember to be honest, but yes it occurs with all games.

---

