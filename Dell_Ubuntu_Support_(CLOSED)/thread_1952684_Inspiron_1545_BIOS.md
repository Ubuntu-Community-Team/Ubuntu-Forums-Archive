---
title: "Inspiron 1545 BIOS"
date: 2012-04-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by benwalburn on 2012-04-04
I am trying to update my BIOS to A14 from A02. I've followed several guides to update it but I must be doing something wrong.

I'm at a point where I'm supposed to run "update_firmware" to update the bios but I get this output:

```
Running system inventory...

Searching storage directory for available BIOS updates...
Checking System BIOS for Inspiron 1545 - A02
	Did not find a newer package to install that meets all installation checks.

This system does not appear to have any updates available.
No action necessary.

```

According to that, I'm at the current version for my model, but according to dell, I'm several versions behind. What is the current method for updating my bios? I am on Ubuntu 11.10

---

### Post by mikewhatever on 2012-04-07
Don't think you've done anything wrong. The BIOS repository provided by Dell doesn't seem to have the latest version for your machine, that's all.

Using FreeDos is a popular method, but if that doesn't work, you'll probably have to install Windows.
Hint: There is a free preview of W8 available.

---

