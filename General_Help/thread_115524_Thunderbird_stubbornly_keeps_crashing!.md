---
title: "Thunderbird stubbornly keeps crashing!"
date: 2006-01-10
forum: General Help
---

### Post by louis_nichols on 2006-01-10
Hi!

Here's my problem: whenever I try to open some windows in thunderbird (like write or account settings), it crashes. The output is:

myself@home:~$ mozilla-thunderbird
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159:  9627 Segmentation fault    "$prog" ${1+"$@"}


Now what I usually do is, after a fresh install of Linux, I copy the mail folder and prefs.js files from my windoze partition in .mozilla-thunderbird directory, to keep my e-mails and account settings. It's always worked before without problems. But now, it just crashes. I also got this erros that it could not write to the mail folder, so I changed the permissions for the whole profile folder, to be able to at least receive mails.

Please help! I'm becoming pretty desperate with this. ](*,)

---

### Post by zoiks on 2006-01-10
Well, the last line in your errors is a clue, since it tells you where in the script it's failing.  Alas, I am not able to interpret that line!

In any case, does it work fine if you don't copy over your mail files first?  Can you import the messages to Thunderbird from your windoze partition *after* getting Thunderbird to work fine?

---

### Post by aysiu on 2006-01-10
Have you checked the ownership and permissions on those files and folders you're copying over?

---

### Post by louis_nichols on 2006-01-11
yes, it works just fine if I don't copy the filesw from my ntfs partition, and the files are  all owned by my user, with permissions set to 700.

---

