---
title: "migration of evolution to another machine"
date: 2005-07-30
forum: Desktop Environments
---

### Post by vinthund on 2005-07-30
hello,

I am migrating to another machine and wonder what is a proper way to move my evolution settings  and possibly mail from the old one. I think I can just copy .evolution directory, but maybe there is a more "correct" way to do it?

regards,

MV

---

### Post by jasmuz on 2005-07-30
Its true, you would only have to copy your .evolution directory in your home dir and place it in the other machine.

---

### Post by manicka on 2005-07-30
[QUOTE=vinthund]hello,

I am migrating to another machine and wonder what is a proper way to move my evolution settings  and possibly mail from the old one. I think I can just copy .evolution directory, but maybe there is a more "correct" way to do it?

regards,

MV[/QUOTE]
 Picked this up ages ago on another forum.

> Back up (tar.gz) your evolution folder in ~/.gconf/apps. Back up (tar.gz) your .evolution folder in ~/.

Before you restore the backups, run Evolution once on the new load. Set up a default email account...doesn't matter what, we will overwrite it anyway. For some reason this is an important step. Then exit Evolution, and restore the backups. Don't run Evolution again without rebooting. The Evolution data server will then load the desired data. When you run Evolution everything should be as you backed it up.

If for some reason you have issues, just restore the data, and reboot before running Evolution again. I've moved Evolution 2.0.x data a dozen times with this method; haven't had 2.2.x yet, but the process should be the same.

---

