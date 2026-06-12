---
title: "Dwarf Fortress Problems"
date: 2011-01-20
forum: Gaming &amp; Leisure
---

### Post by Foxkit on 2011-01-20
Ok, so i'm new to Linux in general but am more than willing to get things running on Linux. I've downloaded and extracted the DF directory to my home folder and i've tried running it. I'm running an upgraded 10.4 Lynx from 9.10 Koala laptop. I'm afraid I don't know exactly what makes up this computer or else i would post. To get back to the problem, i've tried running dwarf fortress with ```
./df 
``` from the DF_linux dir. however it says  ```
bash: ./df: /bin/sh: bad interpreter: Text file busy 
``` 
If I try just double clicking it, it pops a window asking to run it in terminal, display it, or to just run it. If i run it in terminal the terminal pops up for a second, then closes so fast that i can't read the code. if i just run it nothing happens. Any help is appreciated, as I already love Linux much more than windows :KS

---

### Post by Kumpu on 2011-03-15
Well it didn't start for me neiter but i found a way to run it - just replace df with this script
```
#!/bin/sh
#DF_DIR=$(dirname "$0")
#cd "${DF_DIR}"
HOME=BASH_SOURCE
export SDL_DISABLE_LOCK_KEYS=1 # Work around for bug in Debian/Ubuntu SDL patch.
#export SDL_VIDEO_CENTERED=1 # Centre the screen.  Messes up resizing.
./libs/Dwarf_Fortress $* # Go, go, go! :)

```

---

### Post by papercrane1001 on 2011-06-18
I'm sorry, I'm also a new user of Linux, and I'm also having troubles with DF.

I did input what you advised above, but when I got to the end, it told me:

bash: ./libs/Dwarf_Fortress: No such file or directory

Does this mean that it's in the wrong place, or that I somehow did something else entirely wrong?

Thank you for your help!

---

