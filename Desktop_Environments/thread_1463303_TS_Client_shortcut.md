---
title: "TS Client shortcut"
date: 2010-04-26
forum: Desktop Environments
---

### Post by trubendall on 2010-04-26
Is there a way to associate the .rdp file extension with Terminal Server Client?  I have a lot of servers that I connect to and it would be great to just double click on the file to launch the session.

If not, is there another way I could create a shortcut that would launch a specific TS session?

I have searched all over and not found a solution, I may just be searching with the wrong terms, but any help would be great.

Thanks,

---

### Post by trubendall on 2010-04-27
Bump, Anyone?

---

### Post by pricetech on 2010-04-27
I've never tried double clicking so I don't know how it might behave on my computer.

What I do is have the launcher for Terminal Server Client in my Panel and use the Open button on the main screen to pick which session I want.

My situation is similar to yours in that I support a herd of windows boxen which includes some servers.  I use RDP for most, but a couple of them have VNC installed because of peculiarities in the software the run.

Works for me.

---

### Post by pricetech on 2010-04-27
Another thing you might try:  Right click on one of the .rdp files.  Choose Properties and go to the Open With tab.  Mine currently defaults to being opened with a text editor and yours probably will too.

Click the Add button and see if Terminal Server Client is listed as an option.  If not you can click Use a custom command and type in
```
/usr/bin/tsclient
```
That's where mine is located anyway.  I haven't tried this, but I would think it should work.  Easy enough to undo if it doesn't.

---

### Post by bjcubsfan on 2011-12-17
I solved this problem by making a new shortcut that executes a command like this:

```
tsclient -x /home/user_name/.tsclient/computer_to_connect.rdp
```

change the variables for your needs.

---

