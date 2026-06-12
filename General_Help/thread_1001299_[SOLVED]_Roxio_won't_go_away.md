---
title: "[SOLVED] Roxio won't go away"
date: 2008-12-03
forum: General Help
---

### Post by rsnow on 2008-12-03
I've made a mess. I came across Wine in the package manager and I installed it (against my better judgement). So, I thought I would try it out and I tried to install Roxio video editor into it. I guess I didn't do it right because I kept getting a runtime error message. So then I used package manager to uninstall Wine. Now I can't figure out how to get rid of the Roxio files that are still on my computer. I've tried using rmdir but I'm apparently not doing it right because all I get are failed to remove answers.

Can someone let me know what info I need to provide so that I might get some help in getting the Roxio files removed? This is on  Hardy.

---

### Post by Slim Odds on 2008-12-03
```
rm -rf {roxioDir}
```

replace {roxioDir} with the appropriate name

---

### Post by rsnow on 2008-12-03
Here is what I typed and what I got

rm -rf (Roxio)
bash: syntax error near unexpected token `('

---

### Post by rsnow on 2008-12-03
oops, now I see after looking closer. Let me try again.:redface:

---

