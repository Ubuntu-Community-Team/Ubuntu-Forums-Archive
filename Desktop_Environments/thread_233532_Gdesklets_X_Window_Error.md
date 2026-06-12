---
title: "Gdesklets X Window Error"
date: 2006-08-10
forum: Desktop Environments
---

### Post by UrbanSlayer on 2006-08-10
When trying to start Gdesklets on Ubuntu Dapper (Gdesklets installed from Ubuntu Repo), I recieve the following error - 

lain@Eclair:~$ gdesklets start
Starting gdesklets-daemon...
Connecting to daemon [ ### ]The program 'gdesklets-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
(Details: serial 85 error_code 2 request_code 78 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.


All the error log in /home/lain/.gdesklets/logs/gdesklets%3A0.0.log

Is - Log messages of /home/lain/.gdesklets/logs/gdesklets%3A0.0.log

Ive googled the error, but have only come up with some things from 2002 that dont seem to relate to gdesklets. Im a bit stumped.

Can anyone help? Thanks!

---

### Post by maniacmusician on 2006-08-10
i guess you could try reinstalling it. maybe there is a newer version out and you could install that from source or a package (check their website)

---

### Post by UrbanSlayer on 2006-08-10
Hi,

I have uninstalled, reinstalled and have compilied/installed from source (incidently, the latest version on the gDesklets site is also the version in the Ubuntu repo's), and I get the same error I listed above.

Any ideas?

Cheers

---

### Post by taurus on 2006-08-10
How did you install it because I have no problem running it at all on my Dapper with Gnome?

```
sudo apt-get install gdesklets gdesklets-data
```
Also, try to run it without the "start" option at the end...

```
gdesklets
```

---

### Post by UrbanSlayer on 2006-08-10
Hi,

That is the way I installed it from the repos, and running it without or without the start argument produces the same result.

Im wondering if gDesklets doesnt play well with Xinerama or xcompmgr/Composite extenstion.  It worked ok with Xinerama though..

---

### Post by UrbanSlayer on 2006-08-10
Yup, disabling Composite in the xorg.conf fixed it.  Darn.

---

