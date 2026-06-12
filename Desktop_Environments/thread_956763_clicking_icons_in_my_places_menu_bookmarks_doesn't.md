---
title: "clicking icons in my places menu bookmarks doesn't open folders"
date: 2008-10-23
forum: Desktop Environments
---

### Post by ubukool on 2008-10-23
Hi friends,

I've installed Intrepid beta which is absolutely wonderful apart from I'm having problems with my 'places' menu bookmarks.  

The icons look wrong - they look like root user icons instead of the regular icon theme I've installed and when you click them, Nautilus does not open the folder they are pointing to.  

I haven't had this problem in any other release of Ubuntu and I've been onboard since Dapper. Does anyone have any idea what's wrong and how it might be fixed?

Thanks in advance for your help!

---

### Post by rem on 2008-11-10
Hello, 

I don't know if you managed to fix this or not, I had the same problem and here's what I did:

go to .local/share/applications/mimeapps.list and search for inode/directory= ....... line. 
mine was inode/directory=audacious.desktop getting audacious instead every time i was trying to open a folder from the bookmarks. 

it should be

```
inode/directory=nautilus-folder-handler.desktop;
```

this bug has been dealt with here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

Cheers!

---

