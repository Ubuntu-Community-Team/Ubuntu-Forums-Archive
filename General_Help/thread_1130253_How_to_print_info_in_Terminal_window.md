---
title: "How to print info in Terminal window?"
date: 2009-04-19
forum: General Help
---

### Post by JEBB on 2009-04-19
Using this terminal command:   lspci -vnn  
I got the hardware profile of my new Dell Mini 9 to display in the terminal window.  It's rather long.  I would like to know how to print it to a PDF file.  Thanks

---

### Post by Titan8990 on 2009-04-19
You can easily direct the output of a command to a file using the > symbol. Example that you are looking for:


```
lspci -vnn > FILE.txt
```


The output of the command will go to the file named FILE.txt or whatever else you decide to name it in your current directory.

---

### Post by JEBB on 2009-04-19
Titan:  
Thanks.  Where, other than asking here, might I have found that information?

---

### Post by oldos2er on 2009-04-19
> **Titan8990 said:**
> You can easily direct the output of a command to a file using the > symbol. Example that you are looking for:


```
lspci -vnn > FILE.txt
```
The output of the command will go to the file named FILE.txt or whatever else you decide to name it in your current directory.

 Or do it all in one command:
```
lspci -vnn > FILE.txt && cat FILE.txt | lp
```

---

