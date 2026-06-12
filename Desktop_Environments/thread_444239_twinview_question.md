---
title: "twinview question"
date: 2007-05-15
forum: Desktop Environments
---

### Post by TTime on 2007-05-15
Hi all

I have a gforce4 mx440 card. The driver installation went flawlessly. I have acess to Nvidia x server and have twinview active , currently set to clone - with the same desktop showing on a LCD and on a plasma.

What i'm looking to achieve is play movies only to the plasma while still being able to access and work on the desktop via the LCD. Is this possible with this type of video card ? 

I have searched hundreds of pages to get as far as I am with the setup of this card - currently I'm brain dead and am kindly looking for some assistance from you Linux guru's.

thanks

---

### Post by starfry on 2007-05-15
Hi, yes you can do this. How are you watching movies? You need to tell your movie player software to use the relevant display.

I run mythtv and I have told it which display to run my DVDs on. There's an option in the frontend setup screens.

---

### Post by TTime on 2007-05-16
I've been using Totem movie player.

I have down loaded Mythtv front end and backend , but where in the settings is where you tell it which monitor to play to ? Mythtv is a pretty full on program - very confusing - need more help please

---

### Post by starfry on 2007-05-19
In the MythTV front end, do "Utilities/Setup", then "Setup", then "Appearance". Press "Next" once to get to the second screen and at the top you will see "Xinerama screen". It will probably be set to zero. Set this to 1 to use your other display.

---

