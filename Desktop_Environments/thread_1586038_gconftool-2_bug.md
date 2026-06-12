---
title: "gconftool-2 bug?"
date: 2010-10-01
forum: Desktop Environments
---

### Post by aregjan on 2010-10-01
I am reporting on what seems to be a gconftool-2 bug.

I have a perl script which accesses the National Geographic web site, acquires the photo of the day, and tells gconftool-2 to set it as a desktop bgnd.  I put the script in my crontab -- and it fails to do what it's supposed to do.

Here are the conditions and symptoms:

a) if I run the script from command line it works perfectly fine.

b) /var/log/syslog claims that the script is called when it's supposed to be called.  So crontab does its job well.

c) In the script, for debugging purposes the system call which refers to gconftool-2 is implemented in the following way:

```
 
if(system("gconftool-2 --type string --set /desktop/gnome/background/picture_filename $tempfile")==0){
	system("echo $tempfile>>/home/aregjan/date.txt");
    }
    else {
	system("echo \" FAILURE \">>/home/aregjan/date.txt");
    }

```
I check /home/aregjan/date.txt -- it's being incremented with the correct filename at correct times, rather than a FAILURE notification.  In other words the system call returns 0, a success. 

d) Just to make it complete, this is my crontab entry:
 ```

0 * * * * /home/aregjan/bin/background.pl >/dev/null 2>& /dev/null

```

Despite all this, I do not see the background change -- EXCEPT when I login.  

Any ideas?  Is this a real bug?

---

### Post by aregjan on 2010-10-01
Hah!  Just came across the SAME problem as reported 2 years ago on this very forum!
Great to find out that I am not insane.  Sad to find out that 2 years on the problem hasn't been fixed.

[http://ubuntuforums.org/showthread.php?t=952452](http://ubuntuforums.org/showthread.php?t=952452)

---

