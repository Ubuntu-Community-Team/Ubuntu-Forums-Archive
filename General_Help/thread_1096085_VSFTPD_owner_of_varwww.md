---
title: "VSFTPD owner of /var/www"
date: 2009-03-14
forum: General Help
---

### Post by artheus on 2009-03-14
hey..

I have made a virtual user in vsftpd the owner of the /var/www folder.. so that I logically should be able to edit the eg. index.htm file in my apache2 server.

And login in to the ftp and changin the file works great. But when I tried to look at the file in "www.mydomain.com" I get the message:

```
Forbidden

You don't have permission to access /index.htm on this server.
```

And this must be because of that root owns apache2 and webmaster owns the folder.. and that makes a conflict. .right?

so.. how can I fix this? eg. how can I make the **virtual** user webmaster a owner of apache2? or anything else that would solve this problem?

Cheers,
Artheus

---

### Post by artheus on 2009-03-14
Is it possible to port a folder to another.. If you know what I mean????

---

### Post by cariboo on 2009-03-14
Did you set the premissions of the file to 755?

Jim

---

### Post by artheus on 2009-03-14
Now I did that! And it works!
Thanks!

But... Do I have to do this for every file I put there?
Or is there maby a way of writing something that automatically sets the permissions of the files uploaded to 755?

As I will be uploading theese files from a Windows computer, via Dreamweaver ftp, I will not always be able to go to the server and set the file permissions to 755 everytime I upload a file.. And that procedure seems a little... unecessary?

Thanks,
Artheus

---

