---
title: "Connect to webdav in 13.04"
date: 2013-04-30
forum: Desktop Environments
---

### Post by Charlotte18 on 2013-04-30
As has been noted [elsewhere]("http://ubuntuforums.org/showthread.php?t=2116588"), the "Connect to server" box has changed in 13.04. I cannot get the davs:// command to work in the newfangled box. After I type the davs://host command, I get the dialog box to enter my credentials, but nothing happens after that. The username/password box goes away, the "Places" column blinks, and then nothing happens. In other words, no error appears, but neither does the webdav folder appear.  Any advice?

---

### Post by chrismyers on 2013-05-28
Did you find how?

I am running into the same problem.

BTW.. Why did Ubuntu call the file manager "files"? Searching the web doesn't produce helpful results!

:-(

---

### Post by Charlotte18 on 2013-05-28
I have not solved the problem. Since I posted, though, I have changed to lubuntu because unity in 13.04 finally became too slow on my old hardware. 

In lubuntu, I get an error message from pcmanfm after some time passes, so I cannot use davs:// to access webdav. I can authenticate with https:// in Chromium, but davs:// does not work in the file manager.  I'm not sure whether the problem is coming from Ubuntu or from the webdav server.

---

### Post by mkstallings1 on 2013-06-16
If anyone can help, I too would love to connect to webdav in 13.04.

---

### Post by pmgc25 on 2013-06-16
> **mkstallings1 said:**
> If anyone can help, I too would love to connect to webdav in 13.04.
Install gigolo. 
[https://apps.ubuntu.com/cat/applications/gigolo/](https://apps.ubuntu.com/cat/applications/gigolo/)
I have connect to my box.com accounts.

---

### Post by corey-f on 2013-10-17
Gigolo just opens the Files application with the following format:

```
dav://username@host:port/
```

---

### Post by shopkeeper on 2013-12-21
I was able to connect to my Box account using the following format:
davs://email%40domain.com@dav.box.com/

---

### Post by gen0m on 2013-12-27
1. open Nautilus
2. Press ALT-L to show the location bar
3. Type **davs://dav.box.com/dav** into location bar
4. Enter your login into the popup.

---

