---
title: "Transparent terminal with xcompmgr"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by JMO707 on 2007-09-22
I've been looking for a way to make gnome-terminal (or any other, if that is necesary) true transparent with xcompmgr. I use Openbox, and transset is not what I'm looking for. It makes *everything* transparent, when I just whant the background of it.
I couldn't, neither, found a solution in the forums.

Ideas?

---

### Post by JMO707 on 2007-09-23
One more try =)

---

### Post by shirilover on 2007-09-24
I use rxvt-unicode with the following arguments:

```

urxvt -depth 32 -geometry 188x38 -tr +sb -fg white -bg rgba:0000/0000/0000/7777 -tint grey -sh 75 -fade 15 -fadecolor black -pr black -pr2 white

```

which gives me a transparent terminal background. Granted, there are no scrollbars or menu bar, but I don't need those.

---

### Post by FuturePilot on 2007-09-24
If you set the Terminal background to transparency (Edit>Current Profile>Effects) when a composite manager is enabled, the background will switch from pseudo transparency to true transparency.

---

### Post by JMO707 on 2007-09-24
Thanks shirilover. I should try with other terminals. The only thing that keeps me on gnome-terminal is the copy&paste menu.

I've tried, FuturePilot, seeing that with Compiz that was exactly what happened, but with xcompmgr doesn't seem to work.

---

### Post by JMO707 on 2007-09-27
> **shirilover said:**
> I use rxvt-unicode with the following arguments:

```

urxvt -depth 32 -geometry 188x38 -tr +sb -fg white -bg rgba:0000/0000/0000/7777 -tint grey -sh 75 -fade 15 -fadecolor black -pr black -pr2 white

```

which gives me a transparent terminal background. Granted, there are no scrollbars or menu bar, but I don't need those.

Sorry shirilover, but do you know where I can look for those options to manipulate them?, oddly, I dont have any man page of rxvt-unicode, and couldn't find too much on the internet.

---

