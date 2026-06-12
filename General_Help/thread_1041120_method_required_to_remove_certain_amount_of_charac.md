---
title: "method required to remove certain amount of characters from several lines"
date: 2009-01-16
forum: General Help
---

### Post by Rytron on 2009-01-16
Hi,
I need a method to remove certain amount of characters from several lines.

For example in the lines below, I want to remove the first 29 characters: 
/home/user/Documents/Animals/Animal-List
/home/user/Documents/Animals/Cat-Breeds-List
/home/user/Documents/Animals/Cat in differant languages
/home/user/Documents/Animals/dog-breeds-list.ods
/home/user/Documents/Animals/pets

so that I get

Animal-List
Cat-Breeds-List
Cat in differant languages
dog-breeds-list.ods
pets

---

### Post by lswb on 2009-01-16
Are these lines in a file or appearing on standard output as a result of running a command, or ?

One way would be to pipe these lines to the "cut" command: For cutting everything preceeding the 30th byte, the command would be 
"cut -b30- " Cut can also work on fields defined by a certain character, so for your example, " cut -d'/' -f5 " would also work. You may also be interested in the "basename" command.

---

### Post by redilyn on 2009-01-16
Is this from a document??

If you are using open office just use find/replace

Search For =  /home/user/Documents/Animals/
Replace with = NULL (ie nothing)

Should do the trick

---

### Post by Rytron on 2009-01-16
> **redilyn said:**
> Is this from a document??

If you are using open office just use find/replace

Search For =  /home/user/Documents/Animals/
Replace with = NULL (ie nothing)

Should do the trick

Beautiful. The simplest solutions are the best. I tried it in Gedit, works like a charm.
Cheers.

:popcorn:

---

### Post by Rytron on 2009-01-16
> **redilyn said:**
> Is this from a document??

If you are using open office just use find/replace

Search For =  /home/user/Documents/Animals/
Replace with = NULL (ie nothing)

Should do the trick

I selected all files in a folder, then copied and pasted into a text file.

---

