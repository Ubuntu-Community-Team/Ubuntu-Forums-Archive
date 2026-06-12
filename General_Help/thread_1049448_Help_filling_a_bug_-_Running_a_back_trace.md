---
title: "Help filling a bug - Running a back trace"
date: 2009-01-24
forum: General Help
---

### Post by Orfintain on 2009-01-24
I'm trying to file this bug and I need to do a back trace and I have having trouble getting the debugging symbols installed it
following this guide
[http://wiki.ubuntu.com/DebuggingProgramCrash](http://wiki.ubuntu.com/DebuggingProgramCrash)
I get the this point and

"username@jahbuntu:~$ gpg --check-sigs 428D7C01 # signed by key of Martin Pitt
pub 1024D/428D7C01 2008-09-02
uid Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sig!3 428D7C01 2008-09-02 Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sub 2048g/A2C2A7A5 2008-09-02
sig! 428D7C01 2008-09-02 Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>

1 signature not checked due to a missing key"
Then I get a bunch of ..
"No symbol table info available."

a history of the problem can be found here
[http://ubuntuforums.org/showthread.php?t=1023477&page=2](http://ubuntuforums.org/showthread.php?t=1023477&page=2)

---

### Post by Orfintain on 2009-01-26
Just wanted to add that I ran the updates and they did not resolve this issue

---

### Post by Orfintain on 2009-01-31
The problem has been coming and going I tried loading old kernals which didn't fix it.

Can someone help me get the symbol libraries installed.

---

### Post by Prometheus28 on 2009-02-08
I also need help as trying

> 


nick@nick-desktop:~$ gpg --check-sigs 428D7C01
pub 1024D/428D7C01 2008-09-02
uid Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sig!3 428D7C01 2008-09-02 Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sub 2048g/A2C2A7A5 2008-09-02
sig! 428D7C01 2008-09-02 Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>

1 signature not checked due to a missing key


gives me bugs

i am unable to find any debugbuilds for kdenlive

---

### Post by Orfintain on 2009-02-08
I never fixed the missing key issue but my problem was on this line of code

apt-cache policy yelp

I was coping it verbatim instead of changing yelp to the program I was having trouble with (evolution in my case)

---

