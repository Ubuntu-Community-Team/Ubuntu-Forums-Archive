---
title: "apt repository hangs"
date: 2006-07-23
forum: Desktop Environments
---

### Post by martial on 2006-07-23
this is quite odd, but when i try to update my apt repositories, when trying to connect to us.archive.ubuntu.com (146.137.96.7) is hangs and never finishes updating the packages. does anyone have any thoughts?

thanks
martial

---

### Post by Jagot on 2006-07-23
Several people are reporting issues with the US mirror this evening.  Try again in a couple of hours or change the mirror you're using.

---

### Post by teike on 2006-07-23
I was having issues with downloading from the repos also... It appears to be a problem with the us.archive.ubuntu.com mirror. 

If you edit /etc/apt/sources.list and replace *[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)* with *[http://archive.ubuntu.com](http://archive.ubuntu.com)* it will rememdy the issue. 

Just remember to run **sudo apt-get update** after updating the file!

---

