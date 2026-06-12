---
title: "[SOLVED] catfish configuration"
date: 2008-12-12
forum: General Help
---

### Post by pseudonym on 2008-12-12
I'd like to change the default search settings in catfish but there's no way of doing so from within the gui. I searched for a config file but there was no obvious candidate which came up. Does anyone know which file I need to edit?

Thanks.

---

### Post by moncojhr on 2008-12-13
I've modified catfish so you can change the default search settings, also fixed it so folders open properly in nautilus. I'll post it up if your interested.

---

### Post by pseudonym on 2008-12-13
> **moncojhr said:**
> I've modified catfish so you can change the default search settings, also fixed it so folders open properly in nautilus. I'll post it up if your interested.

Yeah, that'd be great. Thanks. I don't use Nautilus, though, because I'm running Xubuntu.

---

### Post by moncojhr on 2008-12-13
Alright, well all you need to do is...

Edit: /usr/share/catfish/catfish.py

Find: 

```

parser.set_defaults(icons_large=0, thumbnails=0, time_iso=0, me

```

change the values to the ones you want

path and method are the interesting ones...

save it, then

Edit: /usr/bin/catfish

and change it to

```

#!/usr/bin/env bash

python /usr/share/catfish/catfish.py "$@"

```

I have no idea if the paths are different under xubuntu...

I hope this helps!

Im still changing catfish so its easier to do this.

---

### Post by pseudonym on 2008-12-13
Thanks for that. I knew some file had to be lying around somewhere :)

---

