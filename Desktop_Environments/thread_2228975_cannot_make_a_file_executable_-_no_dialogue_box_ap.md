---
title: "cannot make a file executable - no dialogue box appears"
date: 2014-06-10
forum: Desktop Environments
---

### Post by Bengt_Hedlund on 2014-06-10
Tried to make a package executable. I go to properties and check the appropriate box. But when i double-click the file no dialogue box appears where i am asked to run the file. Instead geedit opens the file. I even run the command "sudo chmod +x file-name" in the terminal, but the problem remains.

---

### Post by monkeybrain20122 on 2014-06-10
This is because of the stupid default behaviour of the file manager. To change this open Nautilus (the file manager), go to Preferences > Behaviour > Executable Text Files and choose 'Ask each time".

---

### Post by Bengt_Hedlund on 2014-06-10
> **monkeybrain20122 said:**
> This is because of the stupid default behaviour of the file manager. To change this open Nautilus (the file manager), go to Preferences > Behaviour > Executable Text Files and choose 'Ask each time".

Yes that helped. Thanks!

---

