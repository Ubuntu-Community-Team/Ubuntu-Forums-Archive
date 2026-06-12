---
title: "can't get colors to work in terminal"
date: 2010-02-06
forum: Desktop Environments
---

### Post by bostjanv on 2010-02-06
Hello,
I used to work with colors in the terminal by defining environment variables with values equal to ANSI escape sequences, e.g.,

CSI=$'\x1b'[
REDF="$CSI"31m
BLACKF="$CSI"30m

and then if I wrote

echo $REDF bla bla $BLACKF

"bla bla" would show up in red.  For some reason this does not work in Ubuntu 9.10. Perhaps some settings are wrong. Can someone give me some advice?
Regards,
bostjanv

---

### Post by bostjanv on 2010-02-06
Sorry, my mistake. Actually, I made several mistakes, the main one of which not to use echo -e. Some distributions have echo -e as the default (-e not necessary).
Regards,
bostjanv

---

