---
title: "X11 forwarding without leaving terminal open"
date: 2009-03-03
forum: General Help
---

### Post by a person on 2009-03-03
I'd like to keep my remote computer's firestarter on my desktop so I can check it/create rules/etc...

Currently I have been doing:

```

ssh -X user@host
firestarter&

```

I'd like to be able to do this without leaving a terminal open.  Any ideas?

---

### Post by adult swim on 2009-03-03
try running
```
nohup firestarter
``` i just ran it and closed the terminal and it worked.  it did give a message about the application would be closed when the terminal window was closed but it stayed open despite the message.

---

### Post by a person on 2009-03-03
> **adult swim said:**
> try running
```
nohup firestarter
``` i just ran it and closed the terminal and it worked.  it did give a message about the application would be closed when the terminal window was closed but it stayed open despite the message.

Closes every time for me.

---

### Post by Keilaron on 2010-05-04
I know this is an old thread, but it's the first relevant Google result I found (while searching for *linux x11 forwarding without terminal*) so I'm hoping it'll help others too.
The solution was really simple for me -- things I already knew, but just never thought of for some reason. This is all you have to do:
[LIST=1]
[*]Create an [SSH key pair]("http://pkeck.myweb.uga.edu/ssh/") (either without passphrase, or [with ssh-agent]("http://mah.everybody.org/docs/ssh")) and upload the public key to your app server (arguably, you should already have this set up, but anyway)
[*]Test to make sure you can connect without supplying a password
[*]Create a launcher that executes, for example,```
ssh -X myserver.lan pidgin
```
[/LIST]
Obviously, the third step is a bit much if it's a one-time deal, but for any applications you execute often, it's a huge time-saver: Just click the launcher and you're good to go, almost as though it were local.

---

