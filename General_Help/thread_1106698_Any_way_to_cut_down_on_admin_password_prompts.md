---
title: "Any way to cut down on admin password prompts?"
date: 2009-03-26
forum: General Help
---

### Post by iu34 on 2009-03-26
All these password prompts are just bugging me... Is there any way to disable them for installing updates and software?

---

### Post by evilaim on 2009-03-26
That is something you REALLY don't want to do.. but yes... sadly there is.  just type: sudo -i
enter it once and you're off to the races, but I HIGHLY don't suggest it, and please note anyone reading this, I don't suggest it!  It's just how you do it!

---

### Post by kanikilu on 2009-03-26
As mentioned, it's not necessarily a good idea, but check out the documentation, it should have all you need to know:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Might I suggest rather than disabling the prompt you just increase the timeout?

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

This will enable you to set a timeout to your preference so you don't have to put in a password *quite* so often, but also keeps you from running with root full time...

---

### Post by mb_webguy on 2009-03-26
+1

Increasing the timeout is a *much* better idea than disabling the password prompt entirely.

---

### Post by iu34 on 2009-03-26
okay..how do I do the "sudo visudo" editing part? I typed it in the terminal, edited the file with vim, but I can't save it! the "press escape then : to enter colon command mode" isn't working and I can't save!

---

### Post by mb_webguy on 2009-03-26
> **iu34 said:**
> okay..how do I do the "sudo visudo" editing part? I typed it in the terminal, edited the file with vim, but I can't save it! the "press escape then : to enter colon command mode" isn't working and I can't save!

I've never liked vi.

":x" should save and exit.  Getting to colon command mode can be annoying on occasion, even though you should be able to get there by just pressing Esc and then ":".  Try pressing Esc twice, then colon.

---

### Post by sgosnell on 2009-03-26
The reason it's so easy to infect a Windows machine with malware is that you don't need a password to change system settings.  Or at least one of the reasons - there are a number of them.

---

### Post by aeiah on 2009-03-26
ive never bothered to learn vi, vim etc. i probably should. nano is a very nice cli text editor though. its pretty much idiot proof

---

### Post by sgosnell on 2009-03-26
Ummm....  no, I don't think so.  I've seen a number of posts by people who couldn't successfully edit a file with nano.

---

