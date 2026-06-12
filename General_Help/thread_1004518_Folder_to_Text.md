---
title: "Folder to Text"
date: 2008-12-07
forum: General Help
---

### Post by stonedparadox on 2008-12-07
i have ubuntu 8.10

basically i have a Folder full to the brim with movies 
and i basically now what a hard copy on paper

so i was wondering is there software that allows you to do this?
i know in terminal theres something u can do but i can not longer find it 
and iv been searching

so basically
i was wondering is it possible to copy the entire contents of a folder to a text file from A to Z and so on?

muchly thanks

---

### Post by howefield on 2008-12-07
There's probably a neater way, but you could use the ls command in terminal to get the listing and copy/paste to your text editor.

See man ls for  helpfile.

---

### Post by __Ryan__ on 2008-12-07
Try this in a terminal:

```
ls movie_dir/ > movie_list.txt
```

for more information:

```
ls -lh movie_dir/ > movie_list.txt
```

---

### Post by stonedparadox on 2008-12-07
cheers ill try that 

thank you

---

