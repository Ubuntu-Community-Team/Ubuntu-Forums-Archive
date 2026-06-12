---
title: "create links in shell?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by tgone on 2006-06-29
Hi,

I'm very new to Linux and Ubuntu...

I want to make a "shortcut" to another folder. I know how to do this in Gnome (right click and select "make link") - but is it possible to do this at the command line?

Thanks,
Tony

---

### Post by taurus on 2006-06-29
```

ln -s <point_to> <point_from>
-or-
man ln

```

---

### Post by tgone on 2006-06-29
that was real easy. thanks.

one thing though - when open the link the location bar says /home/tony/Desktop/www. Shouldn't it be /var/www since that's the actual dir location?

---

### Post by taurus on 2006-06-29
So you want /home/tony/Desktop/www to point to /var/www!
```

ln -s /var/www /home/tony/Desktop/www

```
Now, if you run "ls -la /home/tony/Desktop" from a prompt, you will see it actually points to /var/www.

Is that what you have in mind?

---

### Post by tgone on 2006-06-29
Yep - I get it now. thanks.

---

### Post by taurus on 2006-06-29
[QUOTE=tgone]Yep - I get it now. thanks.[/QUOTE]
Good because there will be a quiz next week!!!  :lol:

---

