---
title: "Problem with &quot;apt-get install&quot;"
date: 2006-07-30
forum: Desktop Environments
---

### Post by FooAtari on 2006-07-30
When i ever I try and use apt-get command I get the same error
[I]
sudo apt-get install xxxxxx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xxxxxx[/I]

I must have changed a setting or something?

Any suggestions how to fix?  Thanks

---

### Post by Tomosaur on 2006-07-30
Try the following line:

```

sudo apt-get update
```

This should refresh your package list.

---

### Post by taurus on 2006-07-30
What packages are you having in mind here?  Perhaps you need to use synaptic and search for it!!!

---

### Post by Tomosaur on 2006-07-30
What are you talking about? Synaptic is just a GUI for apt :/


EDIT: Oh I see now. Yeah, if it's the case that you don't actually know the name of the package you want, use synaptic, or you could just try this:

```

apt-cache search xxxx

```

Replacing xxxx with whatever you want to search for.

---

### Post by FooAtari on 2006-07-30
I got the same error while trying to several packages today.

I'll see if that fixed it though...

Thanks

---

