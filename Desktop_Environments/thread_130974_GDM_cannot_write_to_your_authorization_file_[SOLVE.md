---
title: "GDM cannot write to your authorization file [SOLVED]"
date: 2006-02-15
forum: Desktop Environments
---

### Post by malacandra on 2006-02-15
There are several posts which ask this question, so I'll post my own problem and solution and hope a search will help someone!

I meant to delete all of the files in my /tmp directory but actually ended up deleting the whole directory.

When I rebooted, I got the message "GDM cannot write to your authorization file...etc"

I knew by using the **df** command that my partitions were not full. 

Some other posts mentioned something about permissions.

That got me thinking: perhaps my user login was trying to write to /tmp but that directory had been recreated as root!  Sure enough!

Solution: Using a terminal as root, type:
**chmod 0777 /tmp**

Note that this will only work if you have an active root account. If not, you may have to log in at a failsafe terminal (rescue mode from Grub) and do it from that command line.

Hope this helps someone!

---

### Post by jssi.net on 2006-02-23
I just installed ubuntu on my iBook G3 and get
"GDM cannot write to your authorization file...etc" when I try to login
via Gnome or terminal (console). I thought clicking on Terminal login would bypass this and allow me to get to a shell prompt.
How do get around this and login into a terminal mode and find out what the problem is?
Thanks,
Eddy

---

### Post by nkindlon on 2008-04-03
Just wanted to offer Malacandra my immense gratitude. I dug around various posts all day, but your suggestion to log in as root and do the chmod 777 /tmp is what finally solved my GDM witing to the auth file problem. Thanks!

---

### Post by agibby5 on 2008-05-22
WOW for some reason I had this issue today when booting up.  I checked my disk space, and had only 19% usage.  Then I found this thread and allowed universal write access to the /tmp folder... worked! Thanks!

---

