---
title: "kpdf fails to print filaneme containing exclamation mark"
date: 2007-11-27
forum: Desktop Environments
---

### Post by barna on 2007-11-27
Hi,
I have looked at a PDF document from the web in kpdf, and then tried to print it. It failed, with the error message:

```

A print error occurred. Error message received from system:

cupsdoprint -P '3-1021-HP' -J '16!Maschinenschraubstoecke.pdf' -H '/var/run/cups/cups.sock:631' -U 'barna' -o ' copies=1 orientation-requested=3' '/tmp/kde-barna/kpdfKJyata.ps' : execution failed with message:

Maschinenschraubstoecke.pdf: Event not found

```

I guess that the reason is that the filename contains an exclamation mark (well, why does somebody put an exclamation mark into the filename? but this is not my fault, this was a catalogue of a company)

Daniel

---

