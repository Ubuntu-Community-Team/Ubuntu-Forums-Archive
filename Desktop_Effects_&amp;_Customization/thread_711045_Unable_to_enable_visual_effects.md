---
title: "Unable to enable visual effects"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by latin_l3oi on 2008-02-29
Hello there, 

I am completely new to Ubuntu, as a matter of fact, I have just managed to get Ubuntu dual boot with WinXP working just then with help from this forum :). 

I would like to enable the Visual Effects but when I go to System -> Preferences -> Appearance and I got to the "Visual Effects" tab "None" is selected by default.

When I try to select "Normal" or "Extra", I get a message that says:

======================================
Enable the Driver?

NVIDIA accelerated graphics driver (latest cards)

This driver is required to fully utilise the 3D potential... etc...
======================================

When I click on "Enable Driver", I get the following message:

==============================
The software source for the package

   nvidia-glx-new

 is not enabled.
==============================

What could I do to enable the driver... and get visual effects working?

Regards,

latin_l3oi

---

### Post by overdrank on 2008-02-29
> **latin_l3oi said:**
> Hello there, 

I am completely new to Ubuntu, as a matter of fact, I have just managed to get Ubuntu dual boot with WinXP working just then with help from this forum :). 

I would like to enable the Visual Effects but when I go to System -> Preferences -> Appearance and I got to the "Visual Effects" tab "None" is selected by default.

When I try to select "Normal" or "Extra", I get a message that says:

======================================
Enable the Driver?

NVIDIA accelerated graphics driver (latest cards)

This driver is required to fully utilise the 3D potential... etc...
======================================

When I click on "Enable Driver", I get the following message:

==============================
The software source for the package

   nvidia-glx-new

 is not enabled.
==============================

What could I do to enable the driver... and get visual effects working?

Regards,

latin_l3oi

HI have you tried to install the restricted drivers located under system, administration.

---

### Post by latin_l3oi on 2008-02-29
Hi,

Yep, I've tried enabling the driver via Restricted Drivers Manager but I get the same message:

> Enable the Driver?

NVIDIA accelerated graphics driver (latest cards).. etc...


and then I click on "Enable Driver" and I get the following message:

> The software source for the package

   nvidia-glx-new

 is not enabled.

Then I can just click on "Close".

---

### Post by latin_l3oi on 2008-02-29
Hi there,

I managed to get it working by:

> Open a terminal and type
Code:

sudo aptitude install ubuntu-restricted-extras



And...

> go to

system > administration > software sources

and enable everything except source code and cd

then run

Code:

sudo apt-get update



---

