---
title: "batch untar"
date: 2005-12-29
forum: Desktop Environments
---

### Post by tagg3rx on 2005-12-29
hello,
i have a directory of about 100 tarballs and i want to un tar them all into a specific directory, i would prefer not to have to do it one at a time.

does anyone know a command line way to untar all the files in a given directory.


thanks

---

### Post by psusi on 2005-12-29
cd specific_dir ; tar xf /path/to/tars/*.tar

---

### Post by tagg3rx on 2005-12-29
something didnt go right

:~/.gkrellm2/themes$ tar xf ~/.gkrellm2/GKrellM-skins/*.tar.gz
tar: /home/helpdesk/.gkrellm2/GKrellM-skins/4D_Ladies.tar.gz: Not found in archive
tar: /home/helpdesk/.gkrellm2/GKrellM-skins/Absolute_E.tar.gz: Not found in archive
tar: /home/helpdesk/.gkrellm2/GKrellM-skins/AbToenAlloy-green.tar.gz: Not found in archive
tar: /home/helpdesk/.gkrellm2/GKrellM-skins/aCOW.tar.gz: Not found in archive
tar: /home/helpdesk/.gkrellm2/GKrellM-skins/Acqua.gkrellm.tar.gz: Not found in archive
tar: /home/helpdesk/.gkrellm2/GKrellM-skins/Acqua-Graphite.gkrellm.tar.gz: Not found in archive
etc......
tar: Error exit delayed from previous errors

---

### Post by psusi on 2005-12-29
Oh, darnit... tar only accepts one file at a time... try this:

for file in /path/to/*.tar ; do tar xf $file ; done

---

### Post by Jason-X on 2005-12-29
This is the command I used to untar my Gkrellm themes:

> for i in *.tar.gz; do echo working on $i; tar xvzf $i ; done

Hope this helps.

---

### Post by tagg3rx on 2005-12-29
nice that for statment worked

Very cool i didnt realize you can just post c code in the bash

thanks

---

### Post by psusi on 2005-12-29
It isn't C code, it's just bash shell scripting.  There's all kinds of good stuff you can do with bash... you can start with "info bash" and do quite a bit of reading about it.

---

