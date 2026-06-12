---
title: "Perl/TK not found in the Synaptic Package Manager"
date: 2006-09-28
forum: Desktop Environments
---

### Post by antheo on 2006-09-28
Hi,

I am trying to install GuitarTex on Ubuntu 606. GuitarTex requires Perl/TK. 
I can not find Perl/TK in the Synaptic Package Manager.
Does it have another name?

Thanks,

antheo

---

### Post by lagagnon on 2006-09-28
I believe Perl/Tk is already installed on a base Ubuntu system...

---

### Post by antheo on 2006-09-28
Would you know why i am getting the following error then?

Can't locate Tk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/bin/guitartex line 3.BEGIN failed--compilation aborted at /usr/local/bin/guitartex line 3.

---

### Post by lamego on 2006-09-28
The perl TK module is not included on the base install, you can install it with:
```
sudo apt-get install perl-tk
```
You could have found it:
```
apt-cache search perl tk
```

---

### Post by antheo on 2006-09-28
I tried the command 
root@ubuntu:/home/ubuntu# sudo apt-get install perl-tk

and here is the result:

Reading package lists... Done
Building dependency tree... Done
Package perl-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package perl-tk has no installation candidate

---

### Post by christhemonkey on 2006-09-28
You need to add all the repositories.

I believe it is in the universe repository.

See here for a howto:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by lukew on 2007-01-01
> **antheo said:**
> I tried the command 
root@ubuntu:/home/ubuntu# sudo apt-get install perl-tk

and here is the result:

Reading package lists... Done
Building dependency tree... Done
Package perl-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package perl-tk has no installation candidate

Hi,

Just installed GuitarTeX today. The only thing I needed to install was perl-tx which is in the universe repo. Sounds like you need to add some more repos into your sources list.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html#id2580924](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html#id2580924)

or 

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Cheers 

Luke

Perhaps once you are up and running with this we can pm each olthers chord files (save us both having to tediously type them all in!! (any one else got any chord files? ) :)

---

### Post by antheo on 2007-01-01
What version of Ubuntu are you using? 6.10? I am still on 6.06. I tried to upgrade to 6.10 from 6.0.6 but i encountered errors.

---

### Post by lukew on 2007-01-08
> **antheo said:**
> What version of Ubuntu are you using? 6.10? I am still on 6.06. I tried to upgrade to 6.10 from 6.0.6 but i encountered errors.

Using Dapper (6.06).

Luke

---

### Post by antheo on 2007-02-12
Thanks a lot for the tip. I finally got Perl/TK installed and succeeded to launch GuitarTex. 
However the menu are in German. Any idea how to display the menu in English?

---

### Post by antheo on 2007-02-12
I have modified the language option in the file "~/.guitartexrc" but it is not read when i launch ~/guitartex but it is read when i open the file guitartex with the file browser! 
Why such a difference?

---

