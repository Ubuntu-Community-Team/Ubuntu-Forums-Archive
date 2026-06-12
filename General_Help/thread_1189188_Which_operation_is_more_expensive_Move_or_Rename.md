---
title: "Which operation is more expensive Move or Rename"
date: 2009-06-16
forum: General Help
---

### Post by mrmaster on 2009-06-16
Hello,

I'd like to create a ruby script that parses emails(that will grow with volume) and I need to find a way to distinct which emails the script touches. I can either rename the email after the script is done with the email or move it to another directory. Which would be a least costly operation or are they both equal expensive?

Would you have any other suggestions for this problem?

The way I understand it is that when you rename or change directory you are just changing the path. I think the directories are stored in a tree structure in which rename would be less expensive.

By the way I'm using Ubuntu(ext3)

Thank you

---

### Post by sdennie on 2009-06-16
They are essentially the same operation if you are talking about a single partition for all operations.  You are basically just updating meta-data.

---

### Post by mrmaster on 2009-06-16
It is a single partition and thank you :)

---

### Post by lloyd_b on 2009-06-16
> **sdennie said:**
> They are essentially the same operation if you are talking about a single partition for all operations.  You are basically just updating meta-data.

Just to clarify - using the "mv" command to change the location of a file and using the "mv" command to just change the name of a file is basically the same thing, though actually moving the file *will* take slightly more time (since both the source and destination directories need to be changed).

However, using the "rename" command is something else entirely.  It invokes a Perl script, with the overhead that using Perl entails...

Lloyd B.

---

