---
title: "Trouble with gnome panel"
date: 2011-05-16
forum: Desktop Environments
---

### Post by grekhss on 2011-05-16
Hello!
I have found a strange bug in 11.04 Classic No Effects with GNOME. It is following: set some custom theme, e.g. Ambiance. Open several applications and make one application with a long title (e.g. set some custom title for the shell). Set mouse pointer on the task on gnome panel (see Screenshot-001) and wait for the caption to appear. The caption will cover some part of the Gnome panel. When the caption appears move mouse pointer to the near task and wait for the other caption appear: as a result the area which was covered by the first caption will not be drawn correctly - instead of normal panel it shows the desktop background (see Screenshot-002).
If someone knows how to solve this - please, help.
Kind regards,
Sergey Grekhov.

---

### Post by grekhss on 2011-08-05
Up!
The problem still annoys me. Please, help! =)

---

### Post by grekhss on 2011-09-30
Hope that someone will help me to fix this issue. Up-up-up!

---

### Post by pkg9991 on 2011-09-30
is it still the issue.. try upgrading ?

---

### Post by grekhss on 2011-10-03
Could you, please, tell in more details what do you mean?
I have Ubuntu 11.04 already. Or you propose to upgrade Gnome?

---

### Post by grekhss on 2011-10-14
Enough for me. Switched to KDE.

---

### Post by pavi_elex on 2011-11-08
Really Annoying...

---

### Post by grekhss on 2011-11-21
Finally, I have found the troublemaker. Or, at least, this is the trace of troublemaker.

Currently, I am working under XFCE4. I decided to try different window managers. It appeared that described bug (see first message in thread) appears in XFCE4 if I use metacity window manager.

Also I found that some troubles with correct drawing of panel take place in XFCE4 with XFWM4 and proprietary ATI drivers. Metacity with and without proprietary ATI drivers produce this error.
On the other hand:
1) I have Ubuntu 10.10 at home
2) I have there onboard ATI card
3) metacity does not show any troubles there
Looks like metacity tries to use some specific API of ATI graphics which is absent in my card.
Any ideas how to check this? And, possibly, fix?

UPDATE:
I have found a workaround. I simply replaced metacity with xfwm4 when running "Gnome Classic (No effects)". And that annoying bug has gone, as I expected. I do not really care about having window manager other than metacity. So, the problem is solved for me. Hope that nobody will have such annoying trouble or will find this post and solve it quickly.
Thanks to everybody for attention and help! =)

---

