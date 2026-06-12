---
title: "mutt problem"
date: 2008-12-20
forum: General Help
---

### Post by abhilashm86 on 2008-12-20
i configured and downloaded files to run mail(gmail),but when i open mutt
following error is occuring
/var/mail/abhilash: No such file or directory (errno = 2)

---

### Post by albinootje on 2008-12-20
> **abhilashm86 said:**
> i configured and downloaded files to run mail(gmail),but when i open mutt
following error is occuring
/var/mail/abhilash: No such file or directory (errno = 2)

You should configure your own .muttrc accordingly.
If /var/mail/abhilash is non existing, and you are the sysadmin on that machine, you can create it by doing :
```

sudo touch /var/mail/abhilash
sudo chown abhilash /var/mail/abhilash

```

---

### Post by abhilashm86 on 2008-12-20
> **albinootje said:**
> You should configure your own .muttrc accordingly.
If /var/mail/abhilash is non existing, and you are the sysadmin on that machine, you can create it by doing :
```

sudo touch /var/mail/abhilash
sudo chown abhilash /var/mail/abhilash

```

hey albi thanks a lot,i actually used cat command initially,then used mkdir commands,but it was'nt accepting,good one friend:)

---

### Post by abhilashm86 on 2008-12-20
can i know meaning of touch command please,coz i heard it for first time.......

---

### Post by abhilashm86 on 2008-12-20
From: Abhilash  <abhilash@abhilash-desktop>
      To: [email]abhilashm86@yahoo.com[/email]
      Cc:
     Bcc:
 Subject: hello
     Fcc: ~/sent
     Mix: <no chain defined>
Security: Clear

can any1 tell why from address is not changed?
where should i change?

---

