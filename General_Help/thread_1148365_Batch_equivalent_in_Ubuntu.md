---
title: "Batch equivalent in Ubuntu?"
date: 2009-05-04
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-04
Hi, many must know about batch (or *.bat) files in Windows. Is there an equivalent of this in Ubuntu? It'd be quite an advantage if Ubuntu had something like this.

Thanks for any help.

---

### Post by lucianct on 2009-05-04
yeah, bash scripts. you will find plenty of them in /usr/bin/

---

### Post by b@sh_n3rd on 2009-05-04
wow...cool...now that was fast..:D Thanks lucianct. The scripts work with python is it?

---

### Post by geirha on 2009-05-04
Check out Bash Guide for Beginners: [http://tldp.org/guides.html](http://tldp.org/guides.html)

---

### Post by Psicolonia on 2009-05-04
they work with pretty much anything.

python, pearl, random shell scripts... (commands in order)

if you open a text file and write the commands as you would on a batch file like:

gedit mybat.sh

and than write "ls -la" and save it.

you got yourselft a batch. the only thing you need is to make that executable. like this:

chmod +x mybat.sh

and then execute it to try out:

./mybat.sh

---

