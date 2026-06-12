---
title: "2 machines, 1 set of packages"
date: 2006-03-11
forum: Desktop Environments
---

### Post by svref on 2006-03-11
I have two nearly-identical computers, used interchangably.   One comes to ubuntu by way of breezy > dist-upgrade dapper.  The other comes dapper-flight-4 > dist-upgrade dapper.  And yet they're not exactly the same, in gnomish ways I can't quite put my finger on.

How can I get a print-out of the packages installed on each computer, so that I can diff them and reconcile the differences?

---

### Post by jasay on 2006-03-11
After reading the apt-cache man pages, I'd guess something like:```
 apt-cache pkgnames --installed > some_file_name

``` on each machine and then after copying them to the same folder```
diff some_file_name1 some_file_name2
```

---

### Post by svref on 2006-03-11
Thanks!

**Holy SH*T!!!**
The Dapper-4 guy has ~7,000 packages.
The Dapperized-Breezy has 22,000 packages. (a strict superset)
Yeah, at one point I installed some "-dev" packages on the latter, and that might have brought in 200 packages, but there's no way in heck that accounts for 15,000 packages!  I wonder what caused that?

Looking through them there seems to be no rhyme or reason to them.  E.g. -dev packages for apache module interfacing, in Ruby!  When I don't use any of those, much less all of them.

---

### Post by svref on 2006-03-11
I guess I can do the following: Get the machine with the smaller number of packages fully working, then apt-get remove the set difference from the bloated machine.

---

### Post by bb002 on 2006-03-12
Um... apt-cache doesn't have a "--installed" parameter and "pkgnames" lists every availiable package, installed or not.

after a little searching and testing. i managed to get a correct package listing by installing a program named "apt-show-versions". then running the command ```
apt-show-versions -a | grep "install ok installed" > ~/Desktop/out.txt
```

"apt-show-version -a" lists every single package availiable just like "apt-cache pkgnames". However, this program adds some extra info on the same line.
So by piping the output to grep and having grep look for "install ok installed" (any other string combination yielded inacurate results. either false positives or duplicates.) finally saving grep's output to the desktop.

For accuracy I picked some random packages out of synaptic and the search for comparision. If synaptic said a package was installed so did the search and visa-versa.

Hopefully you will get a more accurate picture now. :)

[edit]

Hmmm....Well I just checked the man pages for apt-cache. Seems it really DOES have a --installed parameter, it just doesn't work. I normally only trust the options listed by running the command with the "--help" parameter. If i don't enough info that way then I check the man page for that parameter.

BTY, what tag is it that adds a strike through your text? I guessed a couple times but nothing worked. Or is that not possible here and I'm thinking of another forum?

---

### Post by jasay on 2006-03-12
[QUOTE=bb002]Um... apt-cache doesn't have a "--installed" parameter and "pkgnames" lists every availiable package, installed or not.

after a little searching and testing. i managed to get a correct package listing by installing a program named "apt-show-versions". then running the command ```
apt-show-versions -a | grep "install ok installed" > ~/Desktop/out.txt
```

"apt-show-version -a" lists every single package availiable just like "apt-cache pkgnames". However, this program adds some extra info on the same line.
So by piping the output to grep and having grep look for "install ok installed" (any other string combination yielded inacurate results. either false positives or duplicates.) finally saving grep's output to the desktop.

For accuracy I picked some random packages out of synaptic and the search for comparision. If synaptic said a package was installed so did the search and visa-versa.

Hopefully you will get a more accurate picture now. :)[/QUOTE]Shoot. You're right.  --installed only limits "depends and rdepends"  Look who feels stupid now.  :oops: :oops: :oops:

---

### Post by bb002 on 2006-03-12
Well I just checked the man pages before your post and after mine. I saw the --installed parameter and correct my post then saw your new post. So I doubled checked the --installed parameter and read it's discription this time. Be nice if that parameter worked with pkgnames :) would make thing easier....I think.

---

