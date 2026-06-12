---
title: "fast belgian server with ubuntu repo's!!"
date: 2005-12-25
forum: General Help
---

### Post by namedontwant on 2005-12-25
Hi all,

Belnet has put ubuntu on it's servers. Belnet is very fast.

Here you find the packages:
[http://ftp.belnet.be/packages/ubuntu/ubuntu/](http://ftp.belnet.be/packages/ubuntu/ubuntu/)

However, I can't find out how to change my /etc/apt/sources.list to be able to use this server.... Anybody who can help?

Thank you very much.

---

### Post by MonolithTMA on 2005-12-25
```
sudo gedit /etc/apt/sources.list
```

Should open it *and* make it editable.

---

### Post by namedontwant on 2005-12-25
I know how to edit sources.list. The questions is: what do I put in it? I've been trying several things, and it doesn't work.

Thanks for trying ot help, anyway.

---

### Post by MonolithTMA on 2005-12-25
What have you tried? I'm working in OS X right now so I can't boot into Ubuntu to test, but if they are valid repos, then you should just be able to add the following to your list.

```
deb ftp://ftp.belnet.be/packages/ubuntu/ubuntu/
deb-src ftp://ftp.belnet.be/packages/ubuntu/ubuntu/
```

It is an active FTP server, I just logged into it.

Make sure you are putting FTP at the beginning and not HTTP like your original post has. HTTP allows your web browser to see it, but I'm pretty sure you need the FTP for an FTP server.

---

### Post by MonolithTMA on 2005-12-25
Ignore my previous post. It looks like you need to find the path to each repository and change your source file to match them. I'd email [email]ftpmaint@belnet.be[/email] and see if they can help you.

Good luck! :)

---

