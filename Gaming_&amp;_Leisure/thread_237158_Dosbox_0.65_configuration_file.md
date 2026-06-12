---
title: "Dosbox 0.65 configuration file"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by jonboy99 on 2006-08-15
Hi, 
Am running dosbox on kubuntu dapper.  Followed the instructions here

[http://dosbox.sourceforge.net/wiki/index.php?page=FAQ%2FI+would+like+to+change]("http://dosbox.sourceforge.net/wiki/index.php?page=FAQ%2FI+would+like+to+change")

but can't find the conf file that should have been made, with the locate or whereis command.
The wiki says this should be in the same folder as the dosbox executable, but I suspect this only holds true for windows installations - my dosbox executable is in /usr/local/bin and there's no other files in there.

Help!

Jon

[edit]  fixed thanks to replies, ta all!  :-D

---

### Post by h00s on 2006-08-15
Start dosbox from home directory and in dosbox type:
```
config -writeconf dosbox.conf
```
Current dosbox config will be written to home directory.

---

### Post by DoktorSeven on 2006-08-15
It's likely in the same directory you launched DOSbox from; if you ran it from a launch menu, it's probably in your home directory **/home/[your username]/**.

---

### Post by graigsmith on 2006-08-15
you can specify your own config file thru the command line, or in the shortcut icon.

dosbox -conf default.conf

---

### Post by aaslun on 2010-11-05
You will find the dosbox configuration file in your home directory:

/home/[username]/.dosbox/

To edit it, open an xterm window (ALT+F2 and then type: xterm)
Then type:

sudo gedit ~/.dosbox/dosbox-0.65.conf

Enter your sudo-password if prompted.
Hope this helps!

---

### Post by wingnux on 2010-11-05
Talk about necromancy! Why would you resurrect a thread from 2006??

---

### Post by Quadunit404 on 2010-11-05
> **wingnux said:**
> Talk about necromancy! Why would you resurrect a thread from 2006??

This. Also, this:

> **aaslun said:**
> **sudo** gedit ~/.dosbox/dosbox-0.65.conf
isn't necessary, because you're editing a file in your home directory, which, under the UNIX security model, you have complete access to, thus making "sudo" unneeded. Sudo is only necessary if you are editing or doing something that requires permissions **outside** of your home.

May someone lock this thread to prevent further bumping, please?

---

### Post by Perfect Storm on 2010-11-05
Thread closed.

---

