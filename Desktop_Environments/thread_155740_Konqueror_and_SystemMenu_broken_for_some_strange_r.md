---
title: "Konqueror and SystemMenu broken for some strange reason"
date: 2006-04-05
forum: Desktop Environments
---

### Post by kdnewton on 2006-04-05
Hiyall.

I recently ran the Automatix script on my PC here to get my DVD player working properly.

Before I ran Automatix, the System Menu browser from the panel worked properly, and so did Konqueror.

Now, however, when I go to browse /home/myhome I get the following errors.

---
Error - Konqueror
Malformed URL
$HOME        <-- or /home/myhome or whatever I put there
---

---
Error - KDE Panel
The file or folder system:/home.desktop does not exist.
---

Am I missing something obvious here? Thanks.

---

### Post by dermotti on 2006-04-05
Do you have a Desktop folder in your /home/yourname/ folder?

---

### Post by kdnewton on 2006-04-05
That is a good question, and not one that I would ever have thought to look for before asking here.

Unfortunately, yes. I do have a /home/userName/Desktop/ directory.

This is my output for my Desktop:

username@PCname:~/Desktop$ ls -l *
-rw-r--r--  1 username username 4807 2006-03-21 10:22 trash.desktop

---

### Post by dermotti on 2006-04-05
I would create a new account and see if that account has the same issue. You may have just borked something on that account.

---

### Post by kdnewton on 2006-04-06
Nice. Of course, the scientific method.

I created a new account. I restarted the computer. I logged in with the new account and viola, Konqueror worked again.

So I logged out of that account and logged in with my original account. Konqueror/System Menu worked! Maybe I should have tried rebooting the computer the first time.

Thank you.

---

