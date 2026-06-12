---
title: "No Bios VT-option in latest Bios on Dell XPS m1530"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Carroarmato0 on 2009-01-15
I'd like to use the VT-support on the processor, but for some reason Dell removed that option from the bios so it's default is set to off.

Now Dell had added that option in an older version of the bios... the A08 as far as google could tell.

Yet in the latest version (A12 at the moment) they removed that.

My question is why if anyone knows, and if they'll be adding it back soon.

---

### Post by NTolerance on 2009-01-15
Any particular reason to need Intel VT?  The Virtualbox documentation states that performance gains are negligible.  Not sure about other VM software though.

---

### Post by eric.frederich on 2009-07-19
> **NTolerance said:**
> Any particular reason to need Intel VT?  The Virtualbox documentation states that performance gains are negligible.  Not sure about other VM software though.

VirtualBox now needs it to support multiple processors in the guest OS.

---

