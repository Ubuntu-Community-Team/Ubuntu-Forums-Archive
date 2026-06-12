---
title: "Installation problem/ Installationsproblem"
date: 2005-09-02
forum: Desktop Environments
---

### Post by JuCu on 2005-09-02
Hello,

Yesterday I wanted to install the Kubuntu OS 5.4 on my computer.But when the installation was on 19% there was an Error message which says:

(I translated this from German in English):

[COLOR=Red]There was an Error/Problem by installing the the Primary system.
debootstrap was stopped with a law (Returned value 1)

For more pieces of Information examine /var/log/messages look at the virtuell console 3.
[/COLOR]

The original Message (in German):

[COLOR=Red]Bei der Installation des Grundsystems ist ein Fehler aufgetreten.
debootstrap wurde mit einem Fehler beendet (Zurückgegebener Wert 1).

Für mehr Informationen, prüfen sie /var/log/messages oder sehen sie auf der virtuellen Konsole 3 nach.[/COLOR]


If look at the messages, but there was nothing. It would be nice, if anyone could help me.

Thanks and Greetings from Germany,
JuCu

---

### Post by incinerator on 2005-09-02
This is very odd. Have you verified the iso with md5sum?

You could also try run the LiveCD to check it's not a quirk with your hardware.

---

### Post by JuCu on 2005-09-03
I've fixed this problem and I saw others in this forum with the same problem.
Kubuntu doesn't accept FAT32 or FAT16 partitions. So I installed it succesful on a ext2 partition.

Greetings from Germany,
JuCu

---

