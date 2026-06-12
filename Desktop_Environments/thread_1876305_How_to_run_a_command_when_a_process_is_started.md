---
title: "How to run a command when a process is started"
date: 2011-11-06
forum: Desktop Environments
---

### Post by pcarlos853 on 2011-11-06
Hi,

I need to run a command to kill firefox when a program called wfcmgr starts running. How would I achieve this? 

(Ubuntu 10.04)

Thanks!
Carlos

---

### Post by deskman on 2011-11-06
[FONT=Consolas][SIZE=2]Use this command "pgrep firefox" or "pidof firefox" (without quotes) to view its process ID. Now use "kill PID" where PID is the number you received in previus command. If still it doesn't work ucan ran "kill -9 PID". [/SIZE][/FONT]
 
Regards

---

### Post by Lars Noodén on 2011-11-06
On the theme of pgrep, you can use [pkill](http://manpages.ubuntu.com/manpages/oneiric/en/man1/pkill.1.html)

```

pkill -x firefox

```

The -x is there to make it an exact match and not get programs that might include the string "firefox" in the name.

---

### Post by lswb on 2011-11-06
> **pcarlos853 said:**
> Hi,

I need to run a command to kill firefox when a program called wfcmgr starts running. How would I achieve this? 

Possibly there is some command that will watch for a process to start by name, but I don't know of such a command. You can roll your own, though, by watching the /proc directory. Every time a new process starts, a subdirectory is created in /proc with the name being the process number. There are various attributes of the process listed as files in that directory.

First, install the inotify-tools package. This gives you 2 command-line programs, inotifywatch and inotifywait. The 2nd is handy for shell scripts. Read the man pages after installation. Your script would be something like this: 

```

while inotifywait -e OPEN /proc   # Watch /proc for new process starting
do
 if pgrep wfcmgr;      # Is the process named "wfcmgr" ?
 then pkill firefox;   # If yes, then kill firefox
 fi
done

```
Note that this is not a tested script, just a basic idea to get you started.

---

### Post by pcarlos853 on 2011-11-07
I decided to run this at start up:

```
#!/bin/bash
# check daemon
ps -ef | grep -v grep | grep wfica
# if not found - equals to 1, start it
if [ $? -eq 1 ]
then
echo "ICA client is not running..Exiting"
sleep 15
sh /home/thinclient/Downloads/script.sh
else
killall "Virtual Desktop"
killall firefox
sleep 15
sh /home/thinclient/Downloads/script.sh
fi
```Thanks
Carlos

---

