---
title: "Issue w/ LightDM logout script"
date: 2013-08-13
forum: Desktop Environments
---

### Post by Kanefa on 2013-08-13
I've read on this forum you can add the var "session-cleanup-script" to SeatDefaults of lightdm.conf to specify a script to be called on logout.  However, my script is not being called.

Here is my lightdm.conf.  After making changes I have rebooted.

```

[SeatDefaults] 
greeter-session=lightdm-gtk-greeter 
user-session=Lubuntu 
allow-guest=false 
session-cleanup-script=/opt/gScripts/student_logoff_script.sh

```

I have made "student_logoff_script.sh" exectable by calling 

```
chmod a+x student_logoff_script.sh
```

I've tried logging out and rebooting and my script is never called.  Any suggestions?  Thanks.

---

### Post by Toz on 2013-08-13
> I've tried logging out and rebooting and my script is never called. Any suggestions? Thanks. 
How are you sure that the script is never called (as opposed to the script being called but the commands not being executed successfully)? The session-cleanup-script is run as root, so depending on what the script is doing, you may not get anticipated results. How about posting the contents of the script?

---

### Post by Kanefa on 2013-08-13
Here is the script.  This is for a public lab I am volunteering at.  I simply want the student user to have a clean account after each logoff.  The Books, Music, and Videos directory all include large number of multimedia lessons, so I've made them read-only and then change the read access and move them to make the process faster.

```

#!/bash/bin

# create temp dir
mkdir /home/temp_student

# move large read-write files
mv /home/student/.Calibre /home/temp_student/.Calibre

# change attributes of large read-only files to read-write
chattr -i -R  /home/student/Books
chattr -i -R /home/student/Music
chattr -i -R /home/student/Videos

# move large read-only files
mv /home/student/Books /home/temp_student/Books
mv /home/student/Music /home/temp_student/Music
mv /home/student/Videos /home/temp_student/Videos

# delete  student home folder
rm -rf /home/student

# copy default_student to student
cp -rf /home/default_student /home/student

# move large read-write files
mv /home/temp_student/.Calibre /home/student/.Calibre

# move large read-only files
mv /home/temp_student/Books /home/student/Books
mv /home/temp_student/Music /home/student/Music
mv /home/temp_student/Videos /home/student/Videos

# change user and group of student dir
chown -R student:student  /home/student

# change attributes of large read-write files to read-only
chattr +i -R  /home/student/Books
chattr +i -R /home/student/Music
chattr +i -R /home/student/Videos

# delete  student home folder
rm -rf /home/temp_student

```

---

### Post by Toz on 2013-08-13
> #!/bash/bin
...should be:
```
#!/bin/bash
```

In case that doesn't fix it, you can also try adding (just after #!/bin/bash):
```
exec > /tmp/session-cleanup-script.log 2>&1
```
...and then after logout, view the /tmp/session-cleanup-script.log file for any error messages that any of the script commands may have thrown.

---

