---
title: "Ghosts at startup?"
date: 2012-01-01
forum: Desktop Environments
---

### Post by tiger63 on 2012-01-01
Using Xubuntu 11.10

I have a ghost of a problem.  I have experimented with various conky setups and finally settled on a couple that I start at boot.  The problem is that now I have 2 *extra* conkys starting on boot.  Ordinarily, I'd just uncheck them in the xfce settings session and startup module...except that they aren't listed there.  So I go into my /tiger/.config/autostart folder and there are no desktop files for these "ghosts" there either.

Here's where it gets really weird.  When I look for the entries in the task manager, it lists them *both* as "conky -c /home/tiger/.conky/conkyleft."  Why is that weird?  Because I deleted the .conky directory and any files in it days ago.  I've been scratching my head trying to figure out where these "ghosts" are coming from...does anyone have any idea how to stop them from autostarting?

---

### Post by Toz on 2012-01-01
Probably in the sessions cache (~/.cache/sessions). You can try to prune the references out or simply delete that directory to reset the cache.

---

### Post by tiger63 on 2012-01-01
> **Toz said:**
> Probably in the sessions cache (~/.cache/sessions). You can try to prune the references out or simply delete that directory to reset the cache.

Thank you!  You've taught me something new and solved my problem!  Much appreciated :D

---

### Post by tiger63 on 2012-01-08
Well, I thought this was solved, but it isn't.  The problem is that this situation is recurrent.  How do I stop this from happening?  Every 3 or 4 boots I have to erase the /.cache/sessions directory to stop this.  This is just annoying.  Any way to stop this from happening?

BTW, this is on a laptop, so this is why I have multiple boots during a day.

---

### Post by Toz on 2012-01-08
When you logout, make sure that the "Save sessions for future logins" checkbox is unchecked.

---

### Post by tiger63 on 2012-01-08
> **Toz said:**
> When you logout, make sure that the "Save sessions for future logins" checkbox is unchecked.

Thanks, Toz.  Didn't notice that it was checked and don't remember checking it, but that's about par for the course for me lately.

---

