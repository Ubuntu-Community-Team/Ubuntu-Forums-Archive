---
title: "DPKG Parse Error"
date: 2009-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JuggaloN9NE11 on 2009-01-07
ive been trying to install sendmail so i can have XAMPP send emails off of localhost, i used:```
sudo apt-get install sendmail
``` 

then i get an error telling me to run:
```
sudo dpkg --configure -a
```

so i tried that and now i keep getting a parse error:
> 
dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 1: EOF after field name '


what should i do, because now i cant even update anything on the computer, i keep getting this error message
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

```

---

### Post by ibutho on 2009-01-07
In the terminal, run
```
sudo dpkg --configure -a
```

---

### Post by JuggaloN9NE11 on 2009-01-08
ok so i fixed the previous problem but i still get an error when i try to install sendmail

Command:
```
sudo apt-get install sendmail
```

Error:
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblockfile1_1.06.2_i386.deb (--unpack):
 files list file for package `login' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/liblockfile1_1.06.2_i386.deb
Processing was halted because there were too many errors.

```

---

