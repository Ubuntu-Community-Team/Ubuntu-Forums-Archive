---
title: "Using FTP ... setting default editor"
date: 2009-02-01
forum: General Help
---

### Post by bastones on 2009-02-01
I'm using gFTP and I want to set the editor it opens files to and well, transitioning from Windows its difficult to find the path to the Scite Text Editor unlike simply going to 'Program Files' in Windows...any help appreciated :).

---

### Post by mcduck on 2009-02-01
Actually it's easier.. Pretty much all executable files for user programs are in the same place, /usr/bin. :)

If you can't fins something there just run "which *nameOfTheProgram*" and you'll get the path to that program's executable file.

---

### Post by bastones on 2009-02-01
> **mcduck said:**
> Actually it's easier.. Pretty much all executable files for user programs are in the same place, /usr/bin. :)

If you can't fins something there just run "which *nameOfTheProgram*" and you'll get the path to that program's executable file.

Thanks. So in the Options of gFTP do I add usr/bin/scite or something else?

Cheers

---

### Post by mcduck on 2009-02-01
> **bastones said:**
> Thanks. So in the Options of gFTP do I add usr/bin/scite or something else?

Cheers

If there is such a file, then that most likely is the executable for Scite. So that command should work fine.

---

