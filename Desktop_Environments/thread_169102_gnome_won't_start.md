---
title: "gnome won't start"
date: 2006-05-01
forum: Desktop Environments
---

### Post by DSn0wMan on 2006-05-01
I am unable to log into my desktop.

When I login I receive an error message that says try loging in with a failsafe session.

When I check View details (~/.xsession-errors file)

I see a weird message,

/etc/gdm/Xsession: Befinning session setup. . .
/etc/gdm/Xsession: line 73: ls: command not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed!

Any Ideas?

---

### Post by Sef on 2006-05-02
At the log in window, log in to the terminal.  From there,

sudo apt-get update

sudo apt-get upgrade

See if that fixes the corruption.

---

### Post by DSn0wMan on 2006-05-02
Thats a good idea. I will try when I get home, and can connect my laptop to a network.

---

### Post by DSn0wMan on 2006-05-02
[QUOTE=DSn0wMan]Thats a good idea. I will try when I get home, and can connect my laptop to a network.[/QUOTE]

No dice.......

This install looks like a lost cause, I think it's time to re-brick.

---

### Post by JanDM on 2006-05-02
[QUOTE=DSn0wMan]No dice.......

This install looks like a lost cause, I think it's time to re-brick.[/QUOTE]
What is your PATH variable? (echo $PATH)

---

### Post by DSn0wMan on 2006-05-02
[QUOTE=JanDM]What is your PATH variable? (echo $PATH)[/QUOTE]

$PATH was fine. 

I just rebricked to save some headache. Hopefully It doesn't come up again.

---

