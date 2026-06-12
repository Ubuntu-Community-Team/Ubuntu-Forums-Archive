---
title: "Weird problem with Compiz Fusion and Emerald"
date: 2008-12-20
forum: General Help
---

### Post by neo1985 on 2008-12-20
Hello there,

I have a weird problem with my Compiz Fusion & Emerald als Theme manager. Compiz runs very nice, and emerald did the same too. But after a few days, emerald does not start now anymore when I log into KDE. What I get is a full Compiz environment, but with kwin as theme manager. When I now run **emerald --replace** in a shell, it runs as it should.

Now the best of all: "Window Decorations" is enabled in the CompizConfig Settings Manager. When I disable it, my windows loose their frames. When I enable it again, kwin is set as window manager, again. But "emerald" is there as Command?

I tried to resolve this with a startup-script, but this is not the solution I want - why did it first worked?

Please look at the following screenshots.

This is what I get when KDE starts up: The ordinary KDE theme. Window Decoration is enabled.
[img]http://www.jmksf.de/temp/temp1.png[/img]

Now, when I disable Window Decoration, I get
[img]http://www.jmksf.de/temp/temp2.png[/img]

As mentioned: "emerald --replace" gives me what I want!
[img]http://www.jmksf.de/temp/temp3.png[/img]

I hope there is a solution.

Regards,
neo

---

### Post by binbash on 2008-12-20
emerald --replace is the command you will enter to decorations plugin.

---

### Post by neo1985 on 2008-12-20
> **binbash said:**
> emerald --replace is the command you will enter to decorations plugin.

I tried this even too. It did not work.
It looks as emerald is unable to start from compiz?

I don't know - what I know is that it worked.

---

### Post by geekman on 2008-12-21
I'm tired so forgive me if I'm totally wrong here, but it sounds like you're trying to set Emerald as your default decoration manager so it is set when you start up?  You can edit compiz so that it runs Emerald for you, so that if Emerald dies it can then fall back on it's own decoration manager.  To do this you must change /usr/bin/compiz-decorator and /usr/bin/compiz-manager, and change the use USE_EMERALD = "no" to USE_EMERALD = "yes", if you then restart your window manager with Ctrl+Alt+Backspace and log back in, it should take effect.

Sorry if this isn't want you meant :P.

---

