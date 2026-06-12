---
title: "Dot &quot;run&quot; extension doesn't work.."
date: 2005-11-01
forum: Desktop Environments
---

### Post by janko on 2005-11-01
I don't understand why when i run from shell some "installer-version.run" file it doesn't work, can anyone help me? (usually ".run" files are installers and so on ...)
When i run it without sudo it says: Permission denied
Using the same command with sudo : command not found

Thank you all,

Janko

---

### Post by riggsd on 2005-11-01
There is nothing magic about a ".run" or any other extension in *nix. For something to be executable, it must be set executable. Google for "[unix permissions]("http://www.google.com/search?q=unix+permissions")" to learn about this.

```

chmod +x ./whatever.run
sudo ./whatever.run

```

---

