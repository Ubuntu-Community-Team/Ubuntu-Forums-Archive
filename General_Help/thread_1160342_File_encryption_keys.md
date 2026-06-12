---
title: "File encryption keys?"
date: 2009-05-15
forum: General Help
---

### Post by dgrafix on 2009-05-15
I need to open a document on my other machine but it says i dont have the key.
I am glad i found this out now!! i thought it was password based encryprion.
How do i transfer and back up my key??

---

### Post by hangfire on 2009-05-15
> **dgrafix said:**
> I need to open a document on my other machine but it says i dont have the key.

What kind of document, open office, an encrypted Zip file, just what is it?

Open it, how? Over NFS, Samba, file copied over?

Does the original open OK?


> **dgrafix said:**
> 
I am glad i found this out now!! i thought it was password based encryprion.
How do i transfer and back up my key??

What kind of encryption are you using? Luks (Linux Unified Key Setup) is the key archiver of choice.

-HF

---

### Post by dgrafix on 2009-05-15
Where you right click and encrypt in nautilus.

I have tried exporting the key with that tool in accessories and imported it on the other machine but it keeps saying "you dont have the key" when i attempt to decrypt it. Opens fine on the original machine though.

---

### Post by bbala2020 on 2009-05-23
Even i face the same problem.. How do i use that password and encryption keys?? For what all purposes can i use that. the help just explains the options but not how and y to use them.. HELP :^o

---

### Post by dgrafix on 2009-05-29
Yep still having problems, i managed to work it out in the end and import the key and could open it, but encrypt it on this machine and now it has problems the other way round!:

This is dangerous and should have warnings of some sort. People could think their files are safely encrypted with a password, back them up, hard disk crashes loosing the original key .... and BOOM . (nowhere upon encrypting does it explain/warn that  separate key needs to be exported and saved. I was under the assumption it was encrypted using the password/phrase as the rotation key)

---

