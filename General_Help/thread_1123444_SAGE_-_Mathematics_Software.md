---
title: "SAGE - Mathematics Software"
date: 2009-04-12
forum: General Help
---

### Post by rkapadia16 on 2009-04-12
Is SAGE mathematics software any good? How do I install it on Ubuntu 8.10?

---

### Post by zika on 2009-04-12
> **rkapadia16 said:**
> Is SAGE mathematics software any good? How do I install it on Ubuntu 8.10?
very good. as far as I remember, download compressed file and un-compress it at a convenient place. it uses browser as interface. powerful tool! I did not install it yet in JJ but have used it it II ...

---

### Post by rkapadia16 on 2009-04-12
thats's good to hear...so do I just download from the SAGE website and install it? Is there a code I could use in the ubuntu terminal to install it?

---

### Post by zika on 2009-04-12
> **rkapadia16 said:**
> thats's good to hear...so do I just download from the SAGE website and install it? Is there a code I could use in the ubuntu terminal to install it?
no, as far as I rember You just un-compress file You've dl-ed in a convinient directory. then make an alias or shortcut to launch it.
[http://www.sagemath.org/download.html](http://www.sagemath.org/download.html)
> Linux                   [Download Linux binaries]("http://www.sagemath.org/bin/linux/")      
              Usage:        
[LIST=1]
[*]Select the one that suits your setup and extract it in your file-browser by right        clicking "extract" or on the command-line using: tar        xvzf sage...tar.gz.
[*]Run sage by calling the command: sage.
[/LIST]
      
              At the moment there are no distribution-specific packages available

---

### Post by rkapadia16 on 2009-04-13
I've downloaded the SAGE binaries and extracted them into a folder that is located on the desktop.

I don't know how to run sage from the command line. Can anyone help?

---

### Post by 3Miro on 2009-04-13
SAGE is more symbolic oriented, while Octave is more numeric oriented (think of them as being similar to Mathematica and Matlab).

I installed sage once, but I followed the instructions to compile the thing. Getting already compiled binaries (if there are some available) should be easier.

---

### Post by zika on 2009-04-13
> **rkapadia16 said:**
> I've downloaded the SAGE binaries and extracted them into a folder that is located on the desktop.

I don't know how to run sage from the command line. Can anyone help?
```
sh /home/YourUserName/Desktop/TheNameOfDirectoryForSage/sage -notebook
```

---

