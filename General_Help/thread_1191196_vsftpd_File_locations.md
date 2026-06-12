---
title: "vsftpd File locations"
date: 2009-06-18
forum: General Help
---

### Post by Muscovy on 2009-06-18
I downloaded vsftpd to run a simple ftp server, and everything makes sense except, I cannot find anywhere, the location for files to be placed manually on the server. Where can I do that?
  Also, how do I access a file from another computer (I don't know the address format).

  Thanks!

---

### Post by jonobr on 2009-06-18
When you login to the the as anonymous,
you end up in your ftp home directory which is by default /home/ftp

If you allow user login you will be placed in your users home directory.

If your having trouble finding where things have been placed, you can

```
sudo find /home/ -name <myupload.exe>
```

This will find the file you just uploaded
I would consider using scp (secure copy) its easier and more secure.

---

### Post by Muscovy on 2009-06-18
How exactly does one access files over the internet? Is it just [ftp://ip/whatever?](ftp://ip/whatever?)

---

### Post by jonobr on 2009-06-18
it depends how its presented,

You should be able to point your browser to it and it should realise that its an ftp fil;e.

If you wanted to ftp that file using cle,

then try
[ftp://username:password@targetip/ftpfile](ftp://username:password@targetip/ftpfile)

or if you want you can drop the password part and it should prompt you for it

---

### Post by jonobr on 2009-06-18
or consider using places->connect to server or from the terminal, just ftp <ipaddress> and see what it puts you,m 
you may need to navigate to your file using cd.

Once thats done, change to binary mode, by typing bin

you can enable hash markings, which show you its working, by typing hash

then mget filename
or mget f*

or if you want to download a lot of stuff ending in *.doc
disable interactive mode by entering
prompt

them mget *.doc

it wont ask you for an answr after each file match

---

### Post by Muscovy on 2009-06-18
What's the easiest way to give a generic username and password across the board?
  Also, this is intended to be downloaded-from by Windows users, if it changes anything.



Edit: Thank you, I can bring it up with [ftp://ip](ftp://ip) in browser now!

---

