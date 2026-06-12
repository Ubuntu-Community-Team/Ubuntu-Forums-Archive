---
title: "Tomboy at startup"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Gujs on 2007-04-26
Hello,

I added tomboy to my session, that it runs when I log in. How can I prevent tomboy to display search dialog at startup?

Thanks

---

### Post by ComplexNumber on 2007-04-26
> **Gujs said:**
> Hello,

I added tomboy to my session, that it runs when I log in. How can I prevent tomboy to display search dialog at startup?

Thanks
i'm not sure what you're trying to do by adding it to your session.  all you have to do is add it to your panel, and thats it. after that, it will stay on your panel. delete it from your sessions because its not necessary.

---

### Post by Gujs on 2007-04-26
Thanks, I don't know how have I missed that I can add it to panel.

---

### Post by kevinlyfellow on 2007-05-22
> **Gujs said:**
> Thanks, I don't know how have I missed that I can add it to panel.

I didn't know that either!  For some reason this seems to be a not-so-uncommon misunderstanding.

---

### Post by nagylzs on 2007-05-22
I think that the OP was right about his question. Yes, you can add Tomboy to the panel. But it will be a launcher for the tomboy application. I believe the OP wanted to know how to start tomboy automatically, without displaying the main window ("Search all notes").

I think that Tomboy should have a command line option that will prevent displaying the main window. E.g. it should only appear as a small icon beside the clock. Is this possible?

---

### Post by laptoplinux on 2007-05-22
Been there, done that, problem solved:

[http://ubuntuforums.org/showthread.php?t=446743]("http://ubuntuforums.org/showthread.php?t=446743")

Here is the relevant info:

My problem was that I had placed a tomboy applet in the panel, but I also called tomboy as a startup program. Therefore, tomboy was getting called twice at startup since the panel applet always loads at startup and the startup process list calls it again. Hence the window popping up. If you run/execute/call tomboy when the application is already open, it pops up the "Search all notes" window. So either put it in as a panel applet or call it from the sessions startup program list, but don't do both. That should solve the problem.

(RESOLVED)

---

### Post by kevinlyfellow on 2007-05-23
@nagylzs

The applet in feisty fawn acts like if you were to run the command tomboy without options except that it isn't bound to the notification area.

@laptoplinux

I found your post before I came here.  Actually if you run _just_ the tomboy command at startup, the search window pops up.  Your problem was a different one.

---

