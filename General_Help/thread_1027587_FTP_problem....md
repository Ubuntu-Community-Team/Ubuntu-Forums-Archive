---
title: "FTP problem..."
date: 2009-01-01
forum: General Help
---

### Post by enndy on 2009-01-01
Hello.

I recently installed ubuntu in my laptop and everything are working fine, except the ftp on the Ubuntu's File Browser.

The problem is when I go to Ubuntu's File Browser and in the bar a type this:

[ftp://myftpserver.com](ftp://myftpserver.com) 

I typed the username and the password, then the connection to the server it's o.k., the problem is that I can't see the folders and files, I received an EMPTY, but their are a lot of folders and files. 

I tested using the gftp software and are working fine, I can see all the folders and files.

Why I loging to ftp server and i can not see the folders and files ???

Thanks.

---

### Post by wmdiem on 2009-01-01
It might not be a good solution but you could try using curlftpfs to mount it into your filesystem. Then there would be no issue with nautilus.

---

### Post by kokkus on 2009-01-01
I use Nautilus.
Create a new launcer "sudo nautilus [ftp://ftp.yourftp.com](ftp://ftp.yourftp.com)"

---

### Post by enndy on 2009-01-01
I already installed nautilus. But, I have the same problem.

why the file manager do not show me the files and folders of the ftp server ????

---

