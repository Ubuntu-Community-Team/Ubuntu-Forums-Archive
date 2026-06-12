---
title: "comfiz fusion :can not enable desktop effects"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by James696 on 2008-02-26
My Ati driver are installed,  I have a ati HD 2600 xt 512mb card and compiz fusion is installed because it was working the other day. I believe it stopped working after I installed updates. Now when I try to activate the desktop effects it gives me this error: Desktop effects could not be enabled. I read some of the other posts and tried some things and nothing seems to work. Probably does'nt help that I don't know what I'm doing I'm new to Linux and I'm running Ubuntu 7.10 64  bit. Any help is appriciated.

---

### Post by James696 on 2008-02-27
When I put compiz in the terminal the screen flashes and I get this:

james@james-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

---

### Post by mrmiserable on 2008-02-27
try this let me know

[http://ubuntuforums.org/showpost.php?p=3993442&postcount=5](http://ubuntuforums.org/showpost.php?p=3993442&postcount=5)

---

### Post by James696 on 2008-02-27
Thanks for the information however I'm still learning therefore I'm unsure how to change these lines as indicated in the link.  Could you give me a brief outline on the best way to implement these changes. 

Thanks,
Jim

---

### Post by mrmiserable on 2008-02-27
ok 

open terminal

then type sudo gedit /usr/bin/compiz
search for the lines in the link i gave you then change them save and start compiz again to see if it worked

your problem is /usr/bin/compiz is looking for /usr/local/bin/compiz but it does not exist i think its a little bug but easy to resolve

ask again if you get problem

---

### Post by James696 on 2008-02-28
Got it working!

Thanks!

Jim

---

