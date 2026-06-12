---
title: "What is the syntax of precise.xml?"
date: 2012-10-21
forum: Desktop Environments
---

### Post by JamesTheAwesomeDude on 2012-10-21
Hey, I wanted to make a custom background, with it rotating between a sunny picture, a morning picture, an evening picture, and a night picture (it's the same picture, with the lighting edited w/ Gimp,) but I'm not quite sure on all the syntax of the precise.xml file used for animated/changing backgrounds.

Mainly, I just want to know the small things, like what unit of time <duration /> uses, and what are all the options for <transition type="XXX" /> are. I already have a template one that I want to use, but I just want to customize some of the fade lengths a bit. (e.g., I want dusk to start earlier, etc.)

---

### Post by mcduck on 2012-10-22
the times are in seconds, in relation to the start time you define at the start of the XML file.

As far as I know only basic fade between images is currently supported.

---

