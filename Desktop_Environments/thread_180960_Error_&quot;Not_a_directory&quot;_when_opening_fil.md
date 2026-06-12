---
title: "Error &quot;Not a directory&quot; when opening files from Windows share"
date: 2006-05-23
forum: Desktop Environments
---

### Post by sander marechal on 2006-05-23
Hello,

I have mounted a Windows share using "Places->Connect to server". I can browser teh share fine with Nautilus but I cannot open any files, nor copy any files from the share to my Desktop so I can open them locally. I always get the error:

```
Error "Not a directory" while copying "smb://somefile.txt"
```

Any help please? I'm stumped. Searching the forums or even Google doesn't turn up a single instance of this error message. Surely I'm not the first to experience this? Moving my work PC over to Ubuntu has been a succes so far but this is a showstopper.

---

### Post by sander marechal on 2006-05-24
Anyone? Please? I'm really stumped by this. The strange thing is that it works perfectly with a different share that I connected to.

---

### Post by banditti on 2007-01-29
Me too.  Thoughts?

---

### Post by sander marechal on 2007-02-02
I found a workaround. Instead of using smb I installed cifs and added the network drives to my /etc/fstab.

```

//server/share   /media/mountpoint   cifs    username=Sander,password=XXXXX,uid=sander,gid=sander     0       0

```

---

### Post by mogul on 2007-02-07
I've got the exact same problem, and finding a blank when searching Google had convinced me it was my own damned fault.

Surely there's a way to fix this so it works as expected rather than having to fall back to an fstab-level CIFS mount... Isn't there?

---

### Post by sander marechal on 2007-02-07
Maybe there is a way to let Gnome's "connect to server" use cifs, alongside all the other methods, but I don't know how. But using cifs instead of smb is definately the way to go.

---

### Post by loo_nix on 2007-02-24
Hi , guys, I had the same issue on SUSE. So here is what the problem was :

I was specifying only the full directory and not the share name.
It would actually navigate there OK and show me all the files but , 
would get the "Not a directory" error when trying to copy.

The problem is is that you need to specify the actual name of the share, 
the way it was defined on the win box. You still enter the full directory , 
the win box name (w/o domain) , and separately the domain 
(e.g. corp.canonical.com) and optionally the user name.

HTH. Cheers.

---

