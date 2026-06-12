---
title: "Where's the gnome session file?"
date: 2008-12-14
forum: General Help
---

### Post by FIONEX on 2008-12-14
What happened to the gnome session file?  I can't find it.  I want to change the starting order of applications as gnome loads...

Thanks!

---

### Post by linux_tech on 2008-12-14
/home/yourname/.gnome

```
cd /home/yourname/ 
```

```
ls -a 
```(now you see ALL the files, including hidden ones)

```
gedit .gnome
```

[http://node1.yo-linux.com/cgi-bin/man2html?cgi_command=gnome-session](http://node1.yo-linux.com/cgi-bin/man2html?cgi_command=gnome-session)

---

### Post by FIONEX on 2008-12-14
I get an error saying:
```

/home/fionex/.gnome is a directory.

```

Maybe this is because I'm on Ubuntu 8.10 Intrepid

---

### Post by FIONEX on 2008-12-14
This is ridiculous.  Why would ubuntu change from the Gnome standard?  I still can't find any default session file or the user session file.  "man gnome-session" clearly says the file is "~/.gnome2/session", which doesn't exist and neither does a default session file.  What ever happened to documentation...

---

### Post by drs305 on 2008-12-14
> **FIONEX said:**
> I want to change the starting order of applications as gnome loads...

A workaround is to create a script and reference it in Sessions. The script would list the applications you want to run, listed in the order you want them to start. At the end of the command add a "&" so the next command can run. If needed, you can place a *sleep XX* command to create a delay before the next command begins.

Make the script executable and place run command for the script in the Sessions, Startup Programs list.

---

### Post by FIONEX on 2008-12-14
> **drs305 said:**
> A workaround is to create a script and reference it in Sessions. The script would list the applications you want to run, listed in the order you want them to start. At the end of the command add a "&" so the next command can run. If needed, you can place a *sleep XX* command to create a delay before the next command begins.

Make the script executable and place run command for the script in the Sessions, Startup Programs list.

haha genius!  that's a good idea.
If you ever figure out where gnome stores the programs to run at the start of a session, please let me know.  I'd still like to know for the purpose of expanding my knowledge.

---

