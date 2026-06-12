---
title: "Trouble Creating a Desktop Launcher"
date: 2007-02-28
forum: Desktop Environments
---

### Post by mtpadilla on 2007-02-28
Hello Folks,

Because I use scim to use Japanese, I need to start skype via the following command:

XMODIFIERS=@im=none QT_IM_MODULE=xim skype

I would like to be able to create an icon/launcher on the desktop that will issue this command so that I don't have to always open a terminal to do it. I've tried to create such a launcher via the usual right-click on the desktop -> Create Launcher and have put that command above in the "Command" section of the launcher. However, when I then click on the launcher I get an error with the message:

Details: Failed to execute child process "XMODIFIERS=@im=none" (No such file or directory)

Could anyone please tell me how to create such a desktop launcher? I'm sure it's trivial, but I'm unaware of the solution...Thanks a bunch in advance!!

-MP

---

### Post by haricharan on 2007-02-28
this is just a guess..try it within quotes!

---

### Post by mtpadilla on 2007-02-28
> **haricharan said:**
> this is just a guess..try it within quotes!
Thanks for the idea, but unfortunately that didn't work :(

---

### Post by haricharan on 2007-02-28
maybe you can just create script and put it the commands in it. But that wouldn't work as a launcher...it would ask u everytime to display or run...

---

### Post by mcduck on 2007-02-28
you could create a file called startskype.sh and paste the following code into the file:
```
#!/bin/sh
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
```
Save and make the file executable (from the right-click menu/Properties or with chmod ug+x startskype.sh).

Then point your launcher to that file. It should work. :)

---

### Post by mtpadilla on 2007-02-28
> **mcduck said:**
> you could create a file called startskype.sh and paste the following code into the file:
```
#!/bin/sh
XMODIFIERS=@im=none QT_IM_MODULE=xim skype
```
Save and make the file executable (from the right-click menu/Properties or with chmod ug+x startskype.sh).

Then point your launcher to that file. It should work. :)
That did the trick! Thank you both for your help and comments. :)

Best,
MP

---

