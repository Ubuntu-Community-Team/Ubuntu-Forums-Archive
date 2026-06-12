---
title: "hostname in command prompt"
date: 2011-10-11
forum: Desktop Environments
---

### Post by mfearer on 2011-10-11
Hello, all. Running 11.04. Is there a way that, in an ssh or telnet session, that hostname will not appear in the command prompt? Not logged in yet, so not seeking a user shell environment. I just want to see something like 'login>', not 'ubuntu login>'.

---

### Post by SeijiSensei on 2011-10-11
> **mfearer said:**
> Hello, all. Running 11.04. Is there a way that, in an ssh or telnet session, that hostname will not appear in the command prompt? Not logged in yet, so not seeking a user shell environment. I just want to see something like 'login>', not 'ubuntu login>'.

Your prompt is set in ~/.bashrc.  See the section on PROMPTING in "man bash".

The system-wide default prompt is set in /etc/bash.bashrc.

---

### Post by mfearer on 2011-10-12
Thank you. That is helpful, but that was not exactly my question. I am not seeking a user's shell environment. I am speaking of the login prompt. I am seeking a method of not having the hostname displayed in the login prompt. For example, I am currently seeing "ubuntu login>". I just wish to see "login>".

---

### Post by haqking on 2011-10-12
> **mfearer said:**
> Thank you. That is helpful, but that was not exactly my question. I am not seeking a user's shell environment. I am speaking of the login prompt. I am seeking a method of not having the hostname displayed in the login prompt. For example, I am currently seeing "ubuntu login>". I just wish to see "login>".

```
man getty
```

i believe getty controls it.

agetty or mgetty etc

---

