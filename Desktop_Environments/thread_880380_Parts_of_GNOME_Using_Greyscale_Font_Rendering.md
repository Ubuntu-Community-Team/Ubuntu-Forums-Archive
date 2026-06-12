---
title: "Parts of GNOME Using Greyscale Font Rendering?"
date: 2008-08-04
forum: Desktop Environments
---

### Post by cicatriz on 2008-08-04
I've been doing some messing around with freetype2, and I've finally decided that using the Autohinter with the BCI settings (found in ftoption.h?) default to Ubuntu produce beautifully hinted and kerned text with Bitstream Vera Sans Roman.  I reinstalled the current Ubuntu release (Version: 2.3.5-1ubuntu4) of everything relevant with Synaptic, but I'm not sure if there's something left over.

However, only some GTK+2 apps are using this rendering style, and I am confounded thus far.  Firefox obviously is unaffected by the GNOME settings, as it uses its own scheme, and it looks gorgeous--particularly fixed-width serif fonts, which have the same clarity that fonts do with XP's ClearType.  GIMP, Totem and several others are also graced by this look, but some are not, such as gnome-terminal.  Having nice fonts in these few applications is great, but the only part of GNOME "itself" that seems to follow is the desktop icons.  I cannot reliably configure my fonts because the Appearance helper is similarly ugly, as are most of the other helper apps.

I've read several threads concerning fonts, particularly with Firefox, and none of them seem to fit this problem; most of them report Firefox to be the bad guy.  I've seen rendering similar to this when the turner patches were applied to older versions of libcairo, libpango (IIRC), etc., but I hadn't gone that far, and the only software supposed to be compiled against non-system Cairo that I've seen is Firefox (correct?), which is particularly puzzling.  

Could someone give me a push in the right direction?  I figured I would ask now while I'm still trying to gather information in case I can help solve this for someone else.

Attached is a screenshot; the top text is from the GIMP Acquire menu, and the bottom is from my GNOME application menu.

---

### Post by cicatriz on 2008-08-06
I'm going to bump this once, and if it doesn't work, I'll go away.  :)

---

### Post by cicatriz on 2008-08-07
Okay, I am going to tenuously claim this is as due to a bug.  According to Launchpad, some parts of GNOME ignore the RGB subpixel rendering flag regardless of where it is placed.

Setting 

<match target="font">
<edit name="rgba" mode="assign"><const>rgb</const></edit>
</match>

in ~/.fonts.conf should immediately alleviate this problem, but this is what is being ignored.  gnome-panel, gnome-appearance-properties, et al. do, but as mentioned before, GIMP is the only program I have found to honor this value.

---

