---
title: "FIESTY HOW TO: fix beryl / compiz window borders"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by Talz on 2007-04-20
well i was having some problems with beryl or compiz rendering correctly   *missing window borders and stuff*

and i noticed alot of other posts have the same problem

if other methods havent worked  this is the one

this is sheer dumbness on so many ppls parts

to fix the missing borders and such

[SIZE="3"]
EDIT your xorg.conf file   and set the default color depth to 24
was prolly stuck on 16

if that dont work

change your nvidia settings(X server display configuration)
to Millions of colors (32bpp)

dont forget to logout and press ctr + alt + backspace   before yelling at me cause it didnt work
[/SIZE]

uh  if this dont work ( did for me)
then  iunno your problem must be differnt somehow

ati ppl uhhh  sorry ati hates linux

---

### Post by Lykourgos on 2007-04-20
I had the same problem and it was solved just by selecting the Copy option in the:
Beryl Manager->Advanced Beryl Options->Rendering Path

---

### Post by gearshifter on 2007-04-20
copy rendering is slow though :(..  there has got to be a fix out there

---

### Post by pparks1 on 2007-04-20
Yes, that was extremely slow for me too.  I set it back to automatic.

Issued this command
sudo nvidia-xconfig --add-argb-glx-visuals

Restarted X and all is well  (ctrl-alt-backspace)

---

### Post by The Pinny Parlour on 2007-04-20
I still have no borders on restart and have tried the suggested methods.  Any more ideas? before I throw the whole out the window in disgust at myself at why I upgraded?

---

### Post by craigsharp on 2007-04-20
> **pparks1 said:**
> Yes, that was extremely slow for me too.  I set it back to automatic.

Issued this command
sudo nvidia-xconfig --add-argb-glx-visuals

Restarted X and all is well  (ctrl-alt-backspace)

Worked like a charm,  I now have beryl running like a champ!

Thanks for that great piece of info!

---

### Post by jiminycricket on 2007-04-20
> **pparks1 said:**
> Yes, that was extremely slow for me too.  I set it back to automatic.

Issued this command
sudo nvidia-xconfig --add-argb-glx-visuals

Restarted X and all is well  (ctrl-alt-backspace)

Thanks

---

### Post by ~SkyBlue~ on 2007-04-20
> **pparks1 said:**
> Yes, that was extremely slow for me too.  I set it back to automatic.

Issued this command
sudo nvidia-xconfig --add-argb-glx-visuals

Restarted X and all is well  (ctrl-alt-backspace)

Any idea how to do this without having nvidia video card? Above command is not found on my box maybe because I'm using Intel 855GM Integrated Graphics on a laptop.

---

### Post by jiminycricket on 2007-04-21
Skyblue, have you tried this?  [http://ubuntuforums.org/showthread.php?t=291464](http://ubuntuforums.org/showthread.php?t=291464)

---

### Post by Bundai on 2007-04-21
Tried to do that sudo nvidia-xconfig --add-argb-glx-visuals and everything else, but still no luck. Can't see my window borders and the cube is completely broken and my workspaces aren't working either (this is when beryl windows manager is selected). 
Edit: And sometimes when I try to do those suggested things I just get whitescreen, but not always. Then its weird. It says that my processor use is always 100%.

---

