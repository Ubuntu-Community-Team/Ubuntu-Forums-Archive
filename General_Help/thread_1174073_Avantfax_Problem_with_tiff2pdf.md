---
title: "Avantfax Problem with tiff2pdf"
date: 2009-05-30
forum: General Help
---

### Post by Aaronsgwc on 2009-05-30
I just installed Hylafax on Ubuntu Server 9.04, it seems to be working fine. Installed Avantfax 2.3.0 as per a Debian tutorial and it works great except that I keep getting an error about tiff files being corrupted. 

I can manually convert the same tiff files to pdf using the command sudo tiff2pdf fax.tif -o fax.pdf. Works great.

It seems to be a file permissions problem, not actual corrupted tiff files. Has anyone ran into this before and were you able to fix it?

-Aaron Evans

---

### Post by felixherve on 2009-07-23
I had the same problem and managed to get it to work by changing a line in the bin/faxrcvd.php

I've commented out the line that tries to do the conversion (line 87) and replaced it with an exec() that calls for tiff2pdf


```
// create pdf in new dir
//tiff2pdf ($faxfile, $pdffile);
echo exec("tiff2pdf $faxfile -o $pdffile");

```

which seems to fix things.

---

