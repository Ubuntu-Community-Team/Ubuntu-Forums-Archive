---
title: "How to disable trackpad while typing on mac with ubuntu"
date: 2011-05-23
forum: Desktop Environments
---

### Post by jcg5230 on 2011-05-23
Hi,

I'm having trouble typing in ubuntu on my macbook because my palms sometimes touch the trackpad while I'm typing.  I've seen a ton of posts about how to disable the trackpad when a USB mouse is connected, but I just want to write a script that I can run to unconditionally disable the trackpad and turn it back on.  I don't care if it requires an extra keystroke or even if I have to write 2 scripts - one to turn it off and another to turn it on.  Can anyone help or at least direct me to somewhere where someone has had this problem solved?

Thanks

---

### Post by sanderd17 on 2011-05-23
[s]The article seems rather old, and I didn't read it, but can you do something with this? [https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)[/s]

If you run 

```

xinput list

```

then you see a list of input hardware, remember the id of the trackpad, mine was 12. Now you can

```

xinput set-prop 12 "Device Enabled" 0

```
to diable it, and
```

xinput set-prop 12 "Device Enabled" 1

```
to enable it

Now you only need something to check if it was enabled or not (so you don't have to use 2 hotkeys). It may be possible via the command

```

xinput watch-props 12

```

but it's difficult to parse. Maybe there is something better.

---

### Post by sanderd17 on 2011-05-23
you could off coarse make your own way to check if it's activated or not with the script:

```

if [ -f ~/.mouse_disabled ]
then
touch ~/.mouse_disabled
xinput set-prop 12 "Device Enabled" 0
else
rm ~/.mouse_disabled
xinput set-prop 12 "Device Enabled" 1
fi

```

save this script and bind it to a hotkey. This should probably do what you want (if 12 is the id of your trackpad).

---

### Post by jcg5230 on 2011-06-07
Thanks.  The script to check whether or not the trackpad was enabled gave a few error messages that I couldn't figure out.  But having 2 seperate scripts isn't a problem at all

JCG

---

