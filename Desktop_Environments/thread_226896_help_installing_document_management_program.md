---
title: "help installing document management program"
date: 2006-07-31
forum: Desktop Environments
---

### Post by ubiwankanubi on 2006-07-31
I am trying to install knowledge tree from the repository.

it installs into usr/share. I copied it to my www/ folder. but now I'm stuck.
I've found an install guide for this, but it seems to refer to a control.ini which wasn't installed. Also, I created the dms database and added a password. but, when I go to the knowledge tree page, It shows a connection error:
[db_error: message="DB Error: connect failed" code=-24 mode=return level=notice prefix="" info=" [nativecode=Access denied for user 'dms'@'localhost' (using password: YES)] ** Array"]

If someone can give me a hand getting knowledge tree, or some other doc management system to work I'd be sooo grateful!

---

### Post by llamakc on 2006-07-31
Where did you read that you should copy it to www? Many programs that are used over http WILL install into /usr/share. The documentation that comes with the program at /usr/share/doc/NAME-OF-PROGRAM should have instructions for setting it up.

---

### Post by ubiwankanubi on 2006-08-01
there are no help or man files in the usr/share/knowledgetree/documents folder.

---

### Post by llamakc on 2006-08-01
That makes sense because Ubuntu keeps them in the:

/usr/share/doc/ directory.

Also, you can check what files were installed with any package with the command:

```


dpkg -L packagename


```

where 'packagename' would be knowledgetree in this instance.

Do this:

`cd /usr/share/doc/knowledgetree`

and start reading up. 

```

root@llamakc:/home/ken # cd /usr/share/doc/knowledgetree/
root@llamakc:/usr/share/doc/knowledgetree # ls
CREDITS        SearchPermissions.txt  changelog.Debian.gz  examples
README.Debian  TODO.txt               changelog.gz         faq.txt
README.txt     UPGRADE.txt.gz         codingStandards.txt  i18n.txt.gz
RELEASE.txt    VERSION.txt            copyright

```

Yep, its right there in the README.Debian file.

---

