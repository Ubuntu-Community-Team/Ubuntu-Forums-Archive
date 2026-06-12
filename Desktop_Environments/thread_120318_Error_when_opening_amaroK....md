---
title: "Error when opening amaroK..."
date: 2006-01-21
forum: Desktop Environments
---

### Post by Cless on 2006-01-21
Every time I'm trying to open Amarok I get the following errormessage:

["Could not launch the mail client: KDEInit could not launch 'kmail'.: Could not find 'kmail' executable."]("http://img22.imageshack.us/img22/2776/screenshot0hd.png")

Do you know what's wrong?

---

### Post by Elvish Legion on 2006-01-21
[QUOTE=Cless]Every time I'm trying to open Amarok I get the following errormessage:

["Could not launch the mail client: KDEInit could not launch 'kmail'.: Could not find 'kmail' executable."]("http://img22.imageshack.us/img22/2776/screenshot0hd.png")

Do you know what's wrong?[/QUOTE]


Well I know this isn't helpful but it seems your missing kmail....is it installed?

---

### Post by Luggy on 2006-01-23
[QUOTE=Elvish Legion]Well I know this isn't helpful but it seems your missing kmail....is it installed?[/QUOTE]

I'm getting the same error. I didn't have Kmail installed before and Amarok ran fine. Why is it even trying to open Kmail?

---

### Post by dueY on 2006-01-23
I used to get this error, too.  I think I had only armarok installed.  You should try ```
sudo apt-get install amarok amarok-arts amarok-engines amarok-gstreamer amarok-xine
```

---

### Post by Luggy on 2006-01-24
[QUOTE=dueY]I used to get this error, too.  I think I had only armarok installed.  You should try ```
sudo apt-get install amarok amarok-arts amarok-engines amarok-gstreamer amarok-xine
```[/QUOTE]

I figured out what's going on.

I went and installed kmail to see why it wanted to open it. The reason it wanted kmail was since amarok is a KDE application it wants to open a KDE mail client to  return an error message.

---

### Post by mthaddon on 2006-02-03
What was the error message and did you ever resolve it? I still can't get amarok working, and I really like the app.

Here's my error message from the terminal on starting amarok:

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QPainter::begin: Cannot paint null pixmap
mthaddon@ubuntu:~$ kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for job!
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4800015
QWidget::setMaximumSize: (unnamed/RecipientComboBox) The largest allowed size is (32767,32767)
kmail: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'smtp'.
kmail:


Looks like the last bit is just related to submitting a bug report.

Thanks, Tom

---

### Post by ivuntu on 2006-02-09
Hi,

I have the exact same error, but I noticed that Amarok DOES start up,only not directly visible: 

I recently changed my taskbar, I added " Notification Area" , and voila: the Amarok Icon was there, and just clicking on it brought Amarok back to life.

I am not happy with the error message, but as long as it works, I can live with it!

---

### Post by mthaddon on 2006-02-19
Mine wasn't showing up even in the task bar.

Turns out I had some stale config files from an older version of Amarok. Deleted ~/.kde/share/apps/amarok and everything was fine.

---

### Post by khronic on 2006-03-13
Hey Gang,

I'm receiving this error now as well!  I used amarok on a daily basis until today.  When I started it up, I received the same error messages described above.

I tried purging my config files - no luck.  
And, it doesn't hide itself after the errors - it completely quits.

The only thing I've done since the last time I amarok was install todays security updates...But I can't recall what packages those effected.

Anyone have any more thoughts on this?

TIA,
-k

---

### Post by ElmZ on 2006-03-14
hi guys....its my first time to use amarok and it is a cool player....but how come some of my songs will shut down amarok.....? it doesnt play at all....my musics are all in ntfs hard drive...(slave hdd)....

tnx

---

### Post by ElmZ on 2006-03-18
bump....

---

### Post by orawax on 2006-03-31
[QUOTE=mthaddon]Deleted ~/.kde/share/apps/amarok and everything was fine.[/QUOTE]

This worked for me.

---

