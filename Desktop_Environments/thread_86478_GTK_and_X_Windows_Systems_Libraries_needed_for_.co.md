---
title: "GTK and X Windows Systems Libraries needed for ./configure?"
date: 2005-11-05
forum: Desktop Environments
---

### Post by erik-the-red on 2005-11-05
I'm trying to install fluxbox by source. I know it is available through the apt repositories, but I have tried that under Hoary and I thought it was choppy.

The error at the end of ./configure for fluxbox is:

```

configure: error: Fluxbox requires the X Windows System libraries and headers.

```

What should I retrieve from the CD in order to be able to go through this compilation process?

I'm also trying to install audacity by source, even though I know it is also available through the apt repositories. I'm using it now, but it's kind of acting up in multitrack recording, so I'm thinking about going hardcore with the source compilation.

The thing is I need the wxWidgets library. When I finished it's - the wxWidgets' - ./configure, the error came up that I needed the GTK2+ development things.

What should I retrieve from the CD in order to be able to go through this compilation process?

Thanks in advance.

---

### Post by Xian on 2005-11-05
[QUOTE=erik-the-red]I'm trying to install fluxbox by source. I know it is available through the apt repositories, but I have tried that under Hoary and I thought it was choppy.

The error at the end of ./configure for fluxbox is:

```

configure: error: Fluxbox requires the X Windows System libraries and headers.

```[/quote]
You will want to try installing the x-window-system-dev package.

[QUOTE=erik-the-red]The thing is I need the wxWidgets library. When I finished it's - the wxWidgets' - ./configure, the error came up that I needed the GTK2+ development things.[/QUOTE]
I believe this is the libwxgtk and libwxgtk-dev packages.

---

### Post by taurus on 2005-11-05
Try installing both build-essential and x-window-system-dev,

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get x-window-system-dev

---

### Post by erik-the-red on 2005-11-05
Thanks. I believe those will work. It's getting kind of late now, so I'll do it tomorrow morning.

---

