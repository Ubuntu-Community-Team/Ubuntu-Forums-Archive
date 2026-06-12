---
title: "Leave message for other users. How?"
date: 2009-02-24
forum: General Help
---

### Post by roccivic on 2009-02-24
Hi,

How would I go about leaving all users on a certain system a message that would be displayed only once when they login into their account?

For example: ```
Please be advised that all invoices have been moved from 
/backup/invoices 
to
/toshare/documents/invoices

Yours truly,
System administrator
```

Many thanks

---

### Post by DerHesse on 2009-02-24
How about e-mailing?

---

### Post by heindsight on 2009-02-24
You could add your message to /etc/motd.tail. That way it will be displayed each time a user logs in via a terminal or ssh. If you also want it displayed each time a user logs into an X session, you can create a file /etc/xprofile containing:

```
#!/bin/sh

xmessage -file /etc/motd -center
```

Then once you're sure all your users have seen the message, you can remove it from /etc/motd.tail (and comment out the xmessage line from /etc/xprofile - or just delete the file).

---

### Post by roccivic on 2009-02-24
Obviously a viable option, but will depend on the user accessing the email inbox. Some might not check and will just ](*,)

Would there be a way of scheduling a task to be executed upon login only once. The task could be as simple as invoking zenity with some parameters I guess...


Thanks

---

### Post by roccivic on 2009-02-24
> **heindsight said:**
> You could add your message to /etc/motd.tail. That way it will be displayed each time a user logs in via a terminal or ssh. If you also want it displayed each time a user logs into an X session, you can create a file /etc/xprofile containing:

```
#!/bin/sh

xmessage -file /etc/motd -center
```

Then once you're sure all your users have seen the message, you can remove it from /etc/motd.tail (and comment out the xmessage line from /etc/xprofile - or just delete the file).

Thanks that will probably do it ;)
One more question, how could this be done to display a message to one user only?

Peace

---

### Post by heindsight on 2009-02-24
> **roccivic said:**
> Thanks that will probably do it ;)
One more question, how could this be done to display a message to one user only?

Peace

I'm not 100% sure of this, but I believe you could put something like

```
#!/bin/sh

if [ $(uid -u) -eq 1000 ]; then
  xmessage -file /etc/motd -center
fi

```
into /etc/xprofile (replace 1000 with the UID of the user you want to display the message for). You could also just create a .xprofile file in that user's home directory.

---

### Post by roccivic on 2009-02-24
Nice one, thanks ;)

---

### Post by sisco311 on 2009-02-24
or

save this script as /usr/bin/notify
```
#!/bin/bash

zenity --info --text "bla bla bla ... \nbla bla bla ..."
rm $HOME/.config/autostart/notify.desktop
```
make it executable:
```
chmod +x /usr/bin/notify
```
and add this desktop entry to $HOME/.config/autostart/notify.desktop
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=notify
```

---

### Post by roccivic on 2009-02-24
That's even better! Awesome, thanks!

---

