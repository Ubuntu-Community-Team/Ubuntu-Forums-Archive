---
title: "i cant extract the rar files (ubuntu 9.4)"
date: 2009-05-23
forum: General Help
---

### Post by devananda on 2009-05-23
hello friends,,,can youu help me with this question.

how can i extract and open the rar files i download from a-mule,,archive manager doesnt seem to support this type of archive.
thank you for your help

---

### Post by Legace on 2009-05-23
Open Terminal, and type in the following:
```
sudo apt-get install rar
```

---

### Post by DeMus on 2009-05-23
> **Legace said:**
> Open Terminal, and type in the following:
```
sudo apt-get install rar
```

The program rar is for making a rar file. What the OP needs is unrar.
Open synaptic and search for unrar. You will find 2 versions, the free and the non-free version.
Install the non-free version. It will depend on another program, just accept that. After that archive manager will extract rar-files.

---

### Post by ActiveFrost on 2009-05-23
Open your terminal and execute this command :
```
sudo apt-get install unrar
```
Once it's installed, Archive Manager will be able to open .rar and similar files ;)

---

### Post by Legace on 2009-05-23
> **DeMus said:**
> The program rar is for making a rar file. What the OP needs is unrar..

Yeah, I messed up :)
Thanks for fixing.

---

### Post by mellowd on 2009-05-23
though if you want to be funky, get unrar and then do it via the terminal:

unrar e archive.rar

---

### Post by hatalar205 on 2009-05-23
Install "7zip full" and never have any problems with .rar, .zip. or something like that.

---

### Post by craig.o on 2009-05-26
> **DeMus said:**
> The program rar is for making a rar file. What the OP needs is unrar.
Open synaptic and search for unrar. You will find 2 versions, the free and the non-free version.
Install the non-free version. It will depend on another program, just accept that. After that archive manager will extract rar-files.

Thank you DeMus;

I had this very problem earlier today, searched the forums and voila!  By the way, it was a good idea to suggest synaptic... That way, 'apt-get update' is automagically run prior to any other operation.  

regards,
-Craig

---

