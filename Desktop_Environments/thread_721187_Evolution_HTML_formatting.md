---
title: "Evolution HTML formatting"
date: 2008-03-11
forum: Desktop Environments
---

### Post by josef.sabl on 2008-03-11
I have a problem with Evolution Mail. It seems to discard all the style from HTML emails.

The main issue with this behavior is I cannot insert my HTML formated signature as it gets stripped of all the style and looks differently than I want.

Is this a feature or a bug? Can it be turned off?

---

### Post by dcstar on 2008-03-11
> **josef.sabl said:**
> I have a problem with Evolution Mail. It seems to discard all the style from HTML emails.

The main issue with this behaviour is I cannot insert my HTML formatted signature as it gets stripped of all the style and looks differently than I want.

Is this a feature or a bug? Can it be turned off?

Like all HTML e-mail clients, Evolution will only support parts of what HTML can do - it looks like Styles aren't part of it.

HTML e-mail is handicapped by the lack of standards - different clients support different things, if you are lucky the HTML formatting in a message is basic enough to render correctly in most clients, if you aren't lucky you get anything from an unreadable message through to various levels of display weirdness.

---

### Post by josef.sabl on 2008-03-11
Ok, that makes sense, but there are two parts that I still find quite unacceptable about Evolutions behaviour.

1. Thunderbird, Outlook 2003, Outlook 2007, Outlook Express, Gmail, Hotmail as well as some other more obscure email clients are all fine displaying our html signature. The lack of such properties makes Evolution exceptionally bad email client.

2. The main problem is not at all in displaying email messages. I don't mind when my signature looks bad on my PC. But Evolution not only does not display whatever is in styles, it also strips email message of content I explicitly put there.

So what do we have here: 1. Evolution is bad in interpreting things. 2. It removes everything that it fails to interpret although it does not have to.

I am sure this needs fixing.

---

### Post by trippinnik on 2008-03-11
Wow, thanks for the thread.  I have been going nuts.  I have a small app I've made that get some info from a DB and then makes an HTML table and sends it in the body of the email.  I couldn't figure out why it wasn't working. Just tried it in thunderbird and it works perfectly. It's a good thing there's plenty of choice in Linux.

---

### Post by josef.sabl on 2008-03-11
> **trippinnik said:**
> Wow, thanks for the thread.  I have been going nuts.  I have a small app I've made that get some info from a DB and then makes an HTML table and sends it in the body of the email.  I couldn't figure out why it wasn't working. Just tried it in thunderbird and it works perfectly. It's a good thing there's plenty of choice in Linux.

Funny and sad at the same time. I decided to switch from Thunderbird to Evolution this morning and already am regretting this move.

Another cool superbug in Evolution:
1) write a long e-mail (does not need to be long, it was long in my case)
2) structure it with built in styles (bulleted, heading 1)
3) select the whole text
4) lose all the formatting you were doing all the afternoon.

Thanks the undo function for not being broken. I am still wondering why selecting text needs to null its formatting.

Come on, is this alpha version or what? I thought it was put to Ubuntu because it is stable.

**Update**
Yet another cool superbug:
1) write an email
2) decide to paste the contents somewhere else
2a) Ctrl+A
2b) Ctrl+C
3) close email window
4) Ctrl+V elsewhere
4a) repeat
4b) repeat
4c) bash keyboard
4d) yell with desperation
5) write content again as for some reason Evolution purges clipboard when you close one of its windows

This time, no undo function will save your day

---

