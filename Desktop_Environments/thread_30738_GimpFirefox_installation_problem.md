---
title: "Gimp/Firefox installation problem"
date: 2005-04-30
forum: Desktop Environments
---

### Post by elder68 on 2005-04-30
A couple of days ago I did a fresh install of Kubuntu. I like it a lot but would like to add some software that I am used to using. Following is the result of those efforts. As you can see, I did not get very far. Any advice would be appreciated.

william@kubuntu:~$ sudo apt-get install mozilla-firefox
Password:

Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate

william@kubuntu:~$ sudo apt-get install gimp

Reading package lists... Done
Building dependency tree... Done
Package gimp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gimp has no installation candidate
william@kubuntu:~$

---

### Post by Morgoth on 2005-05-01
It looks like you need to add some sources to the repository list.

try:
sudo kate /etc/apt/sources.list
and uncomment ( delete the #s ) all the lines that start with #deb........

I had trouble with updates when I uncommented the last three ( ftp.nerim.net ) so it's okay to leave them if you want.  I get all the software I want without them anyway.

---

### Post by elder68 on 2005-05-01
[QUOTE=Morgoth]It looks like you need to add some sources to the repository list.

try:
sudo kate /etc/apt/sources.list
and uncomment ( delete the #s ) all the lines that start with #deb........

I had trouble with updates when I uncommented the last three ( ftp.nerim.net ) so it's okay to leave them if you want.  I get all the software I want without them anyway.[/QUOTE]

Thank you for the above, that was the problem. I got the Gimp and Thunderbird and Firefox down and working. Firefox tells me that it can't find an index file when it boots up but seems to work OK. At the moment I can't remember the path to that file and I am not working on that machine at the moment.

All the best.

---

