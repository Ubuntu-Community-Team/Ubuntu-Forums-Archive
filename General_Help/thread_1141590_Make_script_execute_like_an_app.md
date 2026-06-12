---
title: "Make script execute like an app"
date: 2009-04-28
forum: General Help
---

### Post by HyperX on 2009-04-28
I wrote a backup script, and the only way for me to execute it is to run sh backup.sh in terminal. I just want to double click on it so it executes. Can I save a script as an application?

In windows, you save things as .bat and you can double click. In Mac, I can save a script as an application and double click. I just want to do the same in Ubuntu.

Thanks!

---

### Post by 3Miro on 2009-04-28
You can create a link to application on either the menu or an icon on the desktop. You will have to point it to the script:
```

/full/path/to/script/theScript.whatever_you_called_it

```

Use Nautilus (i.e. the file manager) to set the permissions for the script file to be executable.

---

### Post by HyperX on 2009-04-28
Thanks! That did it!! woo hoo!

---

### Post by N_Nick on 2009-04-28
Just right click the script Properties > Permissions > Allow executing as a program and thats it

---

