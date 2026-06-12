---
title: "Problems installing from scripts when package install has prompts."
date: 2009-03-24
forum: General Help
---

### Post by theolster on 2009-03-24
Hi - I'm having a problem writing a script to install a package. The specific package is mysql-server.

The install process asks me to enter a root password, which I want the script to do automatically. As I understand there must be a way of doing one of two things:

a) either get the script to enter the string into the prompt or
b) ignore the prompt and carry on with the process so that I can configure the mysql root password from within the script later on.

My script currently looks like this:
```
#!/bin/bash
sudo apt-get -y --force-yes install mysql-server
```

Does anyone have any thoughts on this? I also foresee having problems with the phpmyadmin package too.

---

### Post by theolster on 2009-04-18
This is a bump. (It has been 3 weeks now)

---

