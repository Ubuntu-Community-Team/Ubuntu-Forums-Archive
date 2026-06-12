---
title: "Kuser"
date: 2005-08-22
forum: Desktop Environments
---

### Post by pedromsouza on 2005-08-22
Hi, I'm starting to use linux now.... 
I'd like to know how to configure kuser. I want to use my personal acc with all privileges of root acc.

Please help me and thanks.

* I tryied to install firefox but it didn't work. Can it be related to this issue?

---

### Post by Takis on 2005-08-22
[QUOTE=pedromsouza]Hi, I'm starting to use linux now.... 
I'd like to know how to configure kuser. I want to use my personal acc with all privileges of root acc.
[/quote]
In the nicest way possible: bad idea. Very bad idea. You will have the potential to delete or modify in a bad way everything and anything in your system 100% of the time. A badly placed 'rm' command has the potential to wipe your entire system without even prompting for confirmation.

Instead, (if you're using the account you created at install time) your account is what's known as a 'sudo user' account. To run any command as root, type 'sudo <command>'. It will ask you for a password, this is your normal password. It's like it's confirming that you want to run a command with root priviledges.

> * I tryied to install firefox but it didn't work. Can it be related to this issue?
Possibly. How did you try to install Firefox? I was under the impression it was installed with a default Kubuntu setup anyway.

---

