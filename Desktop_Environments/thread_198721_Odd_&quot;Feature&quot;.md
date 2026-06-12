---
title: "Odd &quot;Feature&quot;"
date: 2006-06-17
forum: Desktop Environments
---

### Post by kinghajj on 2006-06-17
In the terminal, when I try to autocomplete files, it doesn't always work. I've determined that it's trying to make me unable to autocomplete "incorrect" files; for example, if I begin typing "dpkg -i m", it won't autocomplete to "dpkg -i myfile.rpm". (I know dpkg can't install from RPMs, but when you try it tells you which tool to use to convert the rpm to a deb.)

Which file can I edit to disable or modify this feature?

---

### Post by astoltz on 2006-06-17
The shell is smart but I don't think it's quite that smart.  It should auto-complete the dpkg -i m[tab] regardless of the command.  Maybe there is more than one file starting with m?  In that case, two presses on tab will bring up a list of possibilities.  Or just continue with the file name a bit: "dpkg -i my[tab]"

---

