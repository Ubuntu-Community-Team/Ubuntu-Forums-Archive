---
title: "compiz and dapper and xgl"
date: 2007-02-17
forum: Desktop Environments
---

### Post by dckirba on 2007-02-17
Hello all,

after months of not being able to get a working modem, I finally have one :)

So after catching up on months of missed updates, my sights turned once again to compiz. 

This is what I have - Nvidia geforce mx 4000, Dapper Drake

So since everything I read says Nvidia users stick to XGL, I set up an XGL session. I then decided to use Gandalf's repos for more up-to-date compiz.

Right. I wasn't sure what to install so this is all I added:

compiz-freedesktop, compiz-freedesktop-gnome, and gnome-compiz-manager

and ofcourse all dependencies it said.

Then happily logged into XGL session, found the GL desktop icon in preferences and said 'enable GL desktop'. 'Let there be bling!'

Screen flickered twice and nothing happened. I played around, enabled woobly and all that. Nothing happened.

I am assumin I'll have to edit my xorg.conf file. Is this correct? Is there anything else that I should've installed? 

Thanks for help.

Cheers,
David K

---

### Post by dckirba on 2007-02-17
Hello again,

I have been following instructions from here: [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz")

After the previous post, I realised I hadn't typed 

```
compiz --replace gconf
```

so I did and I got this output and no control of my screen 

```
 compiz: glXBindTexImageEXT is missing
compiz: failed to manage screen 0
compiz: no manageable screen found on display :1.0

```

And I had no window managers so I made the startup script mentioned in the wiki page.

On running the script I got a white screen. I could alt-tab, but all I saw was grey on white.

Now I logged off and logged into gnome, but now gnome isn't giving me window managers.

My XGL session dows give me window managers though. Just that compiz doesn't run.

Any ideas folks?

Thanks,
David K

---

