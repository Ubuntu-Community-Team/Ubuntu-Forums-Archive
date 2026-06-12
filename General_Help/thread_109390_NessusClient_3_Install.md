---
title: "NessusClient 3 Install"
date: 2005-12-28
forum: General Help
---

### Post by ztrek7 on 2005-12-28
I have successfully installed Nessus 3. I can run the WINDOWS client fine. But, I cannot install the linux client. 

sudo ./configure is a success,

sudo make 
sudo make install are not

I have the backports as a repository, but nessusclient is not there. Does anyone know of a .deb package or if there are plans for it in a repository?

You guys probably want the error message, I am not at the machine now. If you need it, I will post. But, really just would like a .deb!

---

### Post by rrinker on 2006-01-17
Ever get this going? I just installed Nessus 3 and I can start nessusd just fine (as root) but I cannot get my registration or the first user to execute no matter how I run it - GUI terminal as me, GUI Run As root, or boot to a console.
 I previously as Nessus 2 installed from the repository and it was working fine. But for the project I am working on I need Nessus 3, so I removed 2 before trying to install 3.

                --Randy

---

### Post by padraig on 2006-01-31
Hi, perhaps you need to create a user first. Instructions at: [http://www.informit.com/articles/article.asp?p=26263&seqNum=4&rl=1](http://www.informit.com/articles/article.asp?p=26263&seqNum=4&rl=1)

---

