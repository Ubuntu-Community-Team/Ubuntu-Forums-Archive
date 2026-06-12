---
title: "tar command error"
date: 2009-06-15
forum: General Help
---

### Post by hugobife on 2009-06-15
Hi Everyone
Been trying to download some soft for my web cam and I have found the forums  very helpful. I have  been following advice but I get the below error messages in my terminal when I try to unzip the tar file
the file is definitely sitting on my desktop
would appreciate any help

hugh@hugh-desktop:~$ tar xzf qc-usb-messenger-1.8.tar.gz
tar: qc-usb-messenger-1.8.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
hugh@hugh-desktop:~$

---

### Post by c1rcu1t on 2009-06-15
What release are you using?

---

### Post by Bachstelze on 2009-06-15
> **hugobife said:**
> 
the file is definitely sitting on my desktop


Then do [font="monospace"]cd Desktop[/font] before. ;)

---

### Post by Yellow Pasque on 2009-06-15
You need to be in the Desktop directory. You executed the command from your home (~) directory.
```
cd ~/Desktop
```

---

### Post by briguy47 on 2009-06-15
I would try typing 

```
tar xzf qc-
```and then just press TAB so that autocomplete will kick in.  This will guarantee that there is no accidental misspelling and that the issue is with tar itself.  :)

---

### Post by synapsys on 2009-06-15
hugh-desktop is your hostname. You are sitting in the /home/hugh folder. Need to be in /home/hugh/Desktop.

---

### Post by c1rcu1t on 2009-06-15
You might also try right-clicking and selecting "extract here"

---

### Post by hugobife on 2009-06-15
Wow thanks
Didn't expect so many replies -respect!
Of course I was in he wrong directory
Thanks again
hugo

---

