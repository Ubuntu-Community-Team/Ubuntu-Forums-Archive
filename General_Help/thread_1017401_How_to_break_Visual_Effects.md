---
title: "How to break Visual Effects"
date: 2008-12-21
forum: General Help
---

### Post by aeosynth on 2008-12-21
I'm playing around in a live CD (8.10) since I need to do some partitioning, and I messed around with metacity and compiz because I wanted to see how they worked with AWN.

So I went to Appearance -> Visual Effects, set it to 'None', then opened up gconf-editor and navigated to /apps/metacity/general, and checked the box compositing_manager. Ok, now let's put everything back. I uncheck compositing_manager, go back to Visual Effects and set it to 'Normal'. Whoops - 'Desktop effects could not be enabled'.

---

### Post by Vadi on 2008-12-21
Well, that's why the option for metacity compositing it hidden away.

Do "compiz --replace" in the terminal, what does it tell you?

---

### Post by aeosynth on 2008-12-22
Checking for Xgl: not present.
Detected PCI ID for VGA: Flags: bus master, VGA palette snoop, 66MHZ, medium devsel, latency 64
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

---

### Post by Vadi on 2008-12-22
Go to System&#8594;Adminstration&#8594;Hardware Drivers. Do you have a recommended driver active?

---

