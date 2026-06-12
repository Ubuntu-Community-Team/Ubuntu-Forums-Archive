---
title: "Seahorse and Gnugpg problem"
date: 2006-08-09
forum: Desktop Environments
---

### Post by FreDeas on 2006-08-09
I install Seahorse as a frontend to gpg. I followed the instructions on the help file and configured it proprerly. 

When I encrypt a file using right click>encrypt I can't decrypt either from the terminal or doubleclicking in it. If I doubleclick a seahorse window says it can;t open the file. If I try to decrypt it through the terminal it says it can't open it as well.

When I encrypt the file manually (through terminal with the command gpg -o XXXXX -c XXXXX) I can't decrypt it if I doubleclick, seahorse asks for passphrase but it crashes the same time. I can decrypt it with a command from the terminal but this also posts an error :
can't connect to `/home/dharma/.gnome2/seahorse-DVEr2Y/S.gpg-agent': Connection refused
gpg: can't connect to `/home/dharma/.gnome2/seahorse-DVEr2Y/S.gpg-agent': connect failed

---

### Post by sadam on 2006-08-18
Try

killall seahorse-agent

then remove the last 2 lines of ~/.gnupg/gpg.conf that indicate which socket to use then run seahorse-agent again.

---

