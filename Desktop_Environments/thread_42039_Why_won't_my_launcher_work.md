---
title: "Why won't my launcher work?"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-15
I want an icon to UT2k4 on my desktop. The exe file is called ut2004-bin, and it is located under the System folder of the UT2k4 directory. If I make a "link" to it and click the link, it works. If I then move the link to a location such as my desktop, nothing happens.

I've made a launcher. I copied the install-created Doom3 launcher on my desktop. The only thing different is the directory. Nothing. Won't do anything. Why can't I get a UT2k4 icon on my desktop that works??

---

### Post by rachii on 2005-06-15
what if you made the link from ~/desktop?   instead of making it (and it works) then moving it (broken)?

rather...how are you making the link?

---

### Post by wylfing on 2005-06-15
The reason the link doesn't work is because following an executable symlink doesn't change your working directory. The UT executable wants to run things that are "local," stupidly expecting that the working directory is the one the program was run from. Neverwinter is the same way.

I solved this by creating a script like so:
```
#!/bin/sh

workdir=/home/sparky/games/nwn

cd $workdir
nwn

```
Change $workdir to point to the directory where the UT executable lives, and replace 'nwn' with 'ut-2004.bin'. Then make a launcher that runs the script. Don't forget to make the script executable!

HTH

---

### Post by Curlydave on 2005-06-16
[QUOTE=wylfing]The reason the link doesn't work is because following an executable symlink doesn't change your working directory. The UT executable wants to run things that are "local," stupidly expecting that the working directory is the one the program was run from. Neverwinter is the same way.

I solved this by creating a script like so:
```
#!/bin/sh

workdir=/home/sparky/games/nwn

cd $workdir
nwn

```
Change $workdir to point to the directory where the UT executable lives, and replace 'nwn' with 'ut-2004.bin'. Then make a launcher that runs the script. Don't forget to make the script executable!

HTH[/QUOTE]

Ty very much!!! I knew it had to be something weird like this. I appreciate it.

---

