---
title: "Can anybody reproduce this? Vanishing CJK characters with subpixel smoothing"
date: 2008-01-05
forum: Desktop Environments
---

### Post by jmillikin on 2008-01-05
I noticed that if I select "Subpixel smoothing (LCDs)" in the GNOME "Appearance Preferences", then the character U+FF5E (&#65374;) causes other CJK characters to stop displaying in most GTK+ applications (gnome-terminal is strangly unaffected). I created a simple test text, which when viewed should display like to this:
[img]http://img252.imageshack.us/img252/5585/screenshotok3.png[/img]

With subpixel smoothing enabled, the window looks like this:
[img]http://img106.imageshack.us/img106/9581/screenshot1bc9.png[/img]

Since this is such a strange problem, I'd like to confirm that it's not merely an issue with my personal configuration before submitting it as a bug. Could posters please copy this text into GEdit, toggle subpixel smoothing, and report the results? If somebody else can reproduce this, I will open a bug.

```
|&#65374;|&#26376;|
```

---

### Post by Keith_Beef on 2008-01-06
I entered these characters in gedit and saw the same results with fonts below 14pts. At 14pts, the moon reappears.

If I go into System -> Preferences -> Appearances, and change from sub-pixel smoothing to any of the other three options, then the moon is visible at all font sizes.

Beef.

---

### Post by jmillikin on 2008-01-06
Oh yeah, I forgot you could just paste into GEdit. Here's the direct text, if anybody wants to use that: |&#65374;|&#26376;|

EDIT: [https://bugs.launchpad.net/ubuntu/+bug/180734](https://bugs.launchpad.net/ubuntu/+bug/180734)

---

### Post by Keith_Beef on 2008-01-06
> **jmillikin said:**
> Oh yeah, I forgot you could just paste into GEdit. Here's the direct text, if anybody wants to use that: |&#65374;|&#26376;|

EDIT: [https://bugs.launchpad.net/ubuntu/+bug/180734](https://bugs.launchpad.net/ubuntu/+bug/180734)

Invisible moon in Firefox, even with changing font rendering.

Copy and paste from the thread to gedit works, though, with the same as I described in post #2.

B.

---

