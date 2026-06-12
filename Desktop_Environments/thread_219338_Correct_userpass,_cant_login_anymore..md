---
title: "Correct user/pass, cant login anymore."
date: 2006-07-19
forum: Desktop Environments
---

### Post by paultjeb on 2006-07-19
I was very happy with my installation, untill now. It is impossible to login. I am absolutely sure i am using the correct user/pass, bur the system keeps asking for a user/password.
The Alt-F7 screen shows no errors. 

What can i do to resolve this?

---

### Post by Ramses de Norre on 2006-07-19
Check your keyboard layout!
If that's not the problem you can boot into recovery mode and run ```
passwd user_name
``` to set a new password for your user (there has to be something wrong and that may fix it..)
Then run ```
init 2
``` to get to normal mode.

---

### Post by paultjeb on 2006-07-19
Thanks for the quick reply.
I rebooted in recovery mode, updated the password (typed it twice) and did the init 2 to continue.

Unfortunantely this did not resolve the problem.

---

### Post by Skia_42 on 2006-07-19
You probably already know this but capitalization matters. Make sure you typing your username/password correctly. Also check to make sure caps lock insn't on.

---

### Post by paultjeb on 2006-07-19
Thanks for your reply.

I use a password with a capital, small caps and a number. It is the same password I needed to login as a root to re-enter the userpassword.
When I re-entered the password using 'passwd', I used the same password that I used for user root. 

I am sure capitalisation or keyboard layout is not the problem

---

