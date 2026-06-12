---
title: "how to view .config in open file dialog?"
date: 2023-11-28
forum: Desktop Environments
---

### Post by ubontik22 on 2023-11-28
Dear Experts,

How to view .config in open file dialog?

Thank you

---

### Post by TheFu on 2023-11-28
Type in "~/.config/" without the quotes.

However, it would be best to not use any GUI tool in that area. There are reasons.

---

### Post by ubontik22 on 2023-11-28
Thank you, but I needed from GUI. I already figured out. RMC on Title Bar of an Open File dialog box.

---

### Post by The Cog on 2023-11-28
I'm curious to know the reasons you think it's not a good idea. I'd feel quite happy having a look there with Nemo. I just did, and was surprised how much cruft I've accumulated in there.

---

### Post by ajgreeny on 2023-11-28
> **The Cog said:**
> I'm curious to know the reasons you think it's not a good idea. I'd feel quite happy having a look there with Nemo. I just did, and was surprised how much cruft I've accumulated in there.
Likewise!
You have only to install an application and start it running for a folder to be created there or sometimes in the root of your home folder. 
If you then decide you don't want or need that application those folders will remain in your home. It is very easy to collect huge amounts of unneeded folders and files if you never clean them out after removing an application.
I also wonder why you say using a GUI file manager is not a good idea; I'm aware you are vrh much a cli user but I think you are unusual in that respect and that most Ubuntu users are GUI users.

---

### Post by TheFu on 2023-11-28
I didn't say not to use a file manager in those directories.  The OP was using an editor based on the File-Open dialog.  Based on the question, I assumed a non-sophisticated user. People get into habits and they quickly form habits using GUI programs everywhere rather than noticing the subtle differences in which programs are save to use in their HOME and which are safe to use for system stuff. For $HOME, it shouldn't matter. But just 1 mistake, 1 time, trying to edit system files using a GUI program often has undesirable side effects, it seems.  Eventually, the old settings for sudo will become unsupported and we won't need this caveat. I understand that newer sudo versions set the HOME variable to that of the userid it switches into. That's good and bad. Depends on your point of view.  But there are caveats for when it is safe and when it isn't ... to to minimize confusion and provide an option that is always safe, don't use GUI editors in ~/.config/.  Of course, people will have different opinions about that.

I've seen people use GUI editors in their first login session and lock themselves out (into a boot-loop) because the GUI programs created root-owned directories under ~/.config/.  Basically, their own userid couldn't access or override what the root account had already done and failed, badly. Crashing over and over and over and over as the GUI programs tried to access ~/.config/ stuff, but couldn't.

---

