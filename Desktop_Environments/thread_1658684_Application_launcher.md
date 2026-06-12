---
title: "Application launcher"
date: 2011-01-03
forum: Desktop Environments
---

### Post by HughJarse on 2011-01-03
Two things I would like to learn:

[LIST=1]
[*]Make a new application launcher.

[*]Move or edit an existing application launcher.
[/LIST]

Any ideas?

---

### Post by claracc on 2011-01-03
Right click in any empty part of desktop, and a window where you has to fill the name of app, the command to launch and a comment to describe how it works will appear; also you can drag and drop and icon to change the image of launcher.

Other way is through system --> preferences --> main menu, there you select the category and click on new element.

---

### Post by HughJarse on 2011-01-03
Thanks, that helps. However, I have no idea where all applications are found. There is no path showing against the command.
e.g.
Type: Application
Name: Filezilla
Command: Filezilla (browse...)
Desc: ...

---

### Post by matt_symes on 2011-01-03
Hi

> Thanks, that helps. However, I have no idea where all applications are found. There is no path showing against the command.
e.g.
Type: Application
Name: Filezilla
Command: Filezilla (browse...)
Desc: ...

If they are installed in one of your paths, and they usually are, you will not need to add a path to the launcher.

To see your paths (at a terminal type, case sensitive)

```
matthew@matthew-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

If you need to find them, use locate or find from the command line. Or use which 

[http://unixhelp.ed.ac.uk/CGI/man-cgi?locate+1](http://unixhelp.ed.ac.uk/CGI/man-cgi?locate+1)
[http://unixhelp.ed.ac.uk/CGI/man-cgi?find](http://unixhelp.ed.ac.uk/CGI/man-cgi?find)

```
matthew@matthew-laptop:~$ which firefox
/usr/bin/firefox
```

Kind regards

---

