---
title: "Remotely grabbing text from a gedit file?"
date: 2009-04-25
forum: General Help
---

### Post by chrisamiller on 2009-04-25
Here's the situation:

1) At work, I have gedit open on my desktop. It's open to an unsaved document, with a bunch of text in it.

2) I am at home, and can ssh into my work computer.  Is there any way to retrieve that text from gedit?

Both computers are running Jaunty (9.04).

Any suggestions that don't involve me spending a half-hour round trip to retrieve a few lines of text?

Ideas: I know gedit does auto-saving and creates temporary files when you're editing a previously saved document.  Does it do anything simlar for unsaved files?

Correct me if I'm wrong, but I don't think using VNC would help, as it starts a new X-session and wouldn't let me see my current desktop (which contains gedit, and the relevant code)

---

### Post by HermanAB on 2009-04-25
Yesh...

You can tell X to switch the screen from the desktop to the SSH session.  However, I haven't ever needed to do that, so you need to Google and read up on X.

The half hour round trip will be faster - this time anyway.

---

