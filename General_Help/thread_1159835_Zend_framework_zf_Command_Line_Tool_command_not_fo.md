---
title: "Zend framework zf Command Line Tool command not found."
date: 2009-05-15
forum: General Help
---

### Post by whisher on 2009-05-15
Hi.
I'm trying to set up a zf
application using 
zf.sh (Command Line Tool command)
I've put the Full Package
in my workspace and than
cd workspace/ZendFramework/bin
zf.sh create project quickstart
but I got an not found command.
Can you help me, please ?

Bye.

---

### Post by whisher on 2009-05-15
So I managed 
alias zf.sh=/home/whisher/workspace/ZendFramework/bin/zf.sh
zf.sh create project quickstart

but I got this error

Fatal error: Cannot redeclare class Zend_OpenId_Provider in /usr/share/php/libzend-framework-php/Zend/OpenId/Provider.php on line 44

---

### Post by whisher on 2009-05-15
[RESOLVED] 
I remove by apt-get the 
zend-framework package.
Thanks the same.

Bye.

---

### Post by foxweb on 2009-05-25
> **whisher said:**
> [RESOLVED] 
I remove by apt-get the 
zend-framework package.
Thanks the same.

Bye.
[whisher]("http://ubuntuforums.org/member.php?u=794437"),
I have the same problem(( I've been remove zf package, but I get the same Fatal error.
Please tell me, what you do for resolve this problem. Tnx.

---

### Post by tawfekov on 2009-06-06
I Do had the Same problem ???????
i tried to fix it but i tried it in windows Do any one had solution :p

---

