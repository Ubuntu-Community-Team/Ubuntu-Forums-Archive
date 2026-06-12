---
title: "Question about terminal"
date: 2009-12-11
forum: Desktop Environments
---

### Post by Ken_C on 2009-12-11
how does terminal remember what you typed when you press the Up Arrow key?
Sometimes I copy/paste passwords and I was wondering if this is a bad idea since ubuntu seems to keep track of whats been typed.

---

### Post by fancypiper on 2009-12-11
I believe it is recorded in the /home/<user>/.bash_history file.  That file doesn't have passwords that I can see and I often paste passwords.

---

### Post by Physical Hook on 2009-12-11
Password isn't a command - it's just an input request by another executable and is not being stored anywhere.

---

### Post by earthpigg on 2009-12-11
let's take a look at the last few commands stored in .bash_history and find out for sure:

> cat .bash_history

if you paste the password as part of a command, it ***will*** be remembered.

that is why i am NOT telling you to enter:

> cat .bash_history | grep mypasswordhere
(dont enter that)

but, while on the subject of passwords stored as plain text...

(look to make sure no one is reading over your shoulder right now)
> cat ~/.purple/accounts.xml | grep password

so, if your IM passwords are the same as any of your banking passwords or private email passwords... make sure only people you trust use your computer with you logged in :D

a bad guy with physical access to your computer could also select 'boot to recovery mode' from the grub menu to get access to that file with***out*** you needing to be logged in.

any passwords you have saved in firefox are the same, btw.

---

### Post by Lars Noodén on 2009-12-13
> **Ken_C said:**
> how does terminal remember what you typed when you press the Up Arrow key?
Sometimes I copy/paste passwords and I was wondering if this is a bad idea since ubuntu seems to keep track of whats been typed.

It depends on which shell (UI) you are using inside the terminal.  
For Ubuntu, the default is bash.  So if no one's changed anything, then you are probably using bash and can clear the history this way by overwriting your bash history:

```

echo > ~/.bash_history

```

**echo** is like print, but with no options it prints nothing.
**>** is a redirect to send the output from the previous program into a file
**~** is a shortcut for your home directory

So 'nothing' is printed into the file where bash keeps its history.  

Some other shells handle this differently than bash. For example, **ksh** keeps a history but only in memory so that it goes away when you exit the session.

---

