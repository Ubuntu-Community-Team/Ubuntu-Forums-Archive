---
title: "gFTP + SSL AUTH?"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Flintkalle on 2006-01-25
Hi I have this problem with gFTP. I can't connect to a ftp that requires SSL. I've tried installing openssl but with no difference. Anyone else that know what to do?

---

### Post by audax321 on 2006-01-25
I had to connect to an SSL FTP a while back and I couldn't figure out how to do it using gFTP either. But, I found this program: [http://www.glub.com/products/secureftp/](http://www.glub.com/products/secureftp/)

It's free for non-commercial use and can be installed as a user into a local directory, so you don't have to do a root install. Then to uninstall, just delete the directory you installed it to.

---

### Post by cwaldbieser on 2006-01-26
[QUOTE=audax321]I had to connect to an SSL FTP a while back and I couldn't figure out how to do it using gFTP either. But, I found this program: [http://www.glub.com/products/secureftp/](http://www.glub.com/products/secureftp/)

It's free for non-commercial use and can be installed as a user into a local directory, so you don't have to do a root install. Then to uninstall, just delete the directory you installed it to.[/QUOTE]
curl also works:
```

SITE=ftps.example.com
USER=user
PWD=password
FILE=filename

#List the directory.
curl -k --ftp-ssl --sslv3 -u ${USER}:${PWD} ftp://${SITE}/

#Delete a remote file.
curl -k --ftp-ssl --sslv3 -u ${USER}:${PWD} -Q "DELE ${FILE}" ftp://${SITE}/ 

#Upload a file.
curl -k --ftp-ssl --sslv3 -u ${USER}:${PWD} -T ${FILE} ftp://${SITE}/

```

---

### Post by Flintkalle on 2006-01-27
Ok, thanks for all the answeres. But I have reformulate my question. I need an ftp client that is PRET compatible, because I've found out that the site i was trying to connect to is an drftpd server. I have checked their homepage and I saw that there were some clients available but i cant get them to work. Maby because I suck at compiling stuff or that they dont work in ubuntu.

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=Flintkalle]Ok, thanks for all the answeres. But I have reformulate my question. I need an ftp client that is PRET compatible, because I've found out that the site i was trying to connect to is an drftpd server. I have checked their homepage and I saw that there were some clients available but i cant get them to work. Maby because I suck at compiling stuff or that they dont work in ubuntu.[/QUOTE]
What is PRET?  I tried looking it up, but the closest I came was the ftp EPRT command.  If you provide the homepage link, maybe we can take a look at their clients and let you know if they're usable.

---

### Post by nix4me on 2006-01-27
My experience with ftp clients for Linux is that secureftp is the best by far.

I use it daily, mostly with ssl/tls sites.

nix4me

---

### Post by Flintkalle on 2006-01-30
Here you got a link to the site: [www.drftpd.org](www.drftpd.org)  .

---

