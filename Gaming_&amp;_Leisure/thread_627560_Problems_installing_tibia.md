---
title: "Problems installing tibia"
date: 2007-11-30
forum: Gaming &amp; Leisure
---

### Post by tabithaboof on 2007-11-30
I have downloaded, extracted and CHMODed my tibia files but when I try to run the "Tibia" file to start the game I get an error message in Terminal.

```
david@david-laptop:~/games/Tibia$ ./Tibia
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  58
  Current serial number in output stream:  59

```

I have a vauge feeling this might be something to do with graphics drives but I am pretty new to linux gaming and dont know where to go from here.

Any help much appreciated!

---

### Post by Vadi on 2007-11-30
Hmm!

Where did you get the same?

I downloaded "tibia800.tgz" off softpedia.com, and the Tibia file was already set to execute as a program properly.

Although... I get the same error as you. Hah.

---

### Post by Vadi on 2007-11-30
Yeah man it looks like its our drivers, and we're out of luck. Us peeps using the open-source "radeon" driver and the intel people can't get it working, and the only way is via wine.

---

### Post by enricoluigi on 2008-02-22
> **tabithaboof said:**
> I have downloaded, extracted and CHMODed my tibia files but when I try to run the "Tibia" file to start the game I get an error message in Terminal.

```
david@david-laptop:~/games/Tibia$ ./Tibia
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  58
  Current serial number in output stream:  59

```

I have a vauge feeling this might be something to do with graphics drives but I am pretty new to linux gaming and dont know where to go from here.

Any help much appreciated!
i can help you with the driver's instalation

send-me an mp and tell-me what is your video board

Sorry for the bad english

---

### Post by Stratok on 2008-04-12
> **enricoluigi said:**
> i can help you with the driver's instalation

send-me an mp and tell-me what is your video board

Sorry for the bad english


same problem, exactly same error in terminal... could you help me 2 please?, how do i know which grafic card do i have?

---

### Post by Bookman on 2008-05-05
turn off compiz! and 3d effects under hardy it will run!

---

### Post by napolperro on 2008-06-08
I tried turning off compiz and 3d effects... but it doesn't make a difference :(

```
xx@xx-desktop:~/Tibia$ ./Tibia
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  58
  Current serial number in output stream:  59
xx@xx-desktop:~/Tibia$ 
```

---

