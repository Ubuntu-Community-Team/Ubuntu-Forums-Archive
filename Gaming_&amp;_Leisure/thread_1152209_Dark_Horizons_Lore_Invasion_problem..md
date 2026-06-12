---
title: "Dark Horizons: Lore Invasion problem."
date: 2009-05-07
forum: Gaming &amp; Leisure
---

### Post by Vel1971 on 2009-05-07
I thought I would give this game a try. Tried installing it from this guide: [http://gaming.gwos.org/doku.php/guides:32bit:dark_horizons_lore_invasion]("http://gaming.gwos.org/doku.php/guides:32bit:dark_horizons_lore_invasion")

I am running Ubuntu 8.10 32 bit. 

This is the problem I am having. I guess it is something with the checksum. Does that mean the download file has changed? The file name I downloaded is dhli_v2_0_2.sh.bin.
```
jon@jon-desktop:~/Desktop$ chmod +x dhli_v2_0_2.sh.bin
jon@jon-desktop:~/Desktop$ linux32 sh dhli_v2_0_2.sh.binVerifying archive integrity
...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 2852045568 is different from 609708321

```

Thank you for any help you can give.:)

---

### Post by wolfyking2 on 2009-05-07
I have the same problem...except the first set of numbers in mine is 716818224.  I really wanna try this game, so can anyone help?

---

### Post by Naiki Makuri on 2009-05-08
The only way I could get it to work was to hexedit . You have to add +266 after tail or something. It was a while ago, so I cant completely remember.

---

### Post by Vel1971 on 2009-05-08
> **Naiki Makuri said:**
> The only way I could get it to work was to hexedit . You have to add +266 after tail or something. It was a while ago, so I cant completely remember.

Thank You! That put me on the right track. A little more digging around lead me to this thread. [http://ubuntuforums.org/showthread.php?t=757104]("http://ubuntuforums.org/showthread.php?t=757104")

That fixed the problem. Just had to edit the file and change "tail +266" to "tail -n +266". It is only in the file twice, so it did not take that long.:)

---

