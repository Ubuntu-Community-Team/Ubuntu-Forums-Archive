---
title: "How do I tell which version of a Gnome Shell Extension is installed?"
date: 2021-03-09
forum: Desktop Environments
---

### Post by Paddy Landau on 2021-03-09
When I have a Gnome extension installed (e.g. [Caffeine]("https://extensions.gnome.org/extension/517/caffeine/")), how can I tell which version is currently installed?

Searching online gives me no answer.

---

### Post by tea for one on 2021-03-09
Some extensions have an [COLOR="#0000FF"]about[/COLOR] info in settings/configuration e.g. Dash to Panel

Also, there is some info in this path :-

/home/[COLOR="#0000FF"]user[/COLOR]/.local/share/gnome-shell/extensions/[COLOR="#0000FF"]extension-folder[/COLOR]/metadata.json

---

### Post by Dennis N on 2021-03-09
> **Paddy Landau said:**
> When I have a Gnome extension installed (e.g. [Caffeine]("https://extensions.gnome.org/extension/517/caffeine/")), how can I tell which version is currently installed? Searching online gives me no answer.

In Extensions, click the arrow to the right of any extension. This reveals the version. See Screenshot, where "Applications Menu" is revealed to be version 44.

---

### Post by ActionParsnip on 2021-03-09
```

apt-cache policy gnome-shell

```

will show you. Oh you mean the version of the addon. Is that right please?

---

### Post by Paddy Landau on 2021-03-09
> **ActionParsnip said:**
> Oh you mean the version of the addon. Is that right please?
Yes, the Gnome Shell Extension (as an add-on is called).
> **tea for one said:**
> /home/[COLOR=#0000FF]user[/COLOR]/.local/share/gnome-shell/extensions/[COLOR=#0000FF]extension-folder[/COLOR]/metadata.json
This works.
> **Dennis N said:**
> In Extensions, click the arrow to the right of any extension.
This is the easy way :)

Thank you for your responses.

---

### Post by tea for one on 2021-03-09
> **Dennis N said:**
> In Extensions, click the arrow to the right of any extension. This reveals the version. See Screenshot, where "Applications Menu" is revealed to be version 44.

Interesting nugget - I've not noticed the little arrow before.
Much better answer than my suggestion.

---

