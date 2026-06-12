---
title: "GAIM Password cracker?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-08-17
Hi all,

Would like to find a little util that would show me all passwords entered/saved on my system.  Especially my GAIM as I have forgotten it.  :-({|= 

Any assistance, much appreciated.  ;) 

Ian

---

### Post by frenkel on 2006-08-17
Run this on a terminal:

$ cat ~/.gaim/accounts.xml  | egrep "<name>|<password>"

It will print out all accounts with passwords you have in Gaim. You need to have checked "save my password" in Gaim off course.

---

### Post by Ramses de Norre on 2006-08-17
I don't get why people always use cat to pipe files to grep..
This does the same: ```
egrep "<name>|<password>" ~/.gaim/accounts.xml

```

---

### Post by The Pinny Parlour on 2006-08-17
Thank you for your prompt reply.  Unfortunately it does not work.  
Thank you for attemping to solve my issue. 

Ian

---

### Post by The Pinny Parlour on 2006-08-17
oh.... just to add

I cut & paste everything you had written in Terminal
bash: $: command not found

---

### Post by The Pinny Parlour on 2006-08-17
> **Ramses de Norre said:**
> I don't get why people always use cat to pipe files to grep..
This does the same: ```
egrep "<name>|<password>" ~/.gaim/accounts.xml

```

Now this did work.  Thank you very much.

---

### Post by The Pinny Parlour on 2006-08-17
One more question.  Is there a util that will show ALL passowrds on ones ubuntu system?   That would help me greatly.

Ian

---

### Post by Ramses de Norre on 2006-08-17
Most of them are stored encrypted, it amazed me a lot that gaim passwords aren't.. So I guess no.

---

### Post by The Pinny Parlour on 2006-08-17
> **Ramses de Norre said:**
> Most of them are stored encrypted, it amazed me a lot that gaim passwords aren't.. So I guess no.

ok... thank you.  Great answer, gave me an explanation as to why as well.

Cheers,
Ian

---

### Post by frenkel on 2006-08-17
> **The Pinny Parlour said:**
> ok... thank you.  Great answer, gave me an explanation as to why as well.

Cheers,
Ian

> **The Pinny Parlour said:**
> oh.... just to add

I cut & paste everything you had written in Terminal
bash: $: command not found

I put the $ in front to show you, you had to put it in a terminal. You should copy paste everything after it.

This is how to show it for all your users on the computer:

$ for i in /home/*; do egrep "<name>|<password>" $i/.gaim/accounts.xml; done


Edit:
Ah, I think I didn't understand your question right. You want to see all your passwords from all your applications (which applications? lots of them are stored in plain text so that should be possible)? Or do you want to see the Gaim password of all your users?

---

### Post by The Pinny Parlour on 2006-08-17
> **frenkel said:**
> I put the $ in front to show you, you had to put it in a terminal. You should copy paste everything after it.

This is how to show it for all your users on the computer:

$ for i in /home/*; do egrep "<name>|<password>" $i/.gaim/accounts.xml; done


Edit:
Ah, I think I didn't understand your question right. You want to see all your passwords from all your applications (which applications? lots of them are stored in plain text so that should be possible)? Or do you want to see the Gaim password of all your users?

No you understood correctly.  It was a 2 part question.  Firstly to find GAIM password.  Then a general question regarding a util that would reveal ALL passwords for all and any programs that have passwords stored on my PC.

Cheers,
Ian

---

