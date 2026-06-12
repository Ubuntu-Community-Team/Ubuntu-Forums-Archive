---
title: "Copying files with bad sectors"
date: 2009-02-11
forum: General Help
---

### Post by Metallion on 2009-02-11
I need to backup a huge file (15gb) which has some tiny fault in it and thus shows me the CRC error in windows. It's really important to get a backup of this and the file still works fine so I think it's just some tiny sector that's bad and stopping me from copying the whole thing.

I'm running chkdsk on it right now but I'm afraid that might not help. It's a windows server 2003 box but feel free to give me linux solutions as well. I could just pop in a live cd and run those from there.

Appreciated.

---

### Post by SeanTater on 2009-02-11
I'm not an expert in corrupted files, but I imagine one of these would work:
```
dd if=/path/to/source of=/path/to/dest
```
or
```
rsync /path/to/source /path/to/dest
```

---

### Post by caljohnsmith on 2009-02-11
You could use "dd_rescue" to copy the file; dd_rescue will do its best to read bad sectors, and if it can't, it will skip them and continue to copy the file as well as it can. You can give it a try with:
```
sudo apt-get install ddrescue
sudo dd_rescue /path_to/[COLOR="Blue"]<input file>[/COLOR] /path_to_save/[COLOR="Blue"]<output file>[/COLOR]
```
Let me know how that goes.

---

### Post by Metallion on 2009-02-12
Thank you guys for the suggestions. I came to work today and windows' chkdsk /r that I left running overnight has fixed the problem for me. I will keep that dd_rescue around for the future though! It sounds like exactly the thing I was looking for.

---

