---
title: "How does the GDM login process work?"
date: 2009-07-16
forum: Desktop Environments
---

### Post by Tails9 on 2009-07-16
Hi,

I would like to write something that shows the progress of loading the Gnome desktop when a user logs in, as described here: [http://brainstorm.ubuntu.com/idea/10568/](http://brainstorm.ubuntu.com/idea/10568/)

I know Gnome had this little splash screen that showed which programs were loaded, but my problem with this thingy is that Gnome isn't fully loaded when the splash disappears.

I have a few orientation questions though,
- does the GDM process ('gdm') account for loading the gnome desktop?
- if it does, how does it initialize the panels and how does is start the session applications that should be started on login? Does it do this like Windows, that it starts all startup-applications asynchronous? Or do the programs (and panels) get started sequentially?

- Luuk

---

### Post by Tails9 on 2009-07-20
*bump*

---

### Post by Anzan on 2009-07-20
Good question.

Look here:

[http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_US.ISO_8859-1/articles/gdm-reference/gdm-reference/index.html]("http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_US.ISO_8859-1/articles/gdm-reference/gdm-reference/index.html")

---

### Post by Tails9 on 2009-07-20
Thanks! I'll read into that. :)

---

