---
title: "Emerald acting up?"
date: 2009-02-23
forum: Desktop Environments
---

### Post by suzrocksanne on 2009-02-23
I have the emerald theme manager and I am able to use the different themes on emerald, but everytime I shut down, restart, or hibernate, the theme goes back to default.  I always have to go to the terminal everytime and do

"emerald --replace"

Is there a way that I can keep it the theme I choose?

---

### Post by mcduck on 2009-02-23
Does it go back to default Emerald theme or back to using Gnome-Window-decorator instead of Emerald?

Running "emerald --replace" is not even supposed to permanently replace your previous window manager/decorator. To make the setting permanent you need to set emerald as your default decorator in Compiz settings.

In CompizConfig Settings Manager go to Window Decorator-plugin, and in there change the "Command" to "/usr/bin/emerald".

---

### Post by andrewa1 on 2009-02-23
HI and you can add emerald to the start up under system, preference, sessions. Then click add then use the emerald --replace as the command.  just use Emerald as the name...and as comment just use emerald start.

mcduck your just confusing things

---

### Post by mcduck on 2009-02-23
Well, if you just add "emerald --replace" to your session you're gong to get slower desktop startup because you are first starting Compiz, which loads whatever decorator it's configured to use (GWD by default), and then replacing that with Emerald. Instead you could simply load the correct decorator in the first place.

Of course both ways give the same result in the end, but why start one thing and then immediately replace it with something else?

---

### Post by andrewa1 on 2009-02-23
I see, yes your way is far easier.  Just im a noob and found the way i did it easy so thought other noobs would. i have now changed it under windows management, cheers.

---

### Post by suzrocksanne on 2009-02-23
Ok so I went with Mduck's solution right now and so far so good... let's see if it stays that way.  
Thanks guys!

---

