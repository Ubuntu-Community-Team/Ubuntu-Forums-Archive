---
title: "/usr/share"
date: 2008-12-16
forum: General Help
---

### Post by sulekha on 2008-12-16
Hi all,

the following is the explanation i have read about /usr/share in a book

Data for installed applications that is architecture&#8722;independent and can be shared between systems. A number of subdirectories with equivalents in `/usr' also appear here, including `/usr/share/doc', `/usr/share/info', and `/usr/share/icons'.

how correct is this explanation ?

---

### Post by ibutho on 2008-12-16
Seems correct. If you want to validate it, take a look at the [File Heirarchy Standard]("http://proton.pathname.com/fhs/pub/fhs-2.3.html").

---

### Post by sulekha on 2008-12-31
That being said, would it be purdent for me to store my music files in /usr/share/mp3 on a server?

I know many people might want to put these in a /home dir but which would best follow the FHS?

---

### Post by nivreial on 2008-12-31
You can put them there, but then remember to chmod them properly so that no one having access to it erases it.

---

### Post by cariboo on 2008-12-31
/usr is not the place to store normal user accessable files. The directory is for executeables, the libraries they need, configuration files and documentation. I would suggest putting your mp3 files in a subdirectory of /home, like /home/mp3 then you can set the permission of the directory to world readable   with having to worry about accidentally changine permissions of a directory in /usr, the may hose your installation.

Jim

---

### Post by dcstar on 2008-12-31
> **cariboo907 said:**
> /usr is not the place to store normal user accessable files. The directory is for executeables, the libraries they need, configuration files and documentation. I would suggest putting your mp3 files in a subdirectory of /home, like /home/mp3 then you can set the permission of the directory to world readable   with having to worry about accidentally changine permissions of a directory in /usr, the may hose your installation.


Quite right, never EVER use system directories for user files.

People, you have a system (Linux) that is flexible and allows you to do stupid things as well as intelligent things, so don't do stupid things by mucking around with system directories and files because they contain a name that saves you typing a few characters somewhere else.

Just read some of the posts in forums like this - bemoaning their loss of data/having to reinstall their system - if you need a lesson in never tampering in places that you shouldn't.

---

### Post by sulekha on 2009-01-01
what about /usr/local/share/mp3

---

### Post by snova on 2009-01-01
> **sulekha said:**
> what about /usr/local/share/mp3

No better. Use your home directory.

The /usr/local tree is identical (well, almost) to the /usr tree. The sole difference is that /usr is meant for the package manager, and /usr/local is meant for programs you install yourself.

**Programs**, not data. Never put any personal files outside of your home directory.

---

