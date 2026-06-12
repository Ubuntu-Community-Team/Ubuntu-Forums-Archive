---
title: "Problem Creating Launcher"
date: 2009-05-05
forum: General Help
---

### Post by verbal.kint on 2009-05-05
I'm trying to create a launcher for an application, JSMS, but the app wont start.

I have the same problem when I try to start it from "run application" but when I go to the terminal it launches fine.

here is the permissions of the contents of the folder:


```
vinnie@vinnie-laptop:~$ cd /home/vinnie/JSMS
vinnie@vinnie-laptop:~/JSMS$ ls -al
total 5332
drwxr-xr-x  3 vinnie vinnie    4096 2009-04-25 11:10 .
drwxr-xr-x 42 vinnie vinnie    4096 2009-05-05 22:21 ..
-rw-r--r--  1 vinnie vinnie    2348 2008-05-27 22:46 AboutJSMS.txt
-rw-r--r--  1 vinnie vinnie  303792 2008-07-14 22:38 beankeeper-2.4.1.jar
-rw-r--r--  1 vinnie vinnie  171861 2008-06-23 01:25 colorchooser.jar
drwxr-xr-x  2 vinnie vinnie    4096 2009-04-25 00:31 dictionaries
-rw-r--r--  1 vinnie vinnie   62555 2008-05-13 22:12 gdata-client-1.0.jar
-rw-r--r--  1 vinnie vinnie    5455 2008-05-13 22:12 gdata-contacts-1.0.jar
-rw-r--r--  1 vinnie vinnie  264166 2008-05-13 22:12 gdata-core-1.0.jar
-rw-r--r--  1 vinnie vinnie  706710 2008-07-14 22:38 hsqldb.jar
-rw-r--r--  1 vinnie vinnie   60849 2008-05-13 22:12 jacob.jar
-rw-r--r--  1 vinnie vinnie    8933 2008-07-14 22:38 java-cup-11-runtime.jar
-rw-r--r--  1 vinnie vinnie     324 2007-12-22 01:07 JMySpell.license.txt
-rw-r--r--  1 vinnie vinnie  753875 2009-01-19 21:35 JSMS-core.jar
-rw-r--r--  1 vinnie vinnie   37176 2009-01-19 21:35 JSMS.jar
-rwxr-xr-x  1 vinnie vinnie     454 2007-11-05 20:35 JSMS.sh
-rw-r--r--  1 vinnie vinnie   17989 2007-11-01 02:00 LICENSE.txt
-rw-r--r--  1 vinnie vinnie  351731 2008-07-14 22:38 log4j-1.2.15.jar
-rw-r--r--  1 vinnie vinnie    2315 2008-11-03 22:50 logging.properties.unused
-rw-r--r--  1 vinnie vinnie    2971 2007-12-22 01:07 MySpell.license.txt
-rw-r--r--  1 vinnie vinnie    1492 2007-11-01 09:10 quotes.png
-rw-r--r--  1 vinnie vinnie   12720 2009-01-12 14:34 README.txt
-rw-r--r--  1 vinnie vinnie  118103 2008-06-09 23:29 swing-layout-1.0.3.jar
-rw-r--r--  1 vinnie vinnie   12591 2008-07-03 01:02 swing-worker-1.1.jar
-rwx------  1 vinnie vinnie 2210155 2009-04-25 00:31 uninstall
-rw-r--r--  1 vinnie vinnie     162 2009-04-25 00:31 Uninstall JSMS.desktop
-rw-r--r--  1 vinnie vinnie  234398 2008-05-13 22:12 wizard.jar
```

---

### Post by maheshasolkar on 2009-05-05
How do you run it in terminal? What did you put in the the 'command' section of launcher?

If you go into the directory (/home/vinnie/JSMS) and then run JSMS.sh in the terminal, you should try to put the absolute path in the 'command' section of the launcher (/home/vinnie/JSMS/JSMS.sh).

---

### Post by verbal.kint on 2009-05-06
ya thats exactly what i do, I run it in the terminal like so:

*/home/vinnie/JSMS/JSMS.sh*

I do it the exact same way in the launcher but it doesn't start, I've even copied the text from the terminal to make sure I was typing everything the same.


I've created launchers before with no problem, I even had a launcher for JSMS in gutsy....I'm using Jaunty at the moment

---

### Post by verbal.kint on 2009-05-14
Actually if I try and run it using the full path from say the root folder in the terminal it wont run, it'll only run when I navigate to /home/vinnie/JSMS and then run it.

Its really weird, and it makes me seem like a complete technological retard

---

