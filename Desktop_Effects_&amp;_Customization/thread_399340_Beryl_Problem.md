---
title: "Beryl Problem"
date: 2007-04-02
forum: Desktop Effects &amp; Customization
---

### Post by benivilch on 2007-04-02
when I select the "Beryl" in "Select window manager" at beryl manager nothing happen and i saw this in my terminal... can anyone help me about this... Im new at linux and beryl... sorry my english is poor.. thankx in advance..



benivilch@benivilch-desktop:~$ Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager. 
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by Majorix on 2007-04-02
Do you have the libxcomposite1 package installed? Its in the repos...

---

### Post by benivilch on 2007-04-02
Im sorry but I have no idea.. How would I know if libxcomposite1 package is installed in my system?

---

### Post by Majorix on 2007-04-02
Oh wait do you have ATI graphics card? If thats the case beryl will have problems with that and give errors like the one you received :(

---

