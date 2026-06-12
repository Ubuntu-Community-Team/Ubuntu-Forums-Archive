---
title: "ksh - do we have one ?"
date: 2005-12-07
forum: General Help
---

### Post by dotdot on 2005-12-07
hi folks,

I have a few scripts in ksh which i'd like to use .... however 
they don't work in bash.

I see there is pdksh for 5.04 however not for 5.10.

Anyone know what I can do to resolve this problem ?

..Rgds

..

---

### Post by daller on 2005-12-07
The package "pdksh" IS in the main repo of Breezy...

---

### Post by dotdot on 2005-12-07
thanks for your reply.

..I'm pretty new to ubuntu so may have 
some pretty simple questions.

I'm currently using 5.10 (laptop) not connected to the 
net (typing from desktop at work:).

..can I get pdksh off my cd distro or dl the package in 
a format i can then install.(then if so how do i install it?).

thanks for your help.

..

---

### Post by dotdot on 2005-12-07
sorted it - here's howto :

goto [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
select [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

spot 
1.3.	

Where can I find a list of all the programs and libraries that come with Ubuntu?
select
[http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)

select shells

[http://packages.ubuntu.com/breezy/shells/](http://packages.ubuntu.com/breezy/shells/)

select pdksh
[http://packages.ubuntu.com/breezy/shells/pdksh](http://packages.ubuntu.com/breezy/shells/pdksh)

download deb file - copy to dest box.

boot up (lappy into ubu) 

- exec 
sudo dpkg - <file>

...all sorted.

...and all from the first resp - thanks again.

..

---

