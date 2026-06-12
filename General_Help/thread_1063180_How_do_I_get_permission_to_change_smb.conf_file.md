---
title: "How do I get permission to change smb.conf file?"
date: 2009-02-07
forum: General Help
---

### Post by scotttie on 2009-02-07
Hi everyone,
I need to change workgroup name and although I am logged in with full permissions it wont let me save the file (says "You do not have the necessary permissions to save the file.").
any help greatly appreciated.
Scottie

---

### Post by Monotoko on 2009-02-07
run this from the command line:

```
sudo gedit [file path]
```

You will then be able to edit the file as root, any files that are not in your home directry are automatically owned by root, therefore you have to use sudo.

To access your filesystem as root, use

```
sudo nautilus
```
^ only use that when you need it, and close it immediatly after you have done what you need to.

---

### Post by terry_gardener on 2009-02-07
the commands should be gksu or gksudo for using root privileges for graphical applications. 

sudo nautilus should be: 
gksudo naultilus

and sudo gedit <filename> should be 
gksudo gedit <filename> 

check [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo") for more information

---

