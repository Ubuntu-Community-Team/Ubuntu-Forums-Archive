---
title: "Black backgrounds and color issues after logging out KDE"
date: 2012-04-22
forum: Desktop Environments
---

### Post by dzchimp on 2012-04-22
I'm on Kubuntu 11.10. Everytime I logout, backgrounds which are supposed to be white turn black, rendering it impossible to read text. Examples are the addressbar of Firefox and Chromium (See attached screenshot). I'm at a loss as to understand why this is happening.

[IMG]http://droidzone.in/images/screenshots/Selection_002.jpeg[/IMG]

This is what Filezilla looks like:
[IMG]http://droidzone.in/images/screenshots/Selection_003.jpeg[/IMG]

---

### Post by dzchimp on 2012-04-22
I had forgotten to attach screenshots. I did it now.

---

### Post by schnelle on 2012-04-22
I don't know why this happens but maybe I have a solution for the problem :)

```
kdesudo kate /etc/kde4/kdm/kdmrc

```

When kdmrc text file opens change line```
#TerminateServer=true
``` to ```
TerminateServer=true
```

Then reboot your system for the change to take effect and test :)

Hope it helps :D

---

### Post by Erik1984 on 2012-04-22
Weird. Did you install another theme (doesn't look like it judging from the screenshots) or made adjustments to some appearance settings?

---

### Post by dzchimp on 2012-04-23
> **Euroman said:**
> Weird. Did you install another theme (doesn't look like it judging from the screenshots) or made adjustments to some appearance settings?

No I havent installed any themes. Still using Plasma Desktop. I dont remember meddling with many settings either.

> **schnelle said:**
> I don't know why this happens but maybe I have a solution for the problem :)


It works! Thank you!

---

