---
title: "Shell Script for vpnc"
date: 2006-07-30
forum: Desktop Environments
---

### Post by gandalf2041 on 2006-07-30
I am attempting to write a quick shell script for vpnc.  One of the lines in the directives in the conf file is "Xauth password".  The problem is that my network password contains a special character "@" so that when I run the conf file, I get an "authentication unsuccessful" error.  How do I enter this special character in the conf file so that it is interpreted correctly? (No...changing the password is not an option:rolleyes: ) Any help would be greatly appreciated.

Gandalf2041
Dapper Drake 6.06

---

### Post by fabiand on 2006-07-30
Hey,

I don't completely understand what you mean, but you miht "escape" the character or password:

escape password:
'passwordwith@sign'   (The ' are important!)

escape character:
passwordwith\@sign    (The \ is important!)

---

### Post by gandalf2041 on 2006-07-30
Hmm, I tried \@ and 'p@ssword' but I didn't try them in combination.  Thanks for the advice.  I'll give it a try and report back.:)

---

### Post by gandalf2041 on 2006-07-30
That didn't seem to work either. Oh well, I guess having to enter the password manually is more secure anyway :-k  Time for a book on shell scripting!

---

