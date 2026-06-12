---
title: "Touch/Mouse -pad stopped working...?"
date: 2009-05-18
forum: General Help
---

### Post by infinitelink on 2009-05-18
Anyone with ideas why a touchpad would just suddenly cease functioning on a laptop running xubuntu, yet better, how to diagnose, and how to fix it? 

I also just clicked the "Check if Already Posted" link in the posting options of this forum which gave me this (but for ubuntu), [http://ubuntuforums.org/showthread.php?t=1136202&highlight=Touch%2FMouse+-pad+stopped+working...%3F](http://ubuntuforums.org/showthread.php?t=1136202&highlight=Touch%2FMouse+-pad+stopped+working...%3F)

Is/how-is that applicable to Xubuntu? 

P.s. I haven't edited the fdi as that poster said he had.

My file, /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
, looks like, 

> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

And using program 'xev' doesn't show that any input is being detected from the touchpad at all.

---

### Post by BslBryan on 2009-05-18
Hello, infinitelink. :-)

What model laptop are you using?  More specifically, is it an Hp?

---

### Post by infinitelink on 2009-05-18
> **BslBryan said:**
> Hello, infinitelink. :-)

What model laptop are you using?  More specifically, is it an Hp?

HELLLOOooo! Back at ya.

Why, yes, it is...that you'd touch on that, I'm not sure if I want to be worried, or assuaged! : ) It's an HP 2510p: I bought this model specifically for having mostly (I heard) standard components that usually work well with Linux (again, anecdotal, and besides the Touchpad suddenly ceasing to function, everything else has been amazingly spiffy).

---

### Post by infinitelink on 2009-05-18
Okay, figured it out: my lappy has a sensor-strip on which there's a button for en/dis -abling the touchpad; when I close the lid of it (for going into suspend) that strip is touched; I realized that button was tripped, and I just tapped it firmly enough that the touchpad was re-enabled! : D

---

### Post by BslBryan on 2009-05-22
Yep!  That's exactly what happened to my mom's laptop, and she had no clue why her touchpad wasn't working. :lol:

---

### Post by oursin on 2011-10-24
Thank you so much!!!!!!!!!!

---

