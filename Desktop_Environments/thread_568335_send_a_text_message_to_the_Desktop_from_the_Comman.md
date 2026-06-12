---
title: "send a text message to the Desktop from the Command Line"
date: 2007-10-05
forum: Desktop Environments
---

### Post by boondocks on 2007-10-05
I have a cron script that takes care of various chores.
Sometimes  the cron script does not know how to handle a certain situation.

At that point, I would like the cron script to send me a Pop Up message on my Ubuntu desktop.
How can I do this?
Is there some command line utility that can send a line of text to the desktop?

---

### Post by goatflyer on 2007-10-06
I'm no expert, but here are two little python scripts I wrote for you to play around with.  You can play with them a bit to see how they work, and then invoke them from your main cron script.

You will need to install the python package from the repositories if you don't already have it.


Save this one as **askyesno.py**
```

#! /usr/bin/python
import tkMessageBox

yes = tkMessageBox.askyesno("My Urgent Question","Destroy the world?")
if yes:
  print "Now destroying world... please stand elsewhere."
else:
  print "The earthlings live for another day..."


```

Save this one as **showinfo.py**
```

#! /usr/bin/python
import tkMessageBox

result = tkMessageBox.showinfo("An Urgent Annoucement","I'm stuck")
if result:
  print "A user finally pressed ok.  Perhaps they even read the message."
else:
  print "OMG What did you click to get result = false ?!?"


```

Then make them executable
```

chmod +x askyesno.py
chmod +x showinfo.py

```

And finally run them
```

./askyesno
./showinfo

```

... you probably already knew to do the last two, but  I included them for others who may read this post.

Each one will pause your main script and make it wait until the user clicks something.  If you want to just send a popup and keep going without waiting, try invoking them from bash with trailing '&'

Hope they are useful.

---

### Post by Wolki on 2007-10-06
Depends on whether you want a dialog or a notifiaction bubble.

For dialogs, I'd recommend zenity:
```
zenity --info --text="Something really important has happened."
```
For notification bubbles, use notify-send:
```
notify-send "Something really important has happened."
```

---

### Post by goatflyer on 2007-10-06
Hey, I like that zenity command, but notify-send doesn't work for me (not found).  What package is it in?

---

### Post by mlissner on 2007-10-06
It's in libnotify-bin. If you had run it in Feisty, it would tell you:
```
% notify-send "test"
The program 'notify-send' is currently not installed.  You can install it by typing:
sudo apt-get install libnotify-bin
bash: notify-send: command not found

% sudo aptitude install libnotify-bin

```

---

### Post by softdel on 2007-10-27
I seem to be having trouble with both of these commands. 

Allow me to demonstrate:

```

root@ubuntu-server:~# zenity --text="Something really important has happened."
This option is not available. Please see --help for all possible usages.
```

as for notify-send

```
root@ubuntu-server:~# notify-send "Something really important has happened."
libnotify-Message: Unable to get session bus: Failed to execute dbus-launch to autolaunch D-Bus session

```

Any help would be much appreciated, ta.

---

### Post by astoltz on 2007-10-27
Could the problem be that the zenity and notify-send  commands are being run as "root" and the messages are intended for your "user" desktop?

Unfortunately I don't know how to fix that issue.  Anyone know how to let one user (root) send another user a pop-up message?

---

### Post by softdel on 2007-10-27
Oops, yeah...root... But as an admin i should be able to selectively send to users?

---

### Post by softdel on 2007-10-27
My last comment was invalid. It still doesn't work.

Same errors.

---

### Post by wadageek on 2007-11-06
By any chance, have you ssh'd into your pc?  if so you will have to add the --display=DISPLAY (where DISPLAY, is the DISPLAY value of which the user you are trying to send the message is on.  Easiest way to find out is to issue the "who" command)

eg.  $zenity --info --text="This is a test message" --display=:0

Hope this helps.

---

### Post by softdel on 2007-11-07
> **wadageek said:**
> By any chance, have you ssh'd into your pc?  if so you will have to add the --display=DISPLAY (where DISPLAY, is the DISPLAY value of which the user you are trying to send the message is on.  Easiest way to find out is to issue the "who" command)

eg.  $zenity --info --text="This is a test message" --display=:0

Hope this helps.

And this is what happened ( I included a who command too)

```
root@ubuntu-server:~# zenity --info --text="This is a test message" --display=:0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

This option is not available. Please see --help for all possible usages.
root@ubuntu-server:~# who
administrator :0           2007-11-06 19:27
root     pts/0        2007-11-07 18:45 (ubuntu)
root@ubuntu-server:~#

```

---

