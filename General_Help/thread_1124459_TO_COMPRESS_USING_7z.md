---
title: "TO COMPRESS USING 7z"
date: 2009-04-13
forum: General Help
---

### Post by Janzeon on 2009-04-13
Hello everyone

i have a lot of movies taking a lot of space on my hard disk i wanted to compress it so i downloaded 7zip but when i try to compress it compresses a 1.36 GB file to 1.34GB but that is not much of a difference can anyone please tell me how to compress it to smaller file sizes like those i have seen on the net they compress 3 GB files to only 94 MB how do they do that anyway thank you in advance.

---

### Post by TheLions on 2009-04-13
you could use kgb archiver

install it with: sudo apt-get install kbg

in terminal run:
kgb -9 (destination/name_of_file).kgb (source/filename or source/*)

-9 is maximum compresion ratio

run kgb to see more options

---

### Post by NoReflex on 2009-04-13
Hello!

Movies are already compressed (except a few formats). If your movie takes up 1.36 GB it's probably a two CD "rip" so it's already compressed.
If you want to reduce the size of your movies you probably need to "resize" them (reduce the resolution) - but this process will affect the image quality.
You could also try to change the format to mkv for example. Anyway all these processes imply lossy (NOT lossless) compression so the image quality will be reduced. 7zip or other archiving formats won't help you here.
7zip (rar, ace) area very good at "text compression".

Best wishes,
NoReflex

---

### Post by defaultusername on 2009-04-13
Janzeon,

> 
sudo apt-get install p7zip


is 7zip's Linux command-line version.

Large hard drives are cheap these days. Consider buying a 160/320/500gB drive to store more files on. Heck, you could easily obtain a tB or more for under $100. My server has a lot of storage space, but I'm always deleting things I never use anymore. If a file hasn't been accessed since the dawn of time, then it probably doesn't deserve an important chunk of your disk.

---

### Post by mb_webguy on 2009-04-13
As others have said, movies are already compressed, so you won't free up much more space by trying to compress them further -- the law of diminishing returns applies.

However, you can install 7zip by installing the p7zip-rar package.  (The actual 7zip package is p7zip-full, but the p7zip-rar package depends on the p7zip-full package and adds rar support.  Installing p7zip-rar gets you the whole enchilada.)

Once this package is installed, you can use Archive Manager to create 7z archives, but it doesn't give you any options to optimize the compression.  The following command in the terminal should produce a 7z archive with a much higher level of compression than the defaults.```
7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on *archive_name* *file_name*
```

---

### Post by Praxicoide on 2009-04-19
I tried performing the command above, and for some weird reason, it began compressing my entire /home directory.

EDIT: Forget it, it works OK now.

---

