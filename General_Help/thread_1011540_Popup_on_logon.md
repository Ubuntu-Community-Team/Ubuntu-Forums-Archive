---
title: "Popup on logon"
date: 2008-12-14
forum: General Help
---

### Post by lenswipe on 2008-12-14
Hi there

im looking for something to remind me of something when i logon. On M$ i could just make a vbscript and shove it in the startup folder with something like 

MsgBox "Message" 

for the message i wanted for the reminder.

How do i achieve this on ubuntu.

Cheers

-L

---

### Post by lenswipe on 2008-12-15
bump

---

### Post by drs305 on 2008-12-15
I'm not exactly sure I know what you are looking for, but if it is a simple popup message that will always be the same and not require changing, you could use *zenity*. You would put the command in the Sessions, Startup Programs. You could also make a simple script to include a 'sleep' feature so it comes up after everything else is started.

Here is a typical zenity command:
```
zenity --question --text "Did you remember to ...?"; echo $?
*or*
sleep 10 && zenity --question --text "Did you remember to ...?"; echo $?

```
You don't really need the 'echo' portion unless you are running a script.

Here is a good page to view various zenity options/message formats:
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/")

---

### Post by lenswipe on 2008-12-15
> **drs305 said:**
> I'm not exactly sure I know what you are looking for, but if it is a simple popup message that will always be the same and not require changing, you could use *zenity*. You would put the command in the Sessions, Startup Programs. You could also make a simple script to include a 'sleep' feature so it comes up after everything else is started.

Here is a typical zenity command:
```
zenity --question --text "Did you remember to ...?"; echo $?
*or*
sleep 10 && zenity --question --text "Did you remember to ...?"; echo $?

```
You don't really need the 'echo' portion unless you are running a script.

Here is a good page to view various zenity options/message formats:
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/")

Thanks :)

---

