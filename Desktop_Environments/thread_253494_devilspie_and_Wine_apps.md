---
title: "devilspie and Wine apps"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Cable on 2006-09-08
I'm trying to get devilspie to move utorrent to workspace 3 when it opens.  I cannot seem to figure out what application name or window role to use.  Nothing I try is working.  Ideas?

---

### Post by Wolki on 2006-09-08
try using devilspie with a debug rule (i.e., (debug) in a .ds file in your .devilspie directory), then start it from the command line ("devilspie"). You should get a list of all open windows and their names, application names and window roles.

Note that I haven't used devilspie with wine yet and since I don't have any windows apps right now I can't test myself whether devilspie works with wine at all.

---

### Post by Cable on 2006-09-09
Well, I was trying to use things that I saw in the terminal by using the xprop command.  Wouldn't that basically yield the same information as what you suggested?

---

### Post by Wolki on 2006-09-09
Well, I did some testing a long time ago, and found that it was mostly the same, but with some programs there were differences. Some things were translated, some were descriptions, and so on. Maybe it's something like that with wine too?

---

