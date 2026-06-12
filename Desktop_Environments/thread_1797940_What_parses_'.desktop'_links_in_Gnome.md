---
title: "What parses '.desktop' links in Gnome?"
date: 2011-07-05
forum: Desktop Environments
---

### Post by c.cobb on 2011-07-05
Greetings,
I've got a link named 'getting_started.desktop' on my Desktop (Ubuntu 10.04, Gnome). What actually parses this file when you double-click it? It's clearly not the /usr/bin/xdg-open script, as inserting an echo there proves.
Thank you,

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Encoding=UTF-8
Name=Getting Started
Name[es]=Introducción
Comment=A brief overview
Comment[es]=Una breve descripción
Type=Link
URL=file:///usr/share/example-content/getting_started.html
Icon=firefox
```

---

### Post by c.cobb on 2011-07-09
FWIW, it's the 'slurp_key_string()' function in 'libnautilus-private/nautilus-link.c'

I was hoping that it might be an easy hack to implement localization on the URL string which, according to the [Desktop Entry Spec]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys") is unfortunately not a 'localestring'. Seems strange to me. Anyway that would take more digging, as I'm not much of a c hacker.

---

