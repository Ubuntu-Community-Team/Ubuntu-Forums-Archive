---
title: "Poor picture quality in Firefox"
date: 2009-01-26
forum: General Help
---

### Post by fdhealy4 on 2009-01-26
Online picture quality in Firefox is poor. The line are slightly jagged and the resolution seems poor. Pictures viewed outside of the browser are fine. Using 8.10 and have the latest video driver. Firefox pictures are good in XP and OSX.

---

### Post by mcduck on 2009-01-26
That sounds quite strange. Could you provide screenshots of the same page in Ubuntu & in Windows/OSX?

---

### Post by slimx3m on 2009-01-26
that is really weird.  is the screen resolution the same in both OS's?

---

### Post by AliTabuger7 on 2009-01-26
The problem is almost certainly because you have the zoom level set to something other than 100%.

When this happens on windows (and perhaps os x), a higher quality image resizing is used. This MIGHT (haven't checked) be able t be changed in about:config.

This is often reported, and this is for some reason not considered a bug...

---

### Post by clockworkpc on 2010-07-29
Did you ever find out whether Firefox in Linux does or doesn't use a higher quality image when resizing?  If so, do you know how to ensure that it does?

---

### Post by Mecallie on 2010-11-13
I just wanted to reply here since I had the exact same problem up until just now. Firefox images looked as if they came from a compressing proxy such as some mobile phone carriers use to reduce image size.

I came across a post indicating that the imagezoom.defaultGlobalZoom integer was set to 90. Meaning the zoom level was always at 90%.

I however did not have this integer in about:config at all. After creating the integer and setting it to 100 my problem was solved!

Hope this helps you as well, very annoying problem and I really do not understand why this is not considered a bug!

---

