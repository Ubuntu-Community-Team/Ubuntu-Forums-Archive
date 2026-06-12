---
title: "Linux Tar usage question"
date: 2009-01-12
forum: General Help
---

### Post by oaxacamatt1 on 2009-01-12
I have a question on 'tar' usage.

I have a dozen tarballs, (*.tar.gz) in these files is 5-10 text files.  These text files do not have an extension, not that it really matters, but I would like to add (.txt) to each.  

What I would like to do is put all these text files uncompressed into one big file or folder with one 'tar' command.  I looked over the man page and the corresponding website but I am still a little confused.

Any help?

---

### Post by Taidgh on 2009-01-12
What's the point of tar if you want them uncompressed? Wouldn't a directory do it?

---

### Post by electrogeist on 2009-01-12
put all your gzipped tarballs in one folder by themselves, and create a destination folder

tar -zxvf * DESTINATION

cd DESTINATION

for file in *; do mv $file $file.txt; done

---

