---
title: "No save on log out"
date: 2010-04-14
forum: Desktop Environments
---

### Post by felixvah on 2010-04-14
Is it possible to clean the desktop, Documents and etcc.. after log off or the system restart?

I was able to lock down the desktop, but that's not what I need.  I want users to be able to save but will be gone once the computer logoff or restart.  

Please share your knowledge if you have the answer.  Thanks

---

### Post by tom4everitt on 2010-04-14
Assuming you know how to do this with a script, you can add that script to:

/etc/gdm/PostSession/Default

(at least according to [http://ubuntuforums.org/showthread.php?t=147007](http://ubuntuforums.org/showthread.php?t=147007)).


Get back if you need help writing the script.

---

### Post by SnickerSnack on 2010-04-14
> **felixvah said:**
> Is it possible to clean the desktop, Documents and etcc.. after log off or the system restart?

I was able to lock down the desktop, but that's not what I need.  I want users to be able to save but will be gone once the computer logoff or restart.  

Please share your knowledge if you have the answer.  Thanks

What desktop environment are you using?

If you're using xfce, then I think session saving is on by default.  You can change it from one of the gui menus; I just don't remember which one it is.

---

### Post by tom4everitt on 2010-04-14
> **SnickerSnack said:**
> What desktop environment are you using?

If you're using xfce, then I think session saving is on by default.  You can change it from one of the gui menus; I just don't remember which one it is.

You misunderstand the OP. He wants any user created files to be deleted upon logout.

---

### Post by felixvah on 2010-04-14
> **tom4everitt said:**
> You misunderstand the OP. He wants any user created files to be deleted upon logout.
that's right.. I wanted any user created files to be deleted upon logout.  Thanks for the script.. I'm not fimilar with any scrip yet, but I'll check it out.  Thans again..

---

### Post by felixvah on 2010-04-14
> **tom4everitt said:**
> Assuming you know how to do this with a script, you can add that script to:

/etc/gdm/PostSession/Default

(at least according to [http://ubuntuforums.org/showthread.php?t=147007](http://ubuntuforums.org/showthread.php?t=147007)).


Get back if you need help writing the script.
You got me!, I didn't have a clue.  Can you help with the script?

---

### Post by tom4everitt on 2010-04-14
> **felixvah said:**
> You got me!, I didn't have a clue.  Can you help with the script?

Sure. There are tons of ways of doing this obviously, but lets try with the simplest one. 

You need the path of the users home folder / the name of the user. Where I have written <user> below, you need to change this to the actual name of the user. Commands are supposed to be run in a terminal (applications->accessories->terminal)





1. First create a script named cleanup.sh, in, say, /usr/local/bin. Run 
```

sudo gedit /usr/local/bin/cleanup.sh

```
This will bring up a text editor, where you type the script:
```

#!/bin/bash

# Here change <user> to the name of the user account.
rm -rf /home/<user>/*
rm -rf /home/<user>/.*

```
Save it. 




2. Make the script executable. Run
```

sudo chmod 511 /usr/local/bin/cleanup.sh

```



3. Add the script to /etc/gdm/PostSession/Default. Run
```

sudo gedit /etc/gdm/PostSession/Default

```
to bring up the text editor, and add the line
```

/usr/local/bin/cleanup.sh

```
just before the 'exit 0' line. Save.



Now whenever the user logs out, anything in his home folder should be deleted. Try it, and see how it works out. It should work in theory, but its very easy to miss some little detail.

EDIT: I FIXED THE CHMOD COMMAND.

---

### Post by felixvah on 2010-04-14
thanks a lot, I'll try latter and will post the result whether if I miss anything..

---

### Post by mk1w86 on 2010-04-14
You could start a guest session and after the user logs out all files and settings etc. are lost.

To do this click your username at the top right corner of your screen which should bring up a menu (the one you usally use to shutdown or restart your computer) and click Guest Session.

I haven't worked out yet though how you would do this with a normal user login from the login screen.  I know in Windows you can make a user a member of the Guest group and when they logout all files and settings are deleted. :-k

---

### Post by felixvah on 2010-04-15
I followed the instruction and this is what I get after create the cleanup.sh  

Here's my cleanup.sh

#!/bin/bash

# Here change <user> to the name of the user account.
rm -rf /home/public/*
rm -rf /home/public/.*

mcpl@mylabtop:~$ sudo chmod 511
chmod: missing operand after `511'
Try `chmod --help' for more information.

thanks

---

### Post by maddg3241 on 2010-04-15
> **tom4everitt said:**
> Sure. There are tons of ways of doing this obviously, but lets try with the simplest one. 

You need the path of the users home folder / the name of the user. Where I have written <user> below, you need to change this to the actual name of the user. Commands are supposed to be run in a terminal (applications->accessories->terminal)





1. First create a script named cleanup.sh, in, say, /usr/local/bin. Run 
```

sudo gedit /usr/local/bin/cleanup.sh

```
This will bring up a text editor, where you type the script:
```

#!/bin/bash

# Here change <user> to the name of the user account.
rm -rf /home/<user>/*
rm -rf /home/<user>/.*

```
Save it. 




2. Make the script executable. Run
```

sudo chmod 511

```



3. Add the script to /etc/gdm/PostSession/Default. Run
```

sudo gedit /etc/gdm/PostSession/Default

```
to bring up the text editor, and add the line
```

/usr/local/bin/cleanup.sh

```
just before the 'exit 0' line. Save.



Now whenever the user logs out, anything in his home folder should be deleted. Try it, and see how it works out. It should work in theory, but its very easy to miss some little detail.

ya thta looks right to me try that and it should work again (i did not put it because it was there already)

---

### Post by tom4everitt on 2010-04-16
> **felixvah said:**
> I followed the instruction and this is what I get after create the cleanup.sh  

Here's my cleanup.sh

#!/bin/bash

# Here change <user> to the name of the user account.
rm -rf /home/public/*
rm -rf /home/public/.*

mcpl@mylabtop:~$ sudo chmod 511
chmod: missing operand after `511'
Try `chmod --help' for more information.

thanks


Sorry, the chmod command should read:

```

sudo chmod 511 /usr/local/bin/cleanup.sh

```

---

