---
title: "Tibia On Desktop?"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by Yz85Racer on 2007-10-08
Well hey guys, I've got a little problem. I play a game called Tibia, but I hate having to go into it's directory, pressing f4, typing in ./Tibia.

Is there a way to put the executable on the desktop?

Thanks guys.

---

### Post by AZzKikR on 2007-10-08
You can make a symbolic link to the executable.

---

### Post by Yz85Racer on 2007-10-08
> **AZzKikR said:**
> You can make a symbolic link to the executable.
Generally when someone asks how to do something, you don't say what you'd do, you'd say how you'd do it. Hence the "?".

So, could you tell me how to do that?

---

### Post by AZzKikR on 2007-10-08
> **Yz85Racer said:**
> Generally when someone asks how to do something, you don't say what you'd do, you'd say how you'd do it. Hence the "?".

Right, not entirely true, but I get your point.

You can make a symoblic link by the usage of the **ln** command. Typing ```
man ln
``` provides information about it. Generally, to make a symbolic to a file/directory, you need to type something like ```
ln -s TARGET SOURCE
``` where TARGET is the target file to make the link to, and source is the name of the link. Example: ```
ln -s /home/games/tibia/tibia /home/Desktop/TibiaGame
``` 
This will make a link on the Desktop to /home/games/tibia/tibia, named TibiaGame.

Another possibility is by doing it through Nautilus(if you have Gnome, that is). I can't recall exactly how, but it can be done by a few mouse gestures (shift-drag? or copy it and paste as a link? I really can't remember at this moment, not at my Ubuntu pc, sorry).

Hope this clarifies.

---

### Post by Yz85Racer on 2007-10-08
It worked to a certain extent. But when I click it. Nothing happens.

---

### Post by zero-9376 on 2007-10-08
use the middle click on your mouse (if you have one) and drag the icon for tibia onto the desktop release the middle button and select link here
if you dont have three buttons you may be able to do the same thing by pressing both at the same time

---

### Post by AZzKikR on 2007-10-08
> **Yz85Racer said:**
> It worked to a certain extent. But when I click it. Nothing happens.

Can you open a terminal and execute the symbolic link from there? Perhaps there is some output message which you cannot see otherwise.

---

### Post by Yz85Racer on 2007-10-08
Tibia Error

Cannot find file './Tibia.dat'. (Error Code 1)

Please re-install the program.

---

### Post by AZzKikR on 2007-10-08
Looks like it needs to be executed from the directory where Tibia is put in. I think a viable solution will be to create a simple shell script which changes its directory to the directory where Tibia is installed in, and then executes the Tibia executable. Something along the lines of
```
#!/usr/bin/bash
cd /home/games/Tibia
./Tibia

```
Name this script Tibia.sh or the like, put it in /home/games/Tibia, make it executable by ```
chmod +x /home/games/Tibia/Tibia.sh
``` and then create the symbolic link towards /home/games/Tibia/Tibia.sh.

---

### Post by Tomosaur on 2007-10-08
Ok, backtrack a little here - you shouldn't have to be changing directories all the time to launch programs. Where is the game executable stored? Typically, executables go in /usr/bin - but if you installed the software yourself then it will be wherever you put it.

For clarity's sake - let's assume you installed the binary to /home/me/games/tibia/

Now, the reason you need to change directory right now is because the directory with the binary file isn't in your $PATH (which is an environmental variable which tells the shell to look in these directories when you type a command). What you need to do is add the tibia directory to the path. To do this, open up your .bashrc file (it's a hidden file in your home directory), and add the following lines at the end:

```

#Add tibia directory to PATH
export PATH=$PATH:/home/me/games/tibia/

```(Obviously you should change the directory given above to the actual directory the tibia executable is stored).

Now, close any terminals you have open, then re-open one (this will cause the shell to reload the information in your .bashrc file). Now just type name of the tibia executable and it should load just fine. You can now make a normal desktop launcher and just use the command (ie, the executable name), so you shouldn't have to do any changing of directories.

---

### Post by Yz85Racer on 2007-10-08
Now it says it cannot find the Tibia executable. I have it at /home/kyle/Tibia.

---

### Post by LuisC-SM on 2007-10-09
Hi.
I also have the same problem installing tibia in my daughter's machine.
The problem is that Tibia mus be Executed this way:
```
./Tibia
```
in it's own directory...what I have done (and I do not like it at all) was a kind of what AZzKikR   has posted but I added (by right clicking preferences) a "sh" command to the link in my Desktop, then; again, to execute it I right click and choose execute with "sh" and it is working.
The problem with the PATH variable is that tibia has to be executed  the way mentioned above, other wise ti does not find the "tibia.dat" located in its own directory.
Cheers.

Luis

PS I hope someone can post another trick to run it by just double left clicking

---

### Post by AZzKikR on 2007-10-09
Okay guys, this is really simple. I am going to explain it step by step, how I did it. It took me less than 2 minutes. In my case, I put it into my Applications > Games menu entry.

[LIST=1]
[*]Go to the directory where Tibia is installed in.
[*]Put the attached script in that directory.
[*]Edit that file to make sure it points to the right path. The contents of my run-tibia.sh is the following: ```
#!/bin/bash

cd ~/Tibia/ # my tibia directory is under /home/krpors/Tibia. Edit this line to match it to yours.
./Tibia
```
[*]Make the script executable by: ```
chmod +x run-tibia.sh
```
[*]Go to the menu System > Preferences > Main Menu
[*]Add a new menu entry to the Games menu. Name this something like Tibia. The executable should point to /*tibia install dir*/run-tibia.sh.
[/LIST]

Hope this helps?

---

### Post by AZzKikR on 2007-10-09
If you want it on the desktop by the way, you can right-click on the Desktop and select "Create Launcher...". Let this launcher point to the run-tibia.sh.

---

### Post by LuisC-SM on 2007-10-09
Hi.
Thanks a lot for the reply.

I'll tell you something, I did exactly what you have just posted, except that my file was in this format: /home/salma/Tibia .... and it did NOT work... LOL...
I even made a link to /usr/bin,etc etc etc... nothing worked... I wonder if the "run" word made the difference? mine was Tibia-exec.sh...
HOwever, thanks a lot
Luis

EDIT: I see that my original file started with # /usr/bin/bash instead of #! /bin/bash LOL

---

### Post by fchristophersen on 2008-08-15
thanks a lot! finally it works!!! :)

---

