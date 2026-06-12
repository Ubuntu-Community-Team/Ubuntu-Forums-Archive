---
title: "Trouble with custom panel launcher"
date: 2010-12-20
forum: Desktop Environments
---

### Post by SaintDanBert on 2010-12-20
I add the following command text to a custom panel launcher:
```

/usr/bin/zenity --info --text "$(/usr/bin/ibam -a)" &

```

I get the zenity pop-up but it reports only 
```

$(/usr/bin/ibam -a)

```

From a shell command line, I get the same ibam output with and without the zenity pop-up.

Q1: How do I get this to work with zenity or similar from a gnome panel launcher?

Q2: Please direct me to descriptions of the panel-->command-->shell mechanics. It looks like I might need to wrap my desired command with **bash -c** or similar so that shell substitution happens.

Merci d'avance,
~~~ 0;-Dan

---

### Post by mcduck on 2010-12-21
Try this one:
```
/usr/bin/ibam -a | /usr/bin/zenity --text-info
```

..not sure if that would work directly in a launcher, though. You might have to make it into a script and point the launcher to that instead.

---

### Post by SaintDanBert on 2010-12-21
I had to use the following
```

bash -c '/usr/bin/zenity --title="Battery State" --text-info "$(/usr/bin/ibam -a)&'

```

in the panel launcher.

Your pipe solved part of the problem and showed me that I needed
a shell for all to work correctly.

Thanks,
~~~ 0;-Dan

---

