---
title: "encryption algorithm File Roller"
date: 2010-11-26
forum: Desktop Environments
---

### Post by nicolaas3 on 2010-11-26
Does anybody know what kind of encryption algorithm does File Roller use when you protect a file with a password?

Nicolaas

---

### Post by koleoptero on 2010-11-26
Since file-roller is just a frontend I don't think it uses any particular encryption mechanism. You should look into the respective command-line tools it uses to find that out. In what format do you save the files? If it's zip then you should look at zip's encryption method. If it's tar then tar's. etc.

---

