---
title: "cant change directories?"
date: 2009-05-22
forum: General Help
---

### Post by bolweval on 2009-05-22
Hi, Im new to linux/ubuntu so bear with me.

I can not change directories in the terminal, when I try I get "no such file or directory" I'm trying to install a driver for a linksys wireless usb network adapter, a wusb300n. The command I am typing in is cd ~/public which is where the driver is. I cant seem to change to ANY dir from the terminal?  HELP!!

---

### Post by michy99 on 2009-05-22
First of all, make sure that public is a directory in your home directory. When you enter```
ls
```do you see it listed?

---

### Post by taurus on 2009-05-22
Linux/Unix is case sensitive so ~/Public is not the same as ~/public.

Perhaps you mean ~/Public.

```
cd ~/Public
```

---

### Post by bolweval on 2009-05-22
Yes it is there. I cant cd to any folder, get the same silly message? "no such file or directory"

---

### Post by bolweval on 2009-05-22
> **taurus said:**
> Linux/Unix is case sensitive so ~/Public is not the same as ~/public.

Perhaps you mean ~/Public.

```
cd ~/Public
```

Thanks, tried that, same thing ; (

---

### Post by taurus on 2009-05-22
Can you at least post the output of this command from a terminal?

```
ls -l ~
```
Which directory are you trying to change to from the output above?

---

### Post by michy99 on 2009-05-22
What is the result of```
ls -d -l ~/public
```

---

### Post by gradysghost on 2009-05-22
First off, the tilde (~) is a shortcut symbol that represents the full path of your home directory.  Try this:

[CODE]cd ~
ls[CODE]

If a directory entitled "public" exists, it will print out somewhere in that list.  Also, if you're used to Windows, you may not realize that Linux is case-sensitive in all matters.  For instance, a folder called "Public" can coexist with a folder called "public".  Make sure you're using the proper case.

A nifty trick is to type the first two or three characters of the file or folder name and then press the Tab key.  If it doesn't auto-complete the filename, then it either doesn't exist or there are mutiple files that begin with those letters.  If you're in the containing folder and run the ls command as shown above, you should be able to find out the exact case of the directory.

---

### Post by bolweval on 2009-05-22
Thanks everyone, It was the case sensitive problem I was having, problem solved, and the driver is working, after i did 
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9" anyway, whew, my brain hurts  ; )

---

