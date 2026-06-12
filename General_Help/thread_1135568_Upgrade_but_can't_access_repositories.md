---
title: "Upgrade but can't access repositories"
date: 2009-04-24
forum: General Help
---

### Post by Morokiane on 2009-04-24
I upgraded from 8.10 to 9.04 successfully...however, my apt-get repositories are no longer accessible it does point to the jaunty ones but I get Could not resolve 'us.archive.ubuntu.com'

I also like how when I do apt-get update and it fails it tells me to do a apt-get update...haha.

---

### Post by Almighty on 2009-04-24
I had the same problem. Fortunately it "fixed itself." I did experience very slow transfer speeds also. I'll assume it's because a million people are doing the same thing at the same time?

---

### Post by shunter1191 on 2009-06-03
I have had the same problem, I recently installed Jaunty, but because of an error with a package, I cannot boot at all. It gets to about 9/10 of the way through the initial boot-up loading bar, and then the screen flashes and goes blank. Starting in recovery mode every check except dpkg works fine, and dpkg gets this error message ```
W: Some index files failed to download, the have been ignored, or old ones used instead.
W: you may want to use apt-get update to correct these problems
```after that it gives the normal output for an update, stating - 
```
0 upgraded, 0 newly installed, 0 to remove, and 12 not upgraded
```and giving a yes or no prompt.

---

