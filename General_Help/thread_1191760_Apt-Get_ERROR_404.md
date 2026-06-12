---
title: "Apt-Get ERROR 404"
date: 2009-06-19
forum: General Help
---

### Post by matey3 on 2009-06-19
I get error 404 upon running the **apt-get -f install**
sources file is OK and I can http to the link it cannot find. So how do you fix this?

Do you want to continue [Y/n]? y

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main libglib2.0-0-dbg 2.16.6-0ubuntu1
  404 Not Found

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main libglib2.0-0 2.16.6-0ubuntu1
  404 Not Found

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0-dbg_2.16.6-0ubuntu1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0-dbg_2.16.6-0ubuntu1_amd64.deb)  404 Not Found

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.6-0ubuntu1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.6-0ubuntu1_amd64.deb)  404 Not Found

E: Unable to fetch some archives, maybe **run apt-get update or try with --fix-missing**?


When using** --fix-missing** I get:


Reading state information... Done

You might want to **run &#8216;apt-get -f install&#8217; **to correct these.
The following packages have unmet dependencies.

  libglib2.0-0-dbg: Depends: libglib2.0-0 (= 2.10.3-0ubuntu1) but it is not installed
E: Unmet dependencies. Try using -f.


Catch 22?
What is unmet dep. mean? (line above)

Is there any way I could install the missing files manually? I used dpkg but I got errors...

Thank You!

---

### Post by redilyn on 2009-06-19
Change the server to the main ubuntu server and try again.

System -> Administration -> Software sources

Change download from to Main Server.

---

