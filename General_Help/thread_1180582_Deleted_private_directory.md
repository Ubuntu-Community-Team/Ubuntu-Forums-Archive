---
title: "Deleted private directory"
date: 2009-06-07
forum: General Help
---

### Post by Praxicoide on 2009-06-07
Hello, I borrowed my computer and the person sent my Private folder to the trash.

Now I can't even start an x session. The entire directory does not mount.

Typing "ecryptfs-mount-private"

Gives me "Encrypted Private is not setup properly"

Following the instructions [here](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually) gives me a "no such file or directory."

Is there any way I can recover my files? I'm very surprised at how easily someone can completely ruin one's files.

---

### Post by Praxicoide on 2009-06-08
Any help is more than appreciated. So far nothing I have tried has worked. I want to avoid losing my data, especially since it's still there, only I can't mount it.

---

### Post by Praxicoide on 2009-06-09
bump

---

### Post by michy99 on 2009-06-09
So I assume the private folder was in your trash when you got the computer back, and you restored it to its original location. Is this correct?

---

### Post by Praxicoide on 2009-06-09
I never got the chance. I assume it's in the trash, but I can't start an xsession.

---

### Post by michy99 on 2009-06-09
Do you see the folder if you do```
ls /home/{YourUserName}/.local/share/Trash/files
```

---

### Post by Praxicoide on 2009-06-10
I get "no such file or directory", not even for /.local. I suppose it's because it doesn't mount the directory. All it leaves me with is Access-Your-Private-Data.desktop and README.txt.

---

### Post by Praxicoide on 2009-06-10
I do have a /.ecryptfs directory. It contains: auto-mount auto-umount and wrapped-passphrase.

Opening them with nano shows that the first two are empty, and the last one has some digits followed by weird symbols.

---

### Post by Praxicoide on 2009-06-10
I also have a /.Private directory, containing a bunch of files that start with "ECRYPTFS_FNEK-ENCRYPTED."

I tried to solve my problem by reestablishing the encryption using:

ecryptfs-setup-private 

But it said that it would rewrite the /.ecryptfs directory. Since that's what I intend to do, I tried with 

ecryptfs-setup-private --force

but then it complains that /.Private needs to be empty.

I'll back both files and try again. We'll see....

EDIT:

It doesn't let me copy the stuff, and I'm not confident enough th erase it.

---

### Post by Praxicoide on 2009-06-11
If anyone has even a clue, or an idea to try out, I'd love to hear it. I don't want to lose my data, especially over a dumb user-level error made by someone without root privileges (I'm still kicking myself for thinking it was safe, because she couldn't change anything in the system, bla, bla.)

---

### Post by michy99 on 2009-06-11
What is the output of```
ls -la ~
```

---

### Post by Praxicoide on 2009-06-13
I can't say because the computer has now died on me.:(

I try to turn it on, but it does nothing. I'm not sure if it's even worth repairing it because it's an old laptop. I could try to salvage the hard drive, but what's the use if I can't even access it. I'm pretty bummed now.

---

