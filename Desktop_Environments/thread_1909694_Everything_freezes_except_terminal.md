---
title: "Everything freezes except terminal"
date: 2012-01-15
forum: Desktop Environments
---

### Post by rhnoble on 2012-01-15
Booting off a USB in Ubuntu 11.10 and 12.04 I get no response to mouse clicks after a few minutes, and any window i open immediately stops receiving input. Keyboard seems to work for longer than the mouse. I can continue to open new windows and programs for several minutes but they all freeze as soon as they launch. I can open a terminal with the keyboard shortcut and it seems to work okay. I was running fine with the same hardware for about 2 months before this started. I pretty much don't know what I'm doing, so let me know what info I can give to to make the problem more clear.

Thanks in advance

---

### Post by Buntumatic on 2012-01-15
Run top on terminal to see what's hogging up resources.

---

### Post by rhnoble on 2012-01-15
Here's a screenshot of top. I'm sure I'm showing my lack of knowledge, but it's weird that there's 0 swap right?

---

### Post by Buntumatic on 2012-01-15
Lack of swap is weird considering it's a part of standard Ubuntu setup, but certainly not fatal with the amount of RAM you have.
However, why are you having so many users? If you are the only one logged in then there definitely is something wrong.

---

### Post by rhnoble on 2012-01-15
I'll post a list of the users as soon as I can get a screen capture to work. My understanding is that it's normal to have multiple users as some programs create their own users. Doing a little googling I've found sources saying that having significantly more than 7 users is normal.

---

### Post by rhnoble on 2012-01-15
Alright, anything look unusual about that?

---

### Post by Buntumatic on 2012-01-16
What is **users** output?

---

