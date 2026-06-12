---
title: "[SOLVED] ATI Radeon and glxinfo errors"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by sk87 on 2007-10-10
Just done a fresh install of feisty at the weekend after a year of going in and out of linux but now on a permanent set up.

Every going really well except for the dreaded ATI Radeon X700 graphics card when trying to  do desktop effects.

I was follwing a guide for me to download an open driver (XGL?) for it but failed at step one when i typed in glxinfo | grep direct
and it returned this.

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17


it should be telling me if the set up is capable direct rendering.

I have searched but have no clues how to solve this

cheers

---

### Post by floke on 2007-10-10
You might want to try gutsy with the restricted ATI driver and xgl-server - it should set most of this stuff up for you.

---

### Post by sk87 on 2007-10-10
All solved I did what you suggested and it works brilliantly.

Can't thank you enough

---

