---
title: "Windows borders and xcleardiff problem"
date: 2006-02-16
forum: Desktop Environments
---

### Post by topolino on 2006-02-16
Hello,

I have just upgraded my laptop from Ubuntu 5.04 to Ubuntu 5.10. It went fine. However, I am facing a problem at work that I did not have with Ubuntu 5.04.

At my office, I work in a HP-UX (11.11) environment. In that environment, we use Clearcase (v4.2). For some unknown reason, the xcleardiff tool always crashes the windows borders of the open windows in Ubuntu 5.10. In fact, the borders simply disappear, the windows and their content are still there. Moreover, the bottom taskbar freezes. I tried different borders 'themes', but they still crash. The xcleardiff tool is the only Clearcase tool that causes such trouble.

Right now, I have not found any other way than log out/log in to restore the windows borders

I would like to know what GNOME process manages the windows and if there is a way to get some error logs. Of course, if anyone is experiencing the same problem, I'll be glad to know it.

Any help, tip or suggestion would be greatly appreciated.

Regards,

Kiem

---

### Post by dcstar on 2006-02-16
[QUOTE=topolino]Hello,

I have just upgraded my laptop from Ubuntu 5.04 to Ubuntu 5.10. It went fine. However, I am facing a problem at work that I did not have with Ubuntu 5.04.
......
I would like to know what GNOME process manages the windows and if there is a way to get some error logs. Of course, if anyone is experiencing the same problem, I'll be glad to know it.

Any help, tip or suggestion would be greatly appreciated.

Regards,

Kiem[/QUOTE]
AFAIK 5.10 used a far different Gnome version than 5.04, and there have been a few issues with certain things - yours could be another.

Probably best to got back to 5.04, and wait for Dapper to be released in a few months to see if that works ok.

---

### Post by udha on 2006-02-16
you could try from any command line on that machine: killall gnome-panel

and see if things are restored.

---

### Post by RAOF on 2006-02-16
Metacity is what manages the window borders.  If you want some debug info, you could run "metacity --replace" from a console.  And once it's crashed, start it up again the same way :)

---

### Post by topolino on 2006-02-16
Thanks for your answers. And special thanks to RAOF.

I indeed have a crash of metacity. Here is the output:

Bug in window manager: Unexpected X error: BadAlloc (insufficient resources for operation) serial 8197 error_code 11 request_code 53 minor_code 0)
Aborted

I was told that xcleardiff (the application that causes metacity crash) was pretty greedy on resources. So is there a way to allocate more resources (memory?) to metacity ?

Regards,

Kiem

---

