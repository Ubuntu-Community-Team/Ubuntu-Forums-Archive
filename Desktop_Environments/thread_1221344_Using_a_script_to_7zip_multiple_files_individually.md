---
title: "Using a script to 7zip multiple files individually"
date: 2009-07-23
forum: Desktop Environments
---

### Post by mrmooge88 on 2009-07-23
Yesterday I was needing to use 7zip to pack multiple files in the same directory to multiple separate compressed archives. 

I was wanting to take some files from the same directory: File1, File2, File3, ... and turn them into: File1.7z, File2.7z ... (The actual files are not sequential)

Since I was using the flag for maximum compression it was taking awhile for each file. Not wanting to babysit the computer I ended up writing a really dirty bash script to compress them individually. The script kind of worked but had a few errors in it because I typed everything out. Today I am trying to figure out how I could have wrote it better. All the files had the same extension and and I wanted each compressed file to have the same name as the original. Any tips on how it could have been improved? This was a one time use script.

date >> ~/Desktop/7z.log
cd Path/to/directory
7z a -t7z -mx9 ./File1.7z ./File1 >> ~/Desktop/7z.log
7z a -t7z -mx9 ./File2.7z ./File2 >> ~/Desktop/7z.log

---

### Post by Zorael on 2009-07-23
My bash-fu is weak, but;
```
for X in *****;
do
  7z a -t7z -mx9 $X.7z $X >> ~/Desktop/7z.log
done
```
Of course, if you need to do better file selection than just *, you can do something like;
```
for X in **$(ls | grep File | grep -v .log | grep -v .nfo)**;
do
  7z a -t7z -mx9 $X.7z $X >> ~/Desktop/7z.log
done
```

---

### Post by mike_tyrell on 2010-02-10
thank u

---

### Post by mister_playboy on 2010-02-10
I had been wondering how to set this up... thanks! :)

---

### Post by talbain on 2010-08-27
This doesn't seem to work if filenames include spaces, how could i achieve this regardless?
Is there a GUI solution to this? I think the "Compress..." context menu dialog should have this option, as well as "Delete source files after compression".

---

### Post by mrmooge88 on 2010-08-27
There should be quotes around the variables. So it should be something like

> 
for X in *;
do
  7z a -t7z -mx9 "$X".7z "$X" >> ~/Desktop/7z.log
done


All I did was change all the instances of:**$X** to **"$X"**

---

