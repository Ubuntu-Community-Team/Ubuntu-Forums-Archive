---
title: "DBGL Not Working After Upgrade"
date: 2019-09-13
forum: Emulators
---

### Post by Shadius on 2019-09-13
Hi all,

I recently upgraded to 18.04.3 LTS after reviving my Ubuntu computer. It seems to have broken my DBGL. I select "Run in Terminal", but the prompt flashes and disappears and nothing else happens. Any suggestions?

---

### Post by Shadius on 2019-09-15
Can anyone help, please?

---

### Post by Holger_Gehrke on 2019-09-27
First we need to find out what is actually wrong. Open a terminal, change to the directory where you put dbgl (on my machine that would be 'cd ~/bin/dbgl', probably different on yours) and run it with './dbgl'. That way the terminal won't close as soon as the program has finished running (which is what happened when you selected run in terminal)

dbgl is written in Java and seems to be highly dependent on the version of the JRE you've got installed. Older version of dbgl won't run on anything newer than Java 8, the current one won't run on old version of the JRE. You can have multiple versions of the JRE installed and switch between them using 'sudo update-java-alternatives -s <Name-of-java-version>'.

Holger

---

