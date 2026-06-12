---
title: "Crontab tutorial"
date: 2005-12-12
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-12
**What Is Crontab?**

A crontab is a simple text file that holds a list of commands that are to be run at specified times. These commands, and their related run times, are controlled by the cron daemon and are executed in the system's background. More information can be found by viewing the crontab's man page. We will run through a simple crontab example later.


**How Does It Work?**

The system maintains a crontab for each user on the system. In order to edit or create a crontab, you must use the text editor that is specified by your system. The nano text editor is the default text editor on my system. This text editor must be opened with the command crontab using the -e option. To create a crontab open a term and type:

```
crontab -e
```

The nano text editor will open with a blank window for the desired times and commands to be entered. Each line represents a seperate crontab entry - also known as a "cron job". If you are not familiar with the nano text editor you should obtain a tutorial for it as that information is beyond the scope of this post.


**Crontab Sections**

Each of the sections is separated by a space, with the final section having one or more spaces in it. No spaces are allowed within Sections 1-5, only between them. Sections 1-5 are used to indicate when and how often you want the task to be executed. This is how a cron job is layed out:

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

```
01 04 1 1 1 /usr/bin/somedirectory/somecommand
```

The above example will run /usr/bin/somedirectory/somecommand at 4:01am on any Monday which falls on January 1st. An asterisk (*) can be used so that every instance (every hour, every weekday, every month, etc.) of a time period is used. Code:

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

The above example will run /usr/bin/somedirectory/somecommand at 4:01am on every day of every month.

Comma-seperated values can be used to run more than one instance of a particular command within a time period. Dash-seperated values can be used to run a command continuously. Code:

```
01,31 04,05 1-15 1,6 * /usr/bin/somedirectory/somecommand
```

The above example will run /usr/bin/somedirectory/somecommand at 01 and 31 past the hours of 4:00am and 5:00am on the 1st through the 15th of every January and June.

The "/usr/bin/somedirectory/somecommand" text in the above examples indicates the task which will be run at the specified times. It is recommended that you use the full path to the desired commands as shown in the above examples. The crontab will begin running as soon as it is properly edited and saved.


**Crontab Options**

The -l option causes the current crontab to be displayed on standard output.
The -r option causes the current crontab to be removed.
The -e option is used to edit the current crontab using the editor specified by the VISUAL or EDITOR environment variables.

After you exit from the editor, the modified crontab will be checked for accuracy and, if there are no errors, installed automatically.


**Crontab Example**

Below is an example of how to setup a crontab to run updatedb, which updates the slocate database: Open a term and type "crontab -e" (without the double quotes) and press enter, type the following line, substituting the full path for the one shown below, into the editor:

```
45 04 * * * /usr/bin/updatedb
```

Save your changes and exit the editor.

Crontab will let you know if you made any mistakes. The crontab will be installed and begin running if there are no errors. That's it. You now have a cron job setup to run updatedb, which updates the slocate database, every morning at 4:45.

Note: The double-ampersand (&&) can also be used in the "command" section to run multiple commands consecutively. 

```
45 04 * * * /usr/sbin/chkrootkit && /usr/bin/updatedb
```

The above example will run chkrootkit and updatedb at 4:45am daily - providing you have all listed apps installed.

I hope this little tutorial is of help to the community.

---

### Post by tonderai on 2005-12-12
Great tutorial! Very demystifying. Thanks.

My one question about cron is - what happens if the system is turned off when the command is scheduled to run? Is it run when the computer is next switched on?

---

### Post by Rinzwind on 2005-12-12
[QUOTE=tonderai]Great tutorial! Very demystifying. Thanks.

My one question about cron is - what happens if the system is turned off when the command is scheduled to run? Is it run when the computer is next switched on?[/QUOTE]

No.

That's what **acron** is for. That one executes cron jobs that where scheduled but where not possible due to your system being down.

---

### Post by tonderai on 2005-12-12
Is acron installed and operational as default, or do I need to do anything to set it up?

---

### Post by ardchoille on 2005-12-12
[QUOTE=tonderai]Is acron installed and operational as default, or do I need to do anything to set it up?[/QUOTE]
After a fresh install of Ubuntu 5.10, I noticed that anacron was installed and running, so I think this is the same thing.

---

### Post by missmoondog on 2006-06-03
cool tutorial.

question:
what exactly does this command do then?
sudo/etc/cron.daily/slocate

thank you

---

### Post by mikeym on 2006-08-01
It may be worth mentioning for those that like to use their own editor - like me - that you can change the defalt editor for cron (and bash) by editing their ~/.bashrc

```

[COLOR="Gray"]# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups[/COLOR]

# use vim for editing
export EDITOR=vim


```

It is also worth mentioning that cron executes commands with minimal set of environmental variables set up. You can get your default profile by executing the following:

```

00 00 * * * . $HOME/.bashrc && $HOME/myscript

```

The '.' executes the .bashrc script in the current process level. '&&' is used for chaining commands together.

It is also a good idea to redirect the output from cron to a log because otherwise it will try to mail the output to root - this will fail by default on an Ubuntu system as mail is not set up. You can redirect as follows:

```

00 00 * * * . $HOME/.bashrc && $HOME/myscript > $HOME/log/cron-myscript.out.log 2> $HOME/log/cron-myscript.err.log

```

If you are wanting to use commands to notify the user - such as zenity - then you may want to set the display first with:

```

00 00 * * * export DISPLAY=:0 && zenity --info --text "Wake me up before you go, go!" > $HOME/log/cron-myscript.out.log 2> $HOME/log/cron-myscript.err.log

```

Display=:0 is the default display for gnome on a single XWindows session machine.

---

### Post by mikeym on 2006-08-01
If you are using multiple users logged on to XWindows on the same machine and you want to send them a message then the following may work:

```

53 20 * * * export DISPLAY=$(who | awk ' BEGIN { FS=" " } /'`whoami`'/ { print $2 }' | head -n1) && zenity --info --text "Testing, testing 1, 2 ,3."

```

The whole '`whoami`' bit gets the name of the user who's cron session you are  editing. You could set this by hand to the users name.

I don't use multiple users running X on the same machine so I can't test this. If anyone does I would love to know if it works. (I am assuming that the first entry for each user on 'who' gives the display for thier X Session - I don't know if this is always the case.)

---

### Post by antilog on 2006-08-10
How do I check to see if a cron job ran?  Are there cron logs?

---

### Post by ardchoille on 2006-08-11
> **mikeym said:**
> If you are using multiple users logged on to XWindows on the same machine and you want to send them a message then the following may work:

```

53 20 * * * export DISPLAY=$(who | awk ' BEGIN { FS=" " } /'`whoami`'/ { print $2 }' | head -n1) && zenity --info --text "Testing, testing 1, 2 ,3."

```

The whole '`whoami`' bit gets the name of the user who's cron session you are  editing. You could set this by hand to the users name.

I don't use multiple users running X on the same machine so I can't test this. If anyone does I would love to know if it works. (I am assuming that the first entry for each user on 'who' gives the display for thier X Session - I don't know if this is always the case.)

Thank you for your posts, good stuff :)
I'll have to add these things to my personal wiki.

---

### Post by natuk on 2006-08-17
And how does the system-wide cron work? Isn't it user independent? Tasks are scheduled in there but in my setup they don't seem to run.

---

### Post by ardchoille on 2006-08-17
> **natuk said:**
> And how does the system-wide cron work? Isn't it user independent? Tasks are scheduled in there but in my setup they don't seem to run.

The system keeps a seperate crontab for each user and runs them all simultaneously at the time(s) specified in the crontabs. If you can list your crontab, maybe myself or someone else can help you get it working.

---

### Post by natuk on 2006-08-17
Thanks for this.

These are the contents of my system-wide crontab file. This is meant to execute every minute, but although there are tasks saved in etc/cron.hourly, they do not actually happen.

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
00 *	* * *	root    run-parts --report /etc/cron.hourly
30 2	* * *	root	run-parts --report /etc/cron.daily
30 3	* * 0	root	run-parts --report /etc/cron.weekly
30 6	1 * *	root	run-parts --report /etc/cron.monthly
#

---

### Post by meth on 2006-08-21
This is my crontab -e

# m h  dom mon dow   command
0 18 * * * shutdown -h now

And never works, what have i made bad??
cron is working

---

### Post by UbuNewbie123 on 2007-10-03
I entered the command i want into my crontab. Then I his control + X to exit. It asked me this:

File Name to Write: /tmp/crontab.gjvazq/crontab

This seems like temporary file. Where should I save it instead?

I enter crontab -l and it does list my cron commands. However, after I enter crontab -e again and exit without saving, then I do a crontab -l again. I see nothing. The file name has changed. I am confused. Am I supposed to be writing to these /tmp/ places in the first place?

---

### Post by UbuNewbie123 on 2007-10-03
I think I got it. I decided to save the crontab file in my home directory.

Then I entered:

crontab -u myusername crontab

After that I restarted cron by entering:

sudo /etc/init.d/cron restart

Any idea to see if my crons are running and working all right?

---

### Post by UbuNewbie123 on 2007-10-03
1 last question...

If I create a cron to run every 6 hours: 0 */6 * * *

When does the cron start? Does it start at 0000h?

---

### Post by zahir76 on 2008-02-11
Thank you, although small yet helpful for newbie like me. Although crontab is for bit experience user but 'term'='terminal' (above in the post) may be confused to some ;)
The more clear and simple the better.

---

