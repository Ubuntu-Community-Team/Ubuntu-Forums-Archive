---
title: "Acroread Fault"
date: 2005-02-09
forum: Desktop Environments
---

### Post by Alessio on 2005-02-09
I have apt-getted acroread but...

alessio@Ubuntu:~ $ acroread
/usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: No such file or directory

---

### Post by benjamin on 2005-02-09
You have to modify somethings .... there is a bug.

First
	cd /usr/lib/Acrobat5/bin
	mv acroread.sh acroread

Then

	sudo gedit acroread

and change

	install_dir=/usr/lib/Acrobat5/reader


Bye

---

### Post by Alessio on 2005-02-09
[QUOTE=benjamin]You have to modify somethings .... there is a bug.

First
	cd /usr/lib/Acrobat5/bin
	mv acroread.sh acroread

Then

	sudo gedit acroread

and change

	install_dir=/usr/lib/Acrobat5/reader


Bye[/QUOTE]
 tx

---

