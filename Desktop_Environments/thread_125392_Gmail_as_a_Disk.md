---
title: "Gmail as a Disk"
date: 2006-02-03
forum: Desktop Environments
---

### Post by christooss on 2006-02-03
Can I use my gmail account as a disk in Linux?

If yes I really cannot use google at all cause I don't know how to search this simple thing

bye

---

### Post by matthew on 2006-02-03
I remembered seeing this a while back so I did some searching to help you out. The search terms that came up with something were "gmail filesystem." Here's a link...haven't tried it but it should work.

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)

---

### Post by bored2k on 2006-02-03
I believe gmailfs is in the repositories. no wait, it is.
> GmailFS provides a mountable Linux filesystem which uses your Gmail account as its storage medium. GmailFS is a Python application and uses the FUSE userland filesystem infrastructure to help provide the filesystem, and libgmail to communicate with Gmail.

To use GmailFS, please use fuse-source to compile appropriate modules for your running kernel.

GmailFS supports most file operations such as read, write, open, close, stat, symlink, link, unlink, truncate and rename. This means that you can use all your favourite unix command line tools to operate on files stored on Gmail (e.g. cp, ls, mv, rm, ln, grep etc. etc.).

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html) 
[http://packages.ubuntu.com/breezy/utils/gmailfs](http://packages.ubuntu.com/breezy/utils/gmailfs)

---

### Post by Paloseco on 2006-02-18
Use the gmail driver for firefox. You do everything thru GUI. Rocks.

---

### Post by christooss on 2006-02-18
?

What do you mean. WHich extension. Please give me a link

---

### Post by parabolize on 2006-02-20
[gSpace FF extension]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=XUL%20Applications&numpg=10&id=1593")
Requires: Firefox: 1.5 - 1.6a1
Its buggy in linux (at least for me).

---

### Post by bonjun on 2006-02-24
i use the extension but i've got this error/Alert,,,

> Not Found http://google.com/accounts/<html><head><title>Google Accounts
</title><script=type Error while retrieving from server!

---

