---
title: "Start Fluxbox"
date: 2004-11-26
forum: Desktop Environments
---

### Post by Miles on 2004-11-26
I'd like to start fluxbox with any other application like gkrellm or gdesklets.

An irc user told me to start fluxbox with "startfluxbox", then it will make a "startup" file on  $.fluxbox folder where i could add as many application I desire.

Well, the thing is a I have no startfluxbox choice in my system.

Any help?

Thanks in advance.

---

### Post by p!=f on 2004-11-26
[QUOTE=Miles]I'd like to start fluxbox with any other application like gkrellm or gdesklets.

An irc user told me to start fluxbox with "startfluxbox", then it will make a "startup" file on  $.fluxbox folder where i could add as many application I desire.

Well, the thing is a I have no startfluxbox choice in my system.

Any help?

Thanks in advance.[/QUOTE]
Do you want Fluxbox to be your window manager or you want to run Fluxbox as your desktop environment?

If second, two choices:
1) Select a Fluxbox session in GDM/KDM
2) Create a file .xsession in your $HOME and edit it like this:
```

[~] > cat .xsession
#!/bin/sh
exec /usr/bin/fluxbox

```
I'm not sure how Fluxbox handles autostarting other applications but adding "gkrellm &" under fluxbox line may help.

3) Login on the console and run
```

startx -- :1

```
This will start another xserver on a new display. You may then switch between those desktops using CTRL+ALT+F7/F8.

---

### Post by TopDog on 2004-12-20
If I understand right, you want for example gaim to start when you login to Fluxbox?

Edit the file called **~/.xinit** with a line like:

**gaim &**

The **&** is important, it keeps the application alive.

More on Flux here: [http://fluxbox.sourceforge.net/docs/en/faq.php](http://fluxbox.sourceforge.net/docs/en/faq.php)

---

