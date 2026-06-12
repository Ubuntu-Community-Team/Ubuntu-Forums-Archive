---
title: "Cron not executing commands"
date: 2009-01-17
forum: General Help
---

### Post by denham2010 on 2009-01-17
Hi,

I'm having a problem with cron.

I am setting it up to schedule a regular backup of my system. The only problem is, come the scheduled execution time, the command does not execute.

I know cron is working as I can add a simple test script (it appends text to a file on my desktop everytime it is executed) and it works.

I have even checked the system logs, and it indicated the command has been run, but I know 100% that it hasn't!

Does anyone have any idea what might be going wrong?

output of crontab -l
```
50 * * * * /home/denham2010/test.sh
50 * * * * /opt/flyback/src/flyback.py --backup
```
(I do have an empty line at the end of my crontab as I know cron needs this)

output in syslog
```
Jan 18 11:50:01 ****** /USR/SBIN/CRON[23810]: (******) CMD (/opt/flyback/src/flyback.py --backup)
Jan 18 11:50:01 ****** /USR/SBIN/CRON[23819]: (******) CMD (/home/******/test.sh)
```

In the log above, I can confirm the script test.sh is executing, as lines are added to the text file on my desktop.

The flyback command is not executing. Infact, the only command it seems to execute (either in a script or not) is 'echo'. Every other command I have tried (and I have tried many) just do not execute.

Help! Please!

Thanks.

---

### Post by ac7ss on 2009-01-17
Try piping the output of the flyback to a spare terminal or file. Have you checked your sterror screen (I think it is 8 but not sure.)

---

### Post by denham2010 on 2009-01-17
Hi ac7ss,

I know the flyback command works.

Running the command directly in a terminal does a backup as expected.

Funny thing though, If I create a script to execute the backup, and include an 'echo' command at the start of the script, cron will run the script, execute the 'echo' command but ignore the rest of the script.

It's not only the flyback command that does not work. Any command that is not an 'echo' will not work, yet running the scripts or commands directly in a terminal all work as expected.

Cheers.

---

### Post by ac7ss on 2009-01-17
try using an absolute path to the command within the script. I was mentioning piping the output from the cron event to an error file.

---

### Post by denham2010 on 2009-01-20
Hi,

Sorry for my late reply.

Ok.....it seems it may have something to do with X.

I tried an example of opening opera web browser:

```
10 * * * * /usr/bin/opera
```

This did not work. Piping stderr to a file told me opera could not connect to the display.

So changing the crontab line to:

```
10 * * * * /usr/bin/opera -display :0.0
```

will now launch opera....ok, this sample worked.

Now my problem is with other scripts which don-t have the luxury of being able to pass an argument to connect to the display.

This is the error I get trying to run a python script:

```
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
```

Again, cannot connect to the display on X.....

Anyone have an idea on what is happening here?

Thanks.

---

