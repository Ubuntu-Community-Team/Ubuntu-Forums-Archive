---
title: "Konqueror crash problem"
date: 2005-04-13
forum: Desktop Environments
---

### Post by -TayloR- on 2005-04-13
i have read that this problem has been identified, i was just wondering on if there is any news on this? like if its being looked into anytime soon and such? i tried the 'way around it' by not showing that side menu thing but that doesnt seem to have helped me, mine still constantly crashes on me. Just wondering if there is going to be a patch / update for this anytime soon?

---

### Post by !nkubus on 2005-04-13
Well have, a watch on the bug in bugzilla but no news since yesterday :(

---

### Post by Manny C on 2005-04-13
As noted in another thread, this has been classified a priority 2 bug (ie...second highest priority) on the kubuntu bugzilla: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8009](https://bugzilla.ubuntu.com/show_bug.cgi?id=8009)

Further here is a temporary hack from bugzilla:

> If you remove the line:   
OpenViews=home.desktop   
   
from the file /etc/kde3/konqsidebartng.rc the sidebar is disabled on konqueror 
start and this problem doesn't happens. This can be a little hack to fix it 
temporarly.  
  
I'll try to collect more data and find where's the problem or report it  
upstream. 

This fix has been confirmed on my system.

---

### Post by dermotti on 2005-04-13
sidebar does help.....

---

### Post by Manny C on 2005-04-14
You can always use the address bar...it does have an autocomplete function.

Or be more basic...use a shell (Konsole)

---

### Post by !nkubus on 2005-04-14
[QUOTE=Manny C]You can always use the address bar...it does have an autocomplete function.

Or be more basic...use a shell (Konsole)[/QUOTE]

Back to old days ;)

seriously i hope hat bug will be fixed soon

---

### Post by -TayloR- on 2005-04-14
Well yeah i now use either the terminal or rox-filer to browse my files now, and for the net i use firefox, these are just as good for me but i to also hope its fixed sometime soon :). Thanks for the replies.

---

