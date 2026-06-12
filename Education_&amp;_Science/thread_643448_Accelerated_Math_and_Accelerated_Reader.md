---
title: "Accelerated Math and Accelerated Reader"
date: 2007-12-17
forum: Education &amp; Science
---

### Post by at78rpm on 2007-12-17
Hope this is the right forum for this question.

Has anyone been able to run Accelerated Math or Accelerated Reader off a Win2003 server?  Whenever I try, I can get Wine to run it, but it can't locate the data folder needed to actually run the program.

I have a Linux geek who's tried to do this, too, but can't figure it out.  It's beginning to make me wish I'd had the patience to stick with Win XP!

---

### Post by xeth_delta on 2007-12-17
Where should that directory be located, in /home/user_name? Have you tried performing a search for files that should be in the directory?

```
find * | grep -i file_name_or_part_of_file_name
```

---

### Post by at78rpm on 2007-12-23
The data directory is and must be located on the Win2003 server.  100 WinXP workstations use that directory.  I'm just hoping to get Ubuntu to do the same,  but it's not working.

---

### Post by xeth_delta on 2007-12-23
It is quite possible the files distribution on a linux box will be different to that in a Windows machine, so the fact that you find that directory in the windows user directory would not imply it will be in the same place for ubuntu.

If it is a configuration file, it is quite possible the installation process placed the directory in /etc/..., /usr/..., /usr/local/... or /opt/....

Have a look in those places, perform a search in the way I described for the file you need.

Xeth

---

### Post by Ardent Maverick on 2008-10-17
I have an entire LAUSD public school, Hollenbeck Middle School, in Boyle Heights, Los Angeles, that needs to be able to run Accelerated Reader or a FOSS equivalent.  If the program as it exists cannot be easily crossed over commercially, an open-source competitor must suffice it. The world (OLPC) needs it. A FOSS alternative.  English is indeed the globalized language.

---

