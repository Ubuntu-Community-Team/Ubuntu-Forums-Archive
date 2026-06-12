---
title: "A quick question on getts and virtual terminals"
date: 2006-04-06
forum: Desktop Environments
---

### Post by harisund on 2006-04-06
Ok, I understand that by default Ubuntu ships with 6  Virtual Terminals (accessible through Alt-F1 through Alt-F6) and a default X session gets started on Terminal 7. 

My question is, when I click on New login, I seem to be taken somewhere and shown a new GDM login screen. Assuming a second person has logged in how do I get back to my own x session? (which I am hoping is still existant, that is I am not logged out) 

Next, I turned off 4 of the 6 virtual terminals by commenting out the lines in /etc/inittab. So now I end up with only 2 consoles at Alt-F1 and Alt-F2. 

Now, when I start a X session, where does it end up? At 3? or at 7 again? Now if I do a "new login" where is that window? 

Also, what do I do (in place of startx) in order to open a X session at a particular terminal instead of the default? 

Just curious to know .. thanks  !

---

### Post by ranf on 2006-04-06
When you switch to another user there is a new X server started on vt8 (on one of my computers it was vt9).
So Ctrl+Alt+F8 or F9.

You can see that with `ps ax'.

---

