---
title: "How to install grid (ccsm plugin)?"
date: 2010-06-05
forum: Desktop Environments
---

### Post by Rumtscho on 2010-06-05
Just bought a new computer and installed Lucid 64 bit. 

On my old PC, I had Lucid 32 bit. There I installed Grid using the instructions on this page: [http://wiki.compiz.org/Plugins/Grid]("http://wiki.compiz.org/Plugins/Grid"). But now, on the new computer, i cannot do it. I get the error: ```
rumtscho@bradbury:~/tmp/grid$ git-checkout 1281082ba678033e515a19419ca8ffe8641d744b
git-checkout: command not found

```
I did install everything mentioned in the instruction, including git-core. The git-clone row worked without errors. So why cannot I finish the installation? 

I don't care if I get Grid from the git repository or from some other source (I don't understand why it is missing from ccsm in the first place, it got installed automatically under 9.10), please just tell me how to get it. Thanks.

---

### Post by Rumtscho on 2010-06-05
Just solved the mystery. 

There is an error in the instructions; the correct command isn't ```
git-checkout
``` but ```
git checkout
```

Head was too bloated after all the OS reinstalls I had to do today, so didn't spot it earlier :X

---

### Post by Zemblan on 2010-06-05
I realize that you have marked this as solved, but if you need to install the grid plugin in the future you might like to know that there is no need to get it from git and compile it.
The grid plugin is part of the compiz-fusion-plugins-extra package in the repos. So you can get it with:
```
sudo apt-get install compiz-fusion-plugins-extra
```

---

