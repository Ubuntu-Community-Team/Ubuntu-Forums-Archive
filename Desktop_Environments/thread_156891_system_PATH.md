---
title: "system PATH"
date: 2006-04-08
forum: Desktop Environments
---

### Post by geniusvicks on 2006-04-08
How do I make sure that "realplay" is in my system path, and that it points to RealPlayer 10.

---

### Post by jpkotta on 2006-04-08
Ensure it is in your path (without running it) with ```
which realplay
```

Find it if it is not in your path with ```
locate realplay
```
You may need to run ```
sudo updatedb
``` first, but probably not unless you just installed realplay less than 24 hrs ago.

Put it in your PATH by adding the directory that it is located in to your PATH.  Add to ~/.bashrc```
PATH=$PATH:/location/of/realplay
```  realplay is in /usr/bin on my machine, which is practically guaranteed to be in the default PATH on any distro, and is part of the default PATH in Ubuntu.  Look at your current PATH with ```
echo $PATH
```

/usr/bin/realplay is a symlink to another file.   You can show the final destination (the "canonical filename") of any symlink with ```
readlink -f /usr/bin/realplay
```

---

