---
title: "ftp question"
date: 2009-06-18
forum: General Help
---

### Post by tomdagreek on 2009-06-18
got a noob question for u guys that may have a easy answer...
working with ftp in the linux terminal. is there a way to ftp a whole directory instead of doing one file at a time?
i am using the get command. i have had a tough time to mount a external dvdrom on my one machine and could very well ftp it from a another. 
it is a large file around 5 gigs with many folders within it
thanks

---

### Post by jonobr on 2009-06-18
hello

You could archive the directory for copying.

You can compress is as follows

```
tar -cvf mydir.tar mydir 
```

it creates a tar file called mydir.tar using the directory mydir

If what you want it in a different directory I.e. on the desktop you should give the path from where you are,

```
tar -cvf mydir.tar ~/Desktop/mydir 
```

One you tar it up you can also compress is.
You could also right click on the directory and create and archive
this will tar and compress the directory for you also.

Once you move over the large amount of info,
I wouold recommend investigating rsync.

This means once the files are copied over, rsync would compare source and destination and copy over the changes in both, but thats a different days work

---

### Post by t4thfavor on 2009-06-18
+1 above, if you need more suggestions please check here, as they have a pretty good thread started that I think pertains to Linux as well.

[http://forums.macosxhints.com/archive/index.php/t-52649.html](http://forums.macosxhints.com/archive/index.php/t-52649.html)


or try wget with the -r option 

Im not sure of the syntax, but I know it will do what you are asking.

Another option is 

cd /somedir/

ftp -inv
open <remote server>
user <uid> <passwd>
ascii
mget *
bye
!

---

### Post by geirha on 2009-06-18
You could also try out [ncftp](apt://ncftp), it's a more feature rich ftp-client than the default ftp client. Amongst other things, its get command allows wildcards, and it has tab-completion.

Run "help get" in ncftp for examples.

---

### Post by tomdagreek on 2009-06-18
in my haste i forgot to mention i am ftpee ing from my windows box to my linux server
if that makes a difference

---

### Post by geirha on 2009-06-18
> **tomdagreek said:**
> in my haste i forgot to mention i am ftpee ing from my windows box to my linux server
if that makes a difference

That makes quite the difference. The default ftp client in windows is very different from the default ftp client in ubuntu. Find a better ftp client for windows. Filezilla perhaps.

---

### Post by oldos2er on 2009-06-18
> **tomdagreek said:**
> in my haste i forgot to mention i am ftpee ing from my windows box to my linux server
if that makes a difference

 There should be a port of ncftp available for Win*.

---

### Post by HermanAB on 2009-06-18
ftp> prompt off
ftp> mget *

---

### Post by tomdagreek on 2009-06-18
yes i have filezilla installed on the win box it was the only way i got the ftp to work
seems to work well
any other suggestions will be appreciated. i have archived the file on the windows side or maybe i should compress it using winrar either way i will try to fire it up this weekend
thanks for all ur help

---

### Post by jonobr on 2009-06-18
+1 on filezilla if your not used to cli stuff.
Once you do the ftp across go the home dir of the user you ftp as and the file should be there

---

### Post by t4thfavor on 2009-06-18
If your not limited to cmd, try fireFTP as a FireFox addin. I use it and it orks fairly well.

If you just want to transfer files on a local lan, give Samba a try, I got it setup and working in about 10 minutes, and have not had a problem with it in about 4 months.

---

