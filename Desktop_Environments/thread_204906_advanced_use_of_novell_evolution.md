---
title: "advanced use of novell evolution"
date: 2006-06-27
forum: Desktop Environments
---

### Post by suoko on 2006-06-27
Hi,

I've got some questions regarding evolution:

- Is there a chance to open a new email message windows from terminal?
Plus, can I open it with TO: and CC: fields already filled in? (something like #evolution --new-message -to [email]john@aol.com[/email] -cc [email]sam@gmail.com[/email])

Or may I open a new message together with a vcard with multiple email addresses where the first email will be put in the TO: field and the others in the CC: or the BCC: fields (something like #evolution --new-message -CC addresses.vcf)?

thanks

Gabriele

---

### Post by suoko on 2006-06-30
Hey there,

nobody knows how to do that????

I discovered openoffice capable of creating a new evolution message with an attachment ....
Is it done through mono? how?

---

### Post by Wolki on 2006-06-30
Hm, in the future this should be possible via dbus.

You can simply use gnome-open with a mailto link, though, if evolution is your default email client:

```
gnome-open "mailto:john@aol.com?cc=sam@gmail.com"
```

I don't know about the vcard thing though :-/

---

### Post by leech on 2006-06-30
Uhm, Evolution already has the Send to in Dapper.  Just install 'nautilus-sendto' then you can right click on any file in Nautilus and send it either through Nautilus or through Gaim.

Not so sure about everything else.  I can do some research on it when I get home from work, if I remember to.

Leech

---

### Post by suoko on 2006-07-01
I don't know how to thank you for the gnome-open thing. 
That's perfect since it's not bind to evolution client.

Where is this gnome-open documented ??
How did you know about it?


thanks again

Gabriele

---

### Post by Wolki on 2006-07-01
You're welcome. Unfortunately it seems to be undocumented, can't tell you anymore where I read about it. It's quite a useful command though, since you can use it to open pretty much any file in the default application.

---

