---
title: "take ownership problems"
date: 2008-07-20
forum: Desktop Environments
---

### Post by bobie on 2008-07-20
I installed Ubuntu on my desktop and I want to copy my files from my user folder in XP from a seperate HD. 

I tried the code sudo chown barry /media/sambo/documents and settings/barry
(barry is my ubuntu user. sambo is the hard drive. barry is the user folder)

I enter my sudo password and get "cannot access '/media/sambo/documents': No such file or directory"
"cannot access 'and': No such file or directory"
"cannot access 'settings/barry': No such file or directory"

I tried renaming the documents and settings folder without the spaces and I tried a variation of CAPS and non caps.

---

### Post by oldschoolrockstar on 2008-07-20
Did you get your window's partition to be  recognized by Ununtu?

---

### Post by bobie on 2008-07-20
Yes. I can physically see my windows hard drive and file system. And I can open and view files from it.

---

### Post by bobie on 2008-07-20
I'm new to Ubuntu and I'm trying to figure this out, but I have thus far been unsuccessful. I'm also unable to log in to the root user account. Please any suggestions.

---

### Post by Tim Sharitt on 2008-07-20
When entering a filename in the terminal, the spaces must be escaped with "\". So you in you case you need to enter 
```
sudo chown barry /media/sambo/documents\ and\ settings/barry
```

---

