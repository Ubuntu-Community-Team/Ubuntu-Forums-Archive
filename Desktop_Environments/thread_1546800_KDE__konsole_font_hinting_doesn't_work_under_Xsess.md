---
title: "KDE / konsole font hinting doesn't work under Xsession"
date: 2010-08-05
forum: Desktop Environments
---

### Post by mandar.mitra on 2010-08-05
Fonts for konsole are rendered differently under Xsession (with fvwm, no KDE / Gnome) and KDE / Gnome. Under KDE or Gnome, if I look very closely, I can see little coloured lines in the characters. Under Xsession, those very thin coloured lines disappear and the characters appear slightly weaker / eaten away. I prefer the former look, but can't get it to work under Xsession.
 
 I'm running a more or less up-to-date version of 10.04. Would be grateful for any pointers to what is causing this difference and how I can fix it.
 
Other details: Using systemsettings, I have turned on font hinting and subpixel smoothing (?) to RGB. My kdeglobals file says:
 XftHintStyle=hintslight
 XftSubPixel=rgb
 
 I also have the following in my ~/.fonts.conf:
 <match target="font">
   <edit mode="assign" name="rgba">
    <const>rgb</const>
   </edit>
  </match>
<match target="font">
   <edit mode="assign" name="hintstyle">
    <const>hintslight</const>
   </edit>
</match>

---

