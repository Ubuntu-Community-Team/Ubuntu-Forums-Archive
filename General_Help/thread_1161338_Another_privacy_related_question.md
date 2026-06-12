---
title: "Another privacy related question"
date: 2009-05-16
forum: General Help
---

### Post by GL_NORWAY on 2009-05-16
I've earlier asked about a full system encryption solution for Ubuntu. After searching trough this forum for *encryption*, I get the impression that a full system encryption is more or less a Windows-thing since Windows stores a lot of sensitive data all around. For Linux it seems like the only thing you need to encrypt -- or clean up -- is the /home dir and swap area.

Also: What about third-party software in Ubuntu? Do they all store their history and temp files in the /home?

Do you have any knowledge or opinions about his? Thanks!

---

### Post by Legace on 2009-05-16
> **GL_NORWAY said:**
> I've earlier asked about a full system encryption solution for Ubuntu. After searching trough this forum for *encryption*, I get the impression that a full system encryption is more or less a Windows-thing since Windows stores a lot of sensitive data all around. For Linux it seems like the only thing you need to encrypt -- or clean up -- is the /home dir and swap area.

Also: What about third-party software in Ubuntu? Do they all store their history and temp files in the /home?

Do you have any knowledge or opinions about his? Thanks!

Yeah, I think all "important" (in terms of privacy) things are stored in /home.

---

### Post by HavocXphere on 2009-05-16
I don't know the answer to your question, but I'm sure there is some sort of disk monitoring software that you can use to check where the app in question is writing to. (i.e. a *nix equivalent of filemon)

---

### Post by paradigm2 on 2009-05-16
> **GL_NORWAY said:**
> I've earlier asked about a full system encryption solution for Ubuntu. After searching trough this forum for *encryption*, I get the impression that a full system encryption is more or less a Windows-thing since Windows stores a lot of sensitive data all around. For Linux it seems like the only thing you need to encrypt -- or clean up -- is the /home dir and swap area.

Also: What about third-party software in Ubuntu? Do they all store their history and temp files in the /home?

Do you have any knowledge or opinions about his? Thanks!

I have heard that loop-aes can do system encryption.

About the tmp files, no they might store files in /tmp (very common) or theoretically anywhere else where they can and have write permission.  In general though most apps use /tmp or other documented places and are well behaved.

---

### Post by GL_NORWAY on 2009-05-16
> **paradigm2 said:**
> I have heard that loop-aes can do system encryption.

That application goes far above my computer/Linux knowledge. :(

Either I have to go back to Windows or figure out how and where Ubuntu stores things. You see, It's important for me to protect my business and privacy.

---

