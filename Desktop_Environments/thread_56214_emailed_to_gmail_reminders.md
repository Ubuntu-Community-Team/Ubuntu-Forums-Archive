---
title: "emailed to gmail reminders"
date: 2005-08-11
forum: Desktop Environments
---

### Post by earobinson on 2005-08-11
I want to set my computer up to email reminders to my gmail accout, or forward my mail (local mail) to my gmail account, any ideas how i would do this?

thanks

---

### Post by kassetra on 2005-08-11
[QUOTE=earobinson]I want to set my computer up to email reminders to my gmail accout, or forward my mail (local mail) to my gmail account, any ideas how i would do this?

thanks[/QUOTE]

Your local mail = mail you receive on your home box and say, you want to be able to see anywhere?

If that's the case - you can use evolution to do both things - you can setup evolution to email your reminders to you, and you can use evolution to forward your mail...

Or are you meaning something else - like you have mail that's only in your home or office lan and not connected to the internet?

---

### Post by earobinson on 2005-08-12
[QUOTE=kassetra]Your local mail = mail you receive on your home box and say, you want to be able to see anywhere?

If that's the case - you can use evolution to do both things - you can setup evolution to email your reminders to you, and you can use evolution to forward your mail...

Or are you meaning something else - like you have mail that's only in your home or office lan and not connected to the internet?[/QUOTE]

That would work but would that not make it so that i had to have evolution  runing all the time on my computer?

---

### Post by earobinson on 2005-08-12
i was hoping to have a cron job do it

---

### Post by earobinson on 2005-08-14
Anyone know how to set up evolution for gmail

---

### Post by krismatth3 on 2005-08-15
In your home directory, create the file ".forward" with your email address in it.

e.g. 

~/.forward:
[email]username@gmail.com[/email]

All mail will be forwarded to gmail.

---

### Post by krismatth3 on 2005-08-15
[QUOTE=earobinson]Anyone know how to set up evolution for gmail[/QUOTE]

It's pretty simple - enable POP on your gmail account. In evolution, add a new account. Your servers will be:

incoming: pop.gmail.com, port 995 (use ssl)
outgoing: smtp.gmail.com, port 587 (use tls)

You username is your gmail username, and your password is your normal gmail password.

---

### Post by earobinson on 2005-08-16
[QUOTE=krism]It's pretty simple - enable POP on your gmail account. In evolution, add a new account. Your servers will be:

incoming: pop.gmail.com, port 995 (use ssl)
outgoing: smtp.gmail.com, port 587 (use tls)

You username is your gmail username, and your password is your normal gmail password.[/QUOTE]
 my problem is i cant find where to add the port and ssl tls info

---

