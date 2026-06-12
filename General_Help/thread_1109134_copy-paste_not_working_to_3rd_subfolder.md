---
title: "copy-paste not working to 3rd subfolder?"
date: 2009-03-28
forum: General Help
---

### Post by attilab on 2009-03-28
testing, can't make it work
the shared Data drive is a (second) Fat32 partition for migrating things-communication there and back between XP (first NTFS partition) and ubuntu (third and forth partition).
I can copy-paste my test files from
/home/attilab/Documents to:
- /media/DATA
- /media/DATA/How To and What To Do
and can't to the 3rd subfolder:
- /media/DATA/How To and What To Do/linux staff
what is a problem? actually I know what is my problem, but what to do to make it work?

---

### Post by SuperSonic4 on 2009-03-28
Fat32 doesn't support file transfers bigger than 4GiB so you may want to check out the size. Does the third subfolder exist? If not make the folder and copy

---

### Post by attilab on 2009-03-28
1.) yes, subfolders exists, I've made the subfolders in XP, there are more sub sub folders below,
I can read my files from it but I can't paste to it in ubuntu, to that third level and below.
2.) yes, Fat32 you could *force* file size whatever you want if you know how to do that (in XP) 
3.) XP does sometimes (I know why), *changes the attributes* to *read only* or *archive only* so you can not re-save the files but have to save as. Wondering if ubuntu doing something like that? called *permissions*,
4.) also right now these my files are smaler sizes (below 2-3Mb), these are my notes "how to do things in ubuntu" want to collect them to a shared place whichever OS I am logged in

---

