---
title: "Quick help, &quot;Private&quot;-Folder and ext4"
date: 2009-02-14
forum: General Help
---

### Post by keine_ahnung on 2009-02-14
Hi everybody. I am reinstalling my PC at the moment using the new Kubuntu 9.04 Alpha 4 amd64 release. Right now the backup copy job is running and I wonder if it's possible to access my "private" (encrypted) folder without the original environment. Where is the actual data stored and how can I access it? I remember I set a password therefore... 

Second question, as I have the option to switch to ext4: If there are major updates/changes done to the filessystem until the final release of 9.04, is this updateable (is this a real word? xD)? So, may I run in troubles if I use the ext4 FS, or can I run updates here? Excuse me if this is total nonsense, I don't know that much about filesystems... 

Hope you can offer me quick help, need to finish the installation within today :)

Thanks everyone!
Daniel

---

### Post by keine_ahnung on 2009-02-14
While waiting for a reply I found a explanation here [1] and tried to mount it. Then I realized that all data from my Private Directory are in there without any encryption. WTF? I am running a Live CD of Kubuntu 8.10 without using any password or anything that could give me access to that folder. So if you can access that folder so easily (I guess through the key file in the stated ~/.ecryptfs directory) what is it actually good for? Am I missing something?

[1] [https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

---

### Post by sdennie on 2009-02-14
> **keine_ahnung said:**
> 
Second question, as I have the option to switch to ext4: If there are major updates/changes done to the filessystem until the final release of 9.04, is this updateable (is this a real word? xD)? So, may I run in troubles if I use the ext4 FS, or can I run updates here? Excuse me if this is total nonsense, I don't know that much about filesystems... 


I'm not sure about your first question.  However, ext4 was deemed stable in 2.6.28 and any changes to ext4 will be backwards compatible with what is in 2.6.28 (which is the Jaunty kernel).  So, yes, it's safe to use ext4.

---

