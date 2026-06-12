---
title: "Deleted items do not go to deleted items folder."
date: 2009-05-19
forum: General Help
---

### Post by user 123 on 2009-05-19
I just did a fresh install of Jaunty and I have noticed that every time I delete an item it does not appear in the Deleted Items folder.
Anybody else experienced this or solved the problem?

Thanks

---

### Post by spacesamurai on 2009-05-19
The issue here is the difference between "removing a file" and "moving a file to trash". With Windows, files deleted by the user go to the trash (Windows does not trust the user, I suppose). As for your problem, you will want to move your files to ~/.Trash. How this is done is up to you. You can just move them with the move command, make an alias where rm moves them (A bad idea in my opinion) and so forth. The freedom is yours.

Also, the [trash] command (which moves files to the trash can) has been made available which can be downloaded as so:

```
sudo apt-get install trash-cli
```

Hope this helps.

---

