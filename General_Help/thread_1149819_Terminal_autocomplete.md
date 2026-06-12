---
title: "Terminal autocomplete"
date: 2009-05-05
forum: General Help
---

### Post by Ramzy on 2009-05-05
Used to Windows and such, being able to do something like,

cd C:\Users\Ramzy\Desktop
start extremely_amazingly_painfully_long_file_name_here1293821983.exe

After filling in the first few letters (extre), then tapping <tab>, command prompt automatically selects the best matching file name to autocomplete.

Is there anything like this with the terminal? I'm finding myself just renaming files at the moment, just to skip the hassle.

---

### Post by wolfestine on 2009-05-05
Of course there is... Why didn't you just press tab to check it out? :) Oh! n remember... everything is case sensitive.

---

### Post by lswb on 2009-05-05
Usually tab completion of filenames works by default with bash (bash is the command interpreter that normally runs in a terminal) In fact, bash and other unix shells have had some form of command or filename completion much longer than windows has with it's cmd.exe shell.

If tab completion doesn't work for you, open up your ~/.bashrc file with the editor of your choice and search for some lines something like this:
```

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

If they are commented out (prefixed with a # character) remove the #, if they are missing entirely you can add them.

---

