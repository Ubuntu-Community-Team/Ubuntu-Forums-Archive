---
title: "gkrellm 100% CPU utilisation ..."
date: 2007-11-15
forum: Desktop Environments
---

### Post by rhdinah on 2007-11-15
When Gutsy gnome login and gkrellm starts there is this little dance between gkrellm, gnome-panel and metacity for 100% of the CPU for between 1 and 10 minutes ... then this stops ...

Running top shows this dance and the players ...

If I drop gkrellm ... everything calms down ... bring gkrellm up again and this continues until it wants to stop ...

There seems to be no sense to this ... sometimes this does not happen at all ... other times it is as long as ten minutes. Originally I thought this was some kind of sanity check on boot up ... top showed it to be the before mentioned tasks. Anyone have a clue to what's happening?

Thanks!

:popcorn:

---

### Post by linuxwizard on 2007-11-16
Are you using any Gkrellm plugins ? If so try disabling them one at a time see if that helps.

---

### Post by rhdinah on 2008-01-14
Not using any plugins except what comes with the vanilla gkrellm ... but I'll take a look at that application ... thanks!

---

