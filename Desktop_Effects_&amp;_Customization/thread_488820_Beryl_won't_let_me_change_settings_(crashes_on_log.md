---
title: "Beryl won't let me change settings (crashes on login)"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by eoghanmurray on 2007-06-30
I accidentally changed a Beryl advanced setting from AIXGL I think, to XGL. When I start beryl-manager, X crashes and i have to resort to Ctrl+Alt+Bckspc. Is there any way of editing Beryl's advanced settigns without actually loading Beryl itself?

(Metacity is window manager)

---

### Post by eoghanmurray on 2007-06-30
Is there a way I can edit a *.conf file or use the terminal?

---

### Post by hyperair on 2007-07-01
To edit a text file (*.conf files are text files) in the terminal, use the command "nano"
```

nano whateverconffile.conf

```

Also, you might want to just reset your Beryl Manager settings:
```

rm ~/.beryl-managerrc

```

Just use the second code given. I think it should work.

---

