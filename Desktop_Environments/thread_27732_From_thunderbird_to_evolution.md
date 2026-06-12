---
title: "From thunderbird to evolution"
date: 2005-04-17
forum: Desktop Environments
---

### Post by robertobech on 2005-04-17
I'm trying to migrate from Thunderbird to Evolution. However, I have no idea how to take my messages from thunderbird to evolution. How can I do it? I have many old messages and don't want to lose them...

---

### Post by tread on 2005-04-17
Looking at the steps in a guide [here](http://www.socklabs.com/node/154) , the same steps should prolly work the other way round too. Backup your email folder though :)

And do let us know if that works!

---

### Post by idn on 2005-04-17
Have you thought about setting up an IMAP account, I did this after get annoyed of backing up and moving my mail folders between my mail clients. Its a little slower because you have to get your mail from the mail server each time, but its alot easier to manage.

---

### Post by robertobech on 2005-04-17
I Did it! Thanks for your help!

In fact, it's very simple: go to the thunderbird folder where your email is stored. For example, for me it was:
mozilla-trhunderbird/robertobech/mail/yahoo.pop/. 

There you have two files for each folder, like "Inbox" and "Inbox.msf". Copy only the first one, "Inbox", to the evolution folder, like this:
evolution/mail/local/.

And that's it! Evolution will index it.

---

