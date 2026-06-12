---
title: "Any idea what does this file do? ---&gt; /usr/bin/["
date: 2009-06-01
forum: General Help
---

### Post by nebileix on 2009-06-01
As the title. 

Any idea anyone?

---

### Post by sisco311 on 2009-06-01
```
man [
```
;)

[s]It is a synonym for *test*, and a builtin for efficiency reasons.[/s]

---

### Post by 73ckn797 on 2009-06-01
> **nebileix said:**
> As the title. 

Any idea anyone?


The same file is in my installation and it is an executable file. It is probably there for a reason so I would just ignore it.

---

### Post by nebileix on 2009-06-01
> **sisco311 said:**
> ```
man [
```
;)

It is a synonym for *test*, and a builtin for efficiency reasons.

Thanks dude. Didn't thought that name using "[" has a man pages as well.. LOL!!!

Cheers!!!

---

### Post by michy99 on 2009-06-01
Did you try```
man [
```

Edit: Boy, am I slow:)

---

### Post by nebileix on 2009-06-01
> **73ckn797 said:**
> The same file is in my installation and it is an executable file. It is probably there for a reason so I would just ignore it.

Well, be safe then sorry. Cuz using the square bracket as filename looks suspicious.

---

### Post by Slim Odds on 2009-06-01
> **sisco311 said:**
> ```
man [
```;)

It is a synonym for *test*, and a builtin for efficiency reasons.

It's a "builtin" for bash, but that file can be used for other shells.

---

### Post by nebileix on 2009-06-01
> **michy99 said:**
> Did you try```
man [
```

Edit: Boy, am I slow:)

nah... its fine man. thks for the info.

Cheers...

---

### Post by 73ckn797 on 2009-06-01
> **nebileix said:**
> Well, be safe then sorry. Cuz using the square bracket as filename looks suspicious.


I understand. Linux is a different beast for sure. Beast being a good thing.

---

### Post by sisco311 on 2009-06-01
> **Slim Odds said:**
> It's a "builtin" for bash, but that file can be used for other shells.

Indeed, [ and test are commands contained within the Bash tool set and /usr/bin/\[ and /usr/bin/test are *standalone* commands.

---

### Post by t0p on 2009-06-01
> **73ckn797 said:**
> The same file is in my installation and it is an executable file. It is probably there for a reason so I would just ignore it.

Well, as it happens there *is* a reason for /usr/bin/['s existence (as other people have told us, it's a synonym for **test**).  But your policy of "It is probably there for a reason so I would just ignore it" does not say much for your security-consciousness.  You find a mysterious executable on your system; someone else has it on their system too; so you decide to just ignore it?  What if it were a surreptitiously-planted bit of malware that had infected several computers including yours and your colleague's?  What if its reason for being was to log your key-strokes and send them to an evil h4x0r?  Just ignore it eh?

The OP did the right thing: he found something extraordinary (in his experience) on his machine, so he came to a trustworthy-ish community and asked what the mysterious file might be.  A lesson for us all.

---

### Post by 73ckn797 on 2009-06-01
> **t0p said:**
> Well, as it happens there *is* a reason for /usr/bin/['s existence (as other people have told us, it's a synonym for **test**).  But your policy of "It is probably there for a reason so I would just ignore it" does not say much for your security-consciousness.  You find a mysterious executable on your system; someone else has it on their system too; so you decide to just ignore it?  What if it were a surreptitiously-planted bit of malware that had infected several computers including yours and your colleague's?  What if its reason for being was to log your key-strokes and send them to an evil h4x0r?  Just ignore it eh?

The OP did the right thing: he found something extraordinary (in his experience) on his machine, so he came to a trustworthy-ish community and asked what the mysterious file might be.  A lesson for us all.

Nice reply.

---

### Post by t0p on 2009-06-01
> **73ckn797 said:**
> Nice reply.

Hmm.  On reflection, more arsey than was necessary.

That's (one of) the problem(s) with the internet: you can read my words but you can't see me smile.

:D  <==me smiling

---

### Post by 73ckn797 on 2009-06-01
> **t0p said:**
> Hmm.  On reflection, more arsey than was necessary.

That's (one of) the problem(s) with the internet: you can read my words but you can't see me smile.

:D  <==me smiling


I saw your point and understand. I have seen that file before in multiple installations so that was why I was not concerned.

YEP sometimes clear communication is lost when not accompanied by the person present. I guess that is why Smilies were created.  ):P

---

### Post by Slim Odds on 2009-06-01
> **t0p said:**
> That's (one of) the problem(s) with the internet: you can read my words but you can't see me smile.

In an unfortunate case of further diverting from the original topic, I just have to mention of the funnier comments that I read about what you just said.

On the Internet you don't have to have a big unit (I hope you know what I mean) to tell someone else that theirs is small.

:D

---

