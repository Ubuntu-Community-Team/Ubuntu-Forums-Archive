---
title: "Cave Story+ Segmentation Fault"
date: 2012-06-10
forum: Gaming &amp; Leisure
---

### Post by Gaygerbil on 2012-06-10
Wondering if anyone else ran into this problem and looking for a solution to it, couldn't find one anywhere. (Saw someone else had the same problem though)

I downloaded CaveStory+ from the Humble Indie Bundle 4 a while ago, never got around to trying it until now. When running it however my screen flashes and nothing happens. I ran it in the terminal to see what the output was:

```
bewbman@bewbman-desktop:~$ /home/bewbman/CaveStory+/CaveStory+
OS...
Mem...
Graphics...
File...Parsing mod list...
  ...FAILED: list file didn't exist.
Menu...
Loading file: UI.bmp
  (Could not find!)
Loading file: ogph/UI.bmp
  (Could not find!)
Loading file: csfont.fnt
  (Could not find!)
Segmentation fault

```

I did look for those files and they actually are in the folder with CaveStory+, under the data and base folder. I'm really not sure what's going on, so any help would be greatly appreciated, thank you in advance.

---

### Post by Gaygerbil on 2012-06-11
So just right now I went to the original Cave Story site and downloaded the original game for Linux and again I was having problems with the screen just flashing and closing. I figured I'd try the Windows version and run it under WINE and it worked.

So I went ahead and downloaded Cave Story+ in Windows and run it under WINE and surely enough it works fine. Would still love an answer to my question, I'd much prefer to run it natively, but this will do for the time being.

---

### Post by Perfect Storm on 2012-06-11
> /home/bewbman/CaveStory+/CaveStory+

Try instead;
```
cd /home/bewbman/CaveStory+ && ./CaveStory+
```

---

### Post by Gaygerbil on 2012-06-11
Yup that worked haha wow. Not sure why you have to mount the folder first but thanks for the help, really appreciate it!

---

