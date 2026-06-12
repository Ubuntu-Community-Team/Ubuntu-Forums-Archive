---
title: "shut-down timer?"
date: 2009-05-28
forum: General Help
---

### Post by zachthejones on 2009-05-28
I would like to have a way to set my computer to shutdown after about two or three hours (like if I'm running and update or installation and want it to be turned off shortly after its done).

Is there a program that can do this? Or will a script or something like that suffice? Maybe a terminal command?

---

### Post by JohnB-nbr on 2009-05-28
You can use the command "sudo shutdown -h  time", e.g. "sudo shutdown -h 13:05"

---

### Post by clonne4crw on 2009-05-28
> **zachthejones said:**
> I would like to have a way to set my computer to shutdown after about two or three hours (like if I'm running and update or installation and want it to be turned off shortly after its done).

Is there a program that can do this? Or will a script or something like that suffice? Maybe a terminal command?

copy this code into a text file, and give it a name (name).sh
```

#! /bin/sh
sleep 10800
#        ^^3 hours =--modify if needed
shutdown now
#EOF

```
then chmod it:

chmod 755 (filename).sh

then run it (as root)
# /path/to/file/(filename).sh

All done!

---

### Post by clonne4crw on 2009-05-28
> **JohnB-nbr said:**
> You can use the command "sudo shutdown -h  time", e.g. "sudo shutdown -h 13:05"
That works, too.

---

### Post by zachthejones on 2009-05-29
clonne4crw - thanks! but it didn't work...at least that I could tell.
Maybe you can tell me where I went wrong.

First I copied this into a text file:
```
#! /bin/sh
sleep 10800
#        ^^3 hours =--modify if needed
shutdown now
#EOF
```

Then I saved it as "later.sh" in my root folder, so when I opened a terminal to run it, I'd be right where the file was located...

Then I ran this command in terminal (in the folder where the file was located)
```
chmod 755 later.sh
```

Then I tried to run it to see if it would work, using this command:
```
sudo later.sh
```

I've never really worked with scripts or anything like that before, so I'm not really clear on what I'm doing...guess I need to do a little bit more research online...

---

### Post by SuperSonic4 on 2009-05-29
You need to run ```
sudo sh later.sh
```. Because you prefaced the command with sudo the sh is no longer implied as it is before so it must be put in

---

