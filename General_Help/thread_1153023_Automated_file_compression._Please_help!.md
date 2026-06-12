---
title: "Automated file compression. Please help!"
date: 2009-05-08
forum: General Help
---

### Post by macroshaft on 2009-05-08
A bit of an odd one here but I'm hoping someone will know the answer.

I have about 5,000 files, half with one extension, half with another. They need pairing up and compressing into zip files. This will take me weeks by hand and I figure their must be a way of automating this. The file name for each in the pair is identical but the extensions differ. Does anyone have any ideas for an app or script to do this?

Thanks

---

### Post by kanikilu on 2009-05-08
Here's one way to do it:

Open terminal, cd to the top of the directory tree that you want to search, in my example, I'm searching through everything in my "Documents" directory and creating a zip file of all files with the extension "txt".

```
cd ~/Documents
find . -type f -name "*.txt" -print | zip txt-files -@
```

---

### Post by macroshaft on 2009-05-08
But I don't want to create a zip file of all mp3s or all cdgs. I want to create 2,500 zip files each containing one mp3 and one cdg.

---

### Post by sisco311 on 2009-05-08
> **macroshaft said:**
> But I don't want to create a zip file of all mp3s or all cdgs. I want to create 2,500 zip files each containing one mp3 and one cdg.

try something like:
```
ls *.mp3 | sed "s/\.mp3$//" | while read file; do zip "$file" "$file".mp3 "$file".cdg; done
```

---

### Post by macroshaft on 2009-05-08
Thanks for that, looks like it'll do nicely. The only problem is as your command works all from one directory it would create a zip when it reads the mp3 and then again for the cdg, so I'll copy the cdg's into a seperate folder for this.

---

### Post by cgkades on 2009-05-08
you get it working yet? that script i sent you, i think you just need an if then statement to stop it from doing the ./ and ../ dirs though it may just ignore it anyways

---

### Post by leoave on 2009-08-12
> **sisco311 said:**
> try something like:
```
ls *.mp3 | sed "s/\.mp3$//" | while read file; do zip "$file" "$file".mp3 "$file".cdg; done
```

hey sisco311, thank's, it did work for me, I had to run this on each folder, but copy/paste is "pecata minuta" (actually did Shift+Insert then Enter on each folder) so easy.

You are master of bash !!

Muchas gracias.

---

