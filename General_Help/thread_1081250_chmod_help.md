---
title: "chmod help"
date: 2009-02-26
forum: General Help
---

### Post by Justbill on 2009-02-26
I recently switched back to Ubuntu (8.10) after a brief,and less than stellar experience with "Ultimate Edition".
Obviously, before I installed Intrepid, I saved the different documents, pictures, etc. from my home and my desktop to a CD, and after my new installation, moved them into my new "Home". 
Which brings me to my question, I know how to unlock the folders with the chmod command, but then I have to go into the folder and unlock the contents, or any sub-folders, and then their contents. Is there one chmod command that will unlock the folder and its contents?

Thanks in advance

Bill

---

### Post by taurus on 2009-02-26
```
sudo chmod -R 755 top_directory
```

---

### Post by glotz on 2009-02-26
Answers to all the questions you might have about chmod are on the manual page
```
man chmod
```

---

### Post by Justbill on 2009-02-26
Thanks!

---

### Post by Slim Odds on 2009-02-26
> **taurus said:**
> ```
sudo chmod -R 755 top_directory
```

I think that it makes more sense to show people the "mnemonic" way to do this. The octal numbers have little meaning to the human mind.

How about:
```
sudo chmod -R u+w top_directory
```Which means: give the User Write permission.

---

