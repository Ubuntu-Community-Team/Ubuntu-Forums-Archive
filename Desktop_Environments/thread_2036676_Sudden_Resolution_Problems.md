---
title: "Sudden Resolution Problems"
date: 2012-08-02
forum: Desktop Environments
---

### Post by marteboi on 2012-08-02
Out of nowhere my display is no longer in the correct resolution (or aspect ratio for that matter) The correct settings isn't listed in display and I'm too much of a newcomer to know the proper solution.

I don't even know where to begin on trying to solve this.

---

### Post by orange2k on 2012-08-02
What is your graphics card and what drivers do you use?

---

### Post by marteboi on 2012-08-02
My graphics card is a Nvidia Geforce 5200 fx, and I'm not sure, I just went to additional drivers to install it,

---

### Post by orange2k on 2012-08-02
> **marteboi said:**
> My graphics card is a Nvidia Geforce 5200 fx, and I'm not sure, I just went to additional drivers to install it,

And if you run Nvidia-X Server settings there is no correct resolution for your monitor available?

---

### Post by marteboi on 2012-08-02
> **orange2k said:**
> And if you run Nvidia-X Server settings there is no correct resolution for your monitor?

Actually, It claims my driver is too old to to anything with display configuration

---

### Post by orange2k on 2012-08-02
> **marteboi said:**
> Actually, It claims my driver is too old to to anything with display configuration

Then try to install the Nvidia-current driver in the additional drivers menu, maybe this will fix the problem...

(thats the recommended option)

---

### Post by marteboi on 2012-08-02
> **orange2k said:**
> Then try to install the Nvidia-current driver in the additional drivers menu, maybe this will fix the problem...

(thats the recommended option)

I did, before i posted, Under additional drivers I have the recommended, installed and in use

---

### Post by orange2k on 2012-08-02
> **marteboi said:**
> I did, before i posted, Under additional drivers I have the recommended, installed and in use

Then maybe it is a problem with the unrecognized monitor...
Does your monitor show up correctly in the Nvidia X Server Settings?

---

### Post by marteboi on 2012-08-02
I can't tell for sure but i'm fairly certain it doesn't, I can't see anything about my monitor in it

---

### Post by orange2k on 2012-08-02
> **marteboi said:**
> I can't tell for sure but i'm fairly certain it doesn't, I can't see anything about my monitor in it

Maybe try "detect displays" option in the X Server Display Configuration dialog...

Otherwise I'm out of ideas what could be the problem, sorry...:(

---

### Post by marteboi on 2012-08-02
> **orange2k said:**
> Maybe try "detect displays" option in the X Server Display Configuration dialog...

Otherwise I'm out of ideas what could be the problem, sorry...:(

No problem, thanks for trying guy! I've posted this in other forums as well so you're not the only one trying

---

### Post by lukeiamyourfather on 2012-08-02
> **marteboi said:**
> Actually, It claims my driver is too old to to anything with display configuration

That chipset is probably depreciated and no longer supported in the latest drivers. There's a legacy driver in the repositories and if that doesn't work there's also a legacy driver directly from Nvidia. If both of those are not an option the open source driver that ships with Ubuntu should support that chipset.

---

