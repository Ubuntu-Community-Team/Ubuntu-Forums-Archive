---
title: "OpenOffice and Ubuntu"
date: 2009-05-12
forum: General Help
---

### Post by setuck on 2009-05-12
Seems i cannot open a file across a mac network with opeenoffice on a ubuntu pc....i have gnome installed....many sites say fix the MIME settings.....help

---

### Post by LoneWolfJack on 2009-05-12
what kind of error message do you get or how does the program not work more precisely?

maybe you should also have a look at this if you expect people to provide fast and helpful assistance:
[http://catb.org/esr/faqs/smart-questions.html](http://catb.org/esr/faqs/smart-questions.html)

---

### Post by bigboy_pdb on 2009-05-12
To choose what program opens a file you can edit "/etc/mime.types".

The folder "/usr/share/mime/application" contains xml files. Each file name (without the xml) is used to indicate what program is used to open a file type. The following is an example.

```


# This will open an open document text file using open office text

application/vnd.oasis.opendocument.text                         odt


```

I'm not certain if you have to run a program for the changes to take affect.

---

### Post by albinootje on 2009-05-12
> **setuck said:**
> Seems i cannot open a file across a mac network with opeenoffice on a ubuntu pc....i have gnome installed

In my experience OOO has problems with samba-shares which are used through Nautilus or Konqueror.
Mounting the samba shares manually (or in my case via autofs) works 
without any problems.
Perhaps you're encountering the same problem ?

Which protocol is in use in the Mac network ? Smb, NFS or what ?

---

