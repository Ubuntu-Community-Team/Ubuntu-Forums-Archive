---
title: "Is there software that..."
date: 2006-07-11
forum: Desktop Environments
---

### Post by DAaaMan64 on 2006-07-11
I have search for such software but with no luck.  Several windows packages but, who wants those :p.  Anyways I need an application that will monitor my outside ip address then notify my via email when it changes. :)  Anyone know?

Thank you

---

### Post by 23meg on 2006-07-11
You can do it with a bash script. Here's an example you can start with, which I found with a web search: 

[http://www.linuxforums.org/forum/linux-programming-scripting/50129-creating-script-notify-me-ip-address-change-2.html](http://www.linuxforums.org/forum/linux-programming-scripting/50129-creating-script-notify-me-ip-address-change-2.html)

Also check out [http://shelldorado.com](http://shelldorado.com) which is a great resource for ready made scripts.

---

### Post by Thund3rstruck on 2006-07-11
Are you behind a router? If so you'll want to use wget to fetch the  (Summary) page that stores your inet address then you can parse it with RegEx (sed/awk/grep) for changes.

---

