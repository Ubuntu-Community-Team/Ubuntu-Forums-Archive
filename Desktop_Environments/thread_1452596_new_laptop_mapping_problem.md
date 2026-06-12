---
title: "new laptop mapping problem"
date: 2010-04-12
forum: Desktop Environments
---

### Post by mess110 on 2010-04-12
Hi

I just bought a new laptop. Dell Inspiron 1545. I have a problem with its default keyboard mapping.

For instance: to close a program (Alt+F4 normally) I have to press FN+Alt+F4. To rename a file I have to press Fn+F2 instead of just F2. When I press F2 it disables my wireless (as the button indicates).

I read something about xmodmap, but when I would map the keys it wouldn't work for me. Some bad configuration on my side. Sorry.

Now the question is:
How can I reverse this? (maybe reverse the function of Fn)

Thank you in advance.
Kiki

---

### Post by tom4everitt on 2010-04-12
On my macbook I can do the this to change the fn-key behaviour:

```

sudo bash
echo 2 > /sys/module/hid_apple/parameters/fnmode

```

It looks slightly apple-specific though, so i'm not sure it works on any system. I found this on a forum, which looks less apple-specific, but doesn't work on my system:

```

sudo bash
echo 2 > /sys/module/hid/parameters/pb_fnmode

```

---

### Post by mess110 on 2010-04-13
that doesn't work for me either.. any other solutions?

---

