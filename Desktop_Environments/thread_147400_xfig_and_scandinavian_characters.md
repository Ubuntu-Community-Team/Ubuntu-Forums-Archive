---
title: "xfig and scandinavian characters"
date: 2006-03-20
forum: Desktop Environments
---

### Post by inha on 2006-03-20
Hi. 

I'm having problems getting the ås, äs  and ös to show up in xfig. xfig supposedly uses iso-8859 for text encoding and that should include those characters. I'm pretty new to the program and I'd appreciate all advice on getting around this issue.

---

### Post by moma on 2006-03-20
Hello,

1) Check your /etc/locale.gen
$ cat  /etc/locale.gen 

nb_NO.ISO-8859-1 ISO-8859-1
en_US.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
.....
.....

Add your country's character map (swedish, finnish, norwegian, danish) at the top of the (/etc/locale.gen) list.   For example I added "nb_NO.ISO-8859-1 ISO-8859-1" for Norway.      Xfig may not understand (the quite new) UTF-8 method, so ISO-8859-1 must do.

Save the file and regenerate character maps like this:
$  sudo locale-gen

Set the language and start xfig like this (on the same line. Replace nb_NO (norsk bokmål) with your own language)

$  LANG=nb_NO.ISO-8859-1  xfig

And ÆØÖÄÅ and other north_european characters should appear correctly.  This method applies to any other older and weird app.

Sincerely
  moma
  [http://www.futuredesktop.org/how2burn.html#Ubuntu](http://www.futuredesktop.org/how2burn.html#Ubuntu)

PS.  Xgl & Compiz :: [http://ubuntuforums.org/showthread.php?t=147049](http://ubuntuforums.org/showthread.php?t=147049)

---

### Post by inha on 2006-03-20
That did the trick. Thanks a lot!

---

