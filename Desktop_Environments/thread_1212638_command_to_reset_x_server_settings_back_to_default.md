---
title: "command to reset x server settings back to default?"
date: 2009-07-13
forum: Desktop Environments
---

### Post by cptjaben on 2009-07-13
I installed compiz and enabled maximum effects successfully on a laptop, but after restarting it says X server failed and that it's unable to start GDM. Does anyone know the command to reset x server settings back to the defaults?

Thanks

---

### Post by x33a on 2009-07-14
try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cptjaben on 2009-07-14
I'm trying to boot in recovery mode and use the command prompt to reset the graphics settings, but it doesn't appear to be doing anything and still isn't booting up to GDM. Anyone have an alternate method for resetting graphics settins. using the recovery tool's 'xfix' also returns the same result. Thanks

---

