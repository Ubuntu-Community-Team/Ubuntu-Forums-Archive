---
title: "How to download compressed archive (zip,7z,etc..) in bulky by wget"
date: 2018-02-22
forum: Desktop Environments
---

### Post by abdulbadii on 2018-02-22
How to download compressed archive (zip, 7z, bzip, xz, etc) files automatically in bulky from a repository by use of wget ?

---

### Post by TheFu on 2018-02-22
It depends on the repository. If they use javascript to generate the URLs, then wget won't help.
OTOH, if you have a base URL and it is simple HTTP/FTP, then you can use simple patterns to match the files to be grabbed with wget.  

But, as an example, 
```
$ wget -r -nd -Ahigh-quality.mp3 URL

    -r recursive
    -nd no directories
    -A{patteren} – which file patterns to match – no regex, sorry
    URL – the ftp/http location to start at
```
The manpage has lots more of details, of course.

---

