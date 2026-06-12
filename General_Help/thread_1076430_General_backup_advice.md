---
title: "General backup advice"
date: 2009-02-21
forum: General Help
---

### Post by Twizzle on 2009-02-21
I have a number of scripts that back up my documents, photos and music. I would like them to do so at different times ie documents hourly, photos daily and music weekly.

I have managed to set a crontab to do the hourly backup which works fine but I have a few questions about the others.

As I see it, I can set the system to backup daily with cron BUT I have to day what time. So if I set it at 9am but don't turn the computer on until 10am does that mean that day will not be backed up? The same goes for the weekly option.

I have thought about using System > Preferences > Sessions but that runs at startup and I don't really want the computer busy backing up large folders while I am trying to do things.

In an ideal world I would like it to happen when I power down as I can just walk away knowing that it is backing up and will then turn off. I have tried to play around with runlevels and init.d but with no luck (for some reason my script would not run in rc0.d and I could not work out why!)

I don't use the computer everyday and turn it on at different times so setting it to backup at a set time is not really the best for me!

---

### Post by brian_p on 2009-02-21
> **Twizzle said:**
> 

In an ideal world I would like it to happen when I power down as I can just walk away knowing that it is backing up and will then turn off.

The ideal world is with us:

[http://ubuntuforums.org/showthread.php?p=6234799](http://ubuntuforums.org/showthread.php?p=6234799)

---

### Post by Twizzle on 2009-02-22
Thanks for the link but I have seen that and many threads similar to it and still can not get it to work, so I was hoping to find an alternative (if one exists).

I guess I will have to keep playing around to try and work out what I am doing wrong!

---

### Post by brian_p on 2009-02-22
> **Twizzle said:**
> 

I guess I will have to keep playing around to try and work out what I am doing wrong!

I might be inclined to write a simple script and run it when closing down. Something like this:

```
#!/bin/bash

do something with rsync ; shutdown -h now

```

---

