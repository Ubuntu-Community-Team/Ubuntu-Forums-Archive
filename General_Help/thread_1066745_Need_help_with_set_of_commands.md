---
title: "Need help with set of commands"
date: 2009-02-11
forum: General Help
---

### Post by kingchipo on 2009-02-11
Im having a problem with installing my soundcard drivers.

Im installing drivers for an old isa card and im running ubuntu 8.10 on a dell precision workstation 610

im trying to run this command....

```
       cd /usr/src
       mkdir alsa
       cd alsa
       cp /downloads/alsa-* .
```

Everythings fine untill the last command were i get.....

cp: missing destination file operand after `/downloads/alsa-*'

i dont understand the conflict can anyone help me sort out this situation so i can get my sound card working?

---

### Post by x33a on 2009-02-11
you aren't specifying the destination directory.

see man cp for more options.

---

### Post by snova on 2009-02-11
> **kingchipo said:**
> ```
       cp /downloads/alsa-* .
```

Everythings fine untill the last command were i get.....

cp: missing destination file operand after `/downloads/alsa-*'

i dont understand the conflict can anyone help me sort out this situation so i can get my sound card working?

There's a dot at the end of that command. :)

```
cp /downloads/alsa-* **.**
```

On a side note, I don't know why there would be a /downloads folder... it shouldn't exist.

I can only assume you downloaded a file somewhere. If it's on your Desktop, for example, you would use:

```
cp ~/Desktop/alsa-* **.**
```

Or if it's in your home directory:

```
cp ~/alsa-* **.**
```

(The ~ symbol is essentially short for, "Your home directory")

---

