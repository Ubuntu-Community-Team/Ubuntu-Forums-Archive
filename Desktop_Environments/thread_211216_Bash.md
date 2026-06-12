---
title: "Bash ?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-07-07
**[SIZE="5"][/SIZE]**

I am doing my first BASH tutorial from Keir Thomas' Beginning Ubuntu Linux.
I am having problems with less command.  What I want to do is to open an openoffice readme from the terminal and then practice navigating the document.  Later, I will cp this readme and practice with vi.

The problem is I can't find the readme.

When I enter per Thomas' instruction:

code  less/usr/lib/openoffice2/README   code

I get "No such file or directory."

OK, so then I tried locate openoffice readme and then I tried less with this combination:

code    less /usr/lib/openoffice/share/readme  code

but then I get " . . . is a Directory."

So what is going on and how do I find this readme document from the terminal??:-k

Duh!!   P.S. How do I get the code field for this forum???

---

### Post by scxtt on 2006-07-07
[ code ][ /code ]

without the spaces ...

---

### Post by FredB on 2006-07-08
> **Kurt_Alan said:**
> 

I am doing my first BASH tutorial from Keir Thomas' Beginning Ubuntu Linux.
I am having problems with less command.  What I want to do is to open an openoffice readme from the terminal and then practice navigating the document.  Later, I will cp this readme and practice with vi.

The problem is I can't find the readme.

When I enter per Thomas' instruction:

code  less/usr/lib/openoffice2/README   code

I get "No such file or directory."

OK, so then I tried locate openoffice readme and then I tried less with this combination:

code    less /usr/lib/openoffice/share/readme  code

but then I get " . . . is a Directory."

So what is going on and how do I find this readme document from the terminal??:-k

Duh!!   P.S. How do I get the code field for this forum???

erh...

less   /usr/lib/openoffice/share/readme ?

Erh. It is empty. And it is a directory.

It looks like it is "ls", not less.

ls => dir like command
less => viewing the content of a text file.

also, when doing a full ls on /usr/lib/openoffice/share/readme, I get :

```

fred@fredo:~$ ls /usr/lib/openoffice/share/readme/ -al
total 8
drwxr-xr-x  2 root root 4096 2006-05-25 06:33 .
drwxr-xr-x 20 root root 4096 2006-05-25 11:50 ..

```

What the point about viewing the content of an empty directory ?

---

### Post by Kurt_Alan on 2006-07-08
****

You are speaking over the head of this new user!  Let me simplify my question:

At the terminal, what command syntax should I enter to find the openoffice readme document??

---

