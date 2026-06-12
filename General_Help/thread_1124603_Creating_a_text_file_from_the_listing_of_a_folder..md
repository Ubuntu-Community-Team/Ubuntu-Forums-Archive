---
title: "Creating a text file from the listing of a folder."
date: 2009-04-13
forum: General Help
---

### Post by yogiman_uk on 2009-04-13
Hi

Under DOS I used to be able to create a text file which contained directory listing of a particular folder and its sub folders. The command I used to use is:-

dir *.ext /s >dirlist.txt

Can any one tell me if there is an equivalent linux command or a Gnome tool that will allow me to generate the same file?

Thanks for any help.

Regards


Yogiman!

---

### Post by Elegia on 2009-04-13
Hmm, I'm not sure how you'd get the subdirectories, but the command 

ls -d */ | cat > directories.txt

should print the directories of the active folder to the file 'directories.txt'.

Edit:  'ls -Rl | egrep './d*' | cat > directories.txt' (without the quotes) also shows the subdirectories.

---

### Post by Copernicus1234 on 2009-04-13
find /home/user -exec ls -laR {} \; > mydirfile

Type "man find" for lots of other options to find. Replace /home/user with the path you want to start the search in.

---

### Post by yogiman_uk on 2009-04-13
Thanks for the feedback people. I really appreciate your help.

I will check out both of these and experiment.

Again thank you very much!

Regards


Yogiman!

---

### Post by John Cheng on 2009-04-13
You can use the -R option of ls to list subdirectories.

```
ls -R
```

---

### Post by yogiman_uk on 2009-04-13
Thanks John! :)

---

