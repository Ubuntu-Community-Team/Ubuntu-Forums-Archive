---
title: "how to run executable files in kubuntu"
date: 2006-06-10
forum: Desktop Environments
---

### Post by nocloud on 2006-06-10
i downloaded an executable file for linux (vnc viewer enterprise edition)

konqueror says it is an executable file...

when i double click on it, it asks me what application i want to use to open it...

does anybody know how i can run that executable file?

---

### Post by FizDev on 2006-06-10
Hmm.. what's the file extension?

---

### Post by nocloud on 2006-06-10
there is no extention, konqueror just says it is an executable file and the place i downloaded it from labeled it as an executable file as well....

---

### Post by FizDev on 2006-06-10
Open a Terminal, go to the directory where the executable file is, then type
```
./nameoftheexecutable
```
This will execute it.

---

### Post by Belathor on 2006-06-10
I went to the website and went to the download page for the free edition. I saw they had .rpm files for download too. If you downloaded an .rpm file you could use monkeyblog.org's install advice for rpm's:

> RPM Package (.rpm)
    RPM is another popular way of packaging software, and it's used by popular distributions such as Fedora Core, SUSE Linux and Mandriva. RPM is not used by the Ubuntu Package Manager, but there does exist a command for converting an RPM into a Deb; this doesn't mean that any RPM will work on your system, though! The same program can also install the RPM directly so that you won't have to do this yourself. The command is not available right away so you'll need to install it yourself - the package is called alien and is of course available through Synaptic. If the user carl wants to install an RPM called test.rpm located on his desktop, he will enter sudo alien -i /home/carl/Desktop/test.rpm.

---

### Post by aysiu on 2006-06-10
What's the difference between the "enterprise edition" and the free edition?

If you just want the free edition, paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install xvncviewer
```

---

### Post by nocloud on 2006-06-10
thanks, that worked

---

