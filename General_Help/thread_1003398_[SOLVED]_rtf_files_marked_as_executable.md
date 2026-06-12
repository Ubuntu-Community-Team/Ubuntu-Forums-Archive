---
title: "[SOLVED] rtf files marked as executable"
date: 2008-12-06
forum: General Help
---

### Post by motoperpetuo on 2008-12-06
most of my .rtf files are marked as executable. that is, if you right-click on them, choose properties, then the permissions tab, the "Allow executing file as a program" check box is selected.

does anyone know why this is, and more importantly, how to automatically remove this flag from all my rtf files? it's annoying, because anytime i double-click on an .rtf in the GUI, i get a dialog asking if i want to display the file or run it as a program. i can remove the flag manually, but i have hundreds of .rtf files, so i'd like to automate the process.

this is in mint 5.0, but it was the same when i was using ubuntu (6.10, i think). also, most of these .rtf files were created in open office, although i think some of them date back to before i transitioned to linux and were created under MS office in windows xp. it doesn't seem to make a difference...ubuntu and mint just seem to think that .rtf files are executables, for some reason.

---

### Post by snova on 2008-12-06
Command to find all files ending in .rtf and remove executable bit:

```
find ~ -name '*.rtf' -exec chmod -x {} \;
```

Replace '~' with a particular directory, else it'll search your entire home directory and take a good long time.

There are more efficient ways to do it, but I don't know how.

---

### Post by motoperpetuo on 2008-12-07
seems to have worked like a charm, also for my .txt files that were executable. thanks!

---

