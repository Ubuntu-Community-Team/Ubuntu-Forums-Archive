---
title: "vertical scroll area too large intrepid"
date: 2009-03-10
forum: General Help
---

### Post by pikaia on 2009-03-10
Hey everyone.  I just upgraded to Intrepid and the touchpad on my gateway mx6422 is really annoying me.  The touchpad has a designated vertical scroll area, but Intrepid defaults it in more than double that distance to take up a full third of the touchpad.  So whenever I'm moving the cursor around the desktop, it either stops altogether or starts switching between workspaces, back and forth.  I had a similar issue in Hardy, but was able to fix it with SHMConfig in xorg.  But since there is no touchpad device in xorg (since I've read that its handled by HAL now) I don't know here to go from here.  I just want to move the vertical scroll area back to where it belongs.  

Any ideas on how to modify this in Intrepid?  I'm using the 32-bit version.

Thanks.

---

### Post by pikaia on 2009-03-11
Ok.

I've read through a ton more threads and have continued to try to fix this to no avail.  I've enabled SHMConfig according to the help file.  And can use synclient to set my RightEdge properly, but it doesn't hold up to a reboot.  I've read through the X/Config/Input Wiki but can't seem to make heads or tails on how to configure this in HAL.  I don't have a file that I can find that lists the parameters that are listed by the command 
```
xinput list-props "SynPS/2 Synaptics TouchPad"
```

Can anyone help?

Thanks.

Oh.  I also have the problem with the network manager trying to constantly connect to the wireless network when connected to a wired network, and have seen this issue over and over but no solution.  (have seen 3 bug reports but no fixes...) Could be my search query.

---

