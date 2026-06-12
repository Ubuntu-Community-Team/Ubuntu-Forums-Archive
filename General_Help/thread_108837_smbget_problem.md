---
title: "smbget problem"
date: 2005-12-27
forum: General Help
---

### Post by _jane_ on 2005-12-27
Hi. I´ve been trying to download files from a samba server and the smbget-program was working fine until I tried downloading a file that had a space-separated filename, for example:

smb -r -a -w WORKGROUP smb://FRIENDSSERVER/sharedirectory/subdirectory/the file that I wanted.txt
(I have to be guest, I don´t have any passwords)

and the program gave me an error message that it couldn´t find //FRIENDSSERVER/subdirectory/the
because that was the first place in the address that had a space-separated character in the filename.
Can I get that file using smbget or is there an another program that I could use?

---

### Post by Thunk on 2005-12-27
Instead of using the syntax "name of file", add a "\" after each word: "name\ of\ file"

Try that.

---

