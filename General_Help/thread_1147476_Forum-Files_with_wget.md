---
title: "Forum-Files with wget"
date: 2009-05-03
forum: General Help
---

### Post by schipper on 2009-05-03
How can I download attached files from inside of the forum with wget like [http://ubuntuforums.org/attachment.php?attachmentid=109895&d=1239814340](http://ubuntuforums.org/attachment.php?attachmentid=109895&d=1239814340) ?

Thank You and regards

---

### Post by oldos2er on 2009-05-03
```
wget http://ubuntuforums.org/attachment.php?attachmentid=109895&d=1239814340
```

---

### Post by karlr42 on 2009-05-03
No. That just downloads the HTML page.
Wget will only work like that if you give it a path to an actual file.
The forum software won't do that, the only way to download those attachments is to sign up for an account and click on those attachments in a browser.

---

### Post by schipper on 2009-05-04
thanks

---

### Post by pshah on 2009-05-14
You can use wget and pass the Cookie headers which contain your userid and password.

I'm assuming that the forum requires authentication before allowing you to download the attachment files.

---

