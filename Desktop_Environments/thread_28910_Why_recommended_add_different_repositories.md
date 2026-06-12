---
title: "Why recommended add different repositories?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Alexandr on 2005-04-22
First, greater thank all participants of forum and developers Ubuntu. It really beautiful!

And now question. :)

In different documents is recommended add different repositories (for wincodecs, Java, divx, dvd ...).

1. In [https://www.ubuntulinux.org/wiki/RestrictedFormats](https://www.ubuntulinux.org/wiki/RestrictedFormats)  recommend to add only

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main

with
  
   Package: *
   Pin: release a=unstable
   Pin-Priority: 1

in  /etc/apt/preferences.

Not backports repositories.

2. In [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) (Author: Chua Wen Kiat) recommend to add

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

and install mplayer NOT from marillat.

3. In "Automate Script for New Users" (Author: ubuntu-geek):

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Not backports. (Right?)

4. In HAIH (Hoary After-Install Helper, Author: Nis) :

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

only, not marillat.

Greater thank all authors!

So, where truth? As better and correct? Possible come to the general opinion? I bewildered. :)

Thanks.

---

### Post by Leif on 2005-04-22
They provide different things. Backports are more tailored for ubuntu, but there are some things in marillat that are not in backports. The choice of whether or not to use either of them is up to you. I use both quite happily.

---

### Post by heimo on 2005-04-22
Word of caution. I haven't run into problems, but I recall reading that using both marillat and backports can cause dependency problems. If I remember correctly, there are some packages which are in both repositories.

---

### Post by derrick1985 on 2005-04-22
[QUOTE=heimo]Word of caution. I haven't run into problems, but I recall reading that using both marillat and backports can cause dependency problems. If I remember correctly, there are some packages which are in both repositories.[/QUOTE]

Yes, there is. So usually it's best to either follow a guide (like [http://www.ubuntulguide.org](http://www.ubuntulguide.org)) where everything has been done already/always getting worked on.

---

