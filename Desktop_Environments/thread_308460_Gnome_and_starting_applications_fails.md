---
title: "Gnome and starting applications fails"
date: 2006-11-28
forum: Desktop Environments
---

### Post by akvik on 2006-11-28
Hi,

I run latest ubuntu Edgy (Nov 28th).

When I startup gnome for the first time after a restart, I can't start any applications. They wait for a while: "Starting terminal.." and then they disappear. The only way to bypass this is to CTRL-ALT-Backspace and then log in again. _then_ everything works as usual.

Does anyone have a similar problem, or a solution to this? Have tried to look in the gdm logs, but have found nothing.

:)

---

### Post by bapoumba on 2006-11-28
Hi,
what theme are you using ? Is it the same with all the default human theme (windows, icons, controls ...) ?

---

### Post by akvik on 2006-11-28
Hi,

Well, I've had the problem for a while, and I've changed the theme once or twice, but I will check more carefully this relation. Using default human at the moment. Have you had a similar problem that you solved by changing the theme. To me it seems as if gnome starts to behave strangely once I start changing and playing with the themes.

---

### Post by bapoumba on 2006-11-28
Well, not with edgy so far. But with dapper, I had once all messed up, ended up checking with a fresh made user, where everything was fine. I nailed down a theme file in my regular user profile. It's worth a try with a newly made user. If you have no problem, there is something to look at in your regular user files (theme, .gnome*, .gconf). If not, it is a more general problem.

---

