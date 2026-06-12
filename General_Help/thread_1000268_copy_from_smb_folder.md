---
title: "copy from smb:// folder"
date: 2008-12-02
forum: General Help
---

### Post by Proto_ on 2008-12-02
Hello all

Sorry for the complete beginner talk but i need some help.

I need to schedule a job to do the following every 8 hours:

delete everything from ~/Desktop/media
copy everything from smb://192.168.0.190 to ~/Desktop/media

i dont have the slightest idea on how to schedule jobs on ubuntu or how to copy the files from the samba (cp did not work)

can anyone help me, please?

Thanks

---

### Post by jspolen on 2008-12-02
Not entirely sure on copying from a samba shared folder, but I would start by looking at cron. Cron is a daemon which executes scheduled tasks in ubuntu. 

Also you might want to copy from the mounted directory instead of "ip/directory"

---

### Post by Proto_ on 2008-12-02
ok... and how do i mount the folder? i am sorry, complete begginner here
(looking for cron)

---

### Post by jspolen on 2008-12-02
Do you know how to shell script? If you don't it's not that difficult to write at miniprogram to copy a bunch of files.

So when you have written your script, you need to edit the /etc/crontab file. In here you specify when you want your script to run and where it's located.
You don't actually need to write a script you can put the commands directly into the crontab file.

crontab:
--------------------------------------------
minute hour dayofmonth month dayofweek user command
15      10     *        *       *       me     cp /home/* /home/1/
----------------------------------------------


Makes a copy of all the files in home to directory 1 every day at 10:15


When you access your samba shared folder it puts itself somewhere on the filesystem, usually in the /mnt or /media directory. Look it up

---

### Post by lovinglinux on 2008-12-02
You can also use a GUI to setup the cron jobs 

[http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)

---

### Post by jspolen on 2008-12-02
Yeah that looks alot easier

---

