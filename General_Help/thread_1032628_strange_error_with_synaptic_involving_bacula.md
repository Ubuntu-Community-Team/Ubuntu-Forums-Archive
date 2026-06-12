---
title: "strange error with synaptic involving bacula"
date: 2009-01-06
forum: General Help
---

### Post by metacym on 2009-01-06
when attempting to run Synaptic, i am also prompted: "an error occurred. E: dpkg was interrupted, you must manually run 'dpkg --configure -a'
to correct the problem.

E:_cache->open()failed, please report."

Then, when i go to run that command in terminal, i immediately get this error:
"Package configuration, Configuring bacula-director-mysql

password mismatch

the password and it's confirmation do not match. please reenter the passwords. Ok"

Only the terminal window looks like a linux-installer, and the terminal does not provide anywhere to type, nor will the "ok" button yield
any results, change or environment, or a cursor to enter commands with.


And just to through another curveball in there, After the first time this happened, i went to try and remove "bacula" and "mysql" and i was told that neither were installed.

...any ideas ? 


help would be greatly appreciated.
i also have IM on: [email]sunyata4@mac.com[/email]


specs: Ubuntu 8.04
linux kernel 2.6.24-22-generic
Gnome 2.223
emachines intel Celeron D 3.46ghz

---

### Post by zvacet on 2009-01-06
Did you run that command like this

```
sudo dpkg --configure -a
```

---

### Post by metacym on 2009-01-06
> **zvacet said:**
> Did you run that command like this

```
sudo dpkg --configure -a
```



yes, i tried that. It would bring me back to the the original 
error messages about "bacula-director  passwords do not match"

I hate inconclusive-fixes, almost more than i hate inconclusiveness.
but unfortunately, it seems this problem has evaded me.

I not got synaptic started without the error. And i dont recall doing anything that would have fixed it. But never-the-less, synaptic was stable long enough for me to mark "remove" on everything related to bacula. So onward and upward to the next issue i suppose. 

thanks though.

---

