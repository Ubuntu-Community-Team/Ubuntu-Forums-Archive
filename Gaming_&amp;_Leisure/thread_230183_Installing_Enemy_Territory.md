---
title: "Installing Enemy Territory"
date: 2006-08-05
forum: Gaming &amp; Leisure
---

### Post by Yggdrasill on 2006-08-05
How do I install the .run file of ET?

I'm using Ubuntu 6.06

---

### Post by louis_nichols on 2006-08-05
well... you need to make it executabe, using:

chmod +x *file-name.run*

and then run it using

./*file-name.run*

---

### Post by Yggdrasill on 2006-08-05
I tried what you suggested louis nichols, but I get a message saying "no such file or directory".

---

### Post by FindWaldo on 2006-08-05
Just right click it and go to permissions and make it executable there. Then just double click it and choose run in terminal.

---

### Post by louis_nichols on 2006-08-05
> **Yggdrasill said:**
> I tried what you suggested louis nichols, but I get a message saying "no such file or directory".

well, you have to be in the folder where you saved the file for this to work. the full command would be

chmod +x *path-to-file*

so you either cd to the directory or use the full path. or you just use a graphical tool, like FindWaldo recommends. whichever is easier for you.

---

### Post by Yggdrasill on 2006-08-05
After entering my root password, I get a "authentication failure" message.

---

### Post by FindWaldo on 2006-08-05
Also run the installer out of your home folder. Someone else was having trouble because they tried running it off the desktop, but putting it in the home folder and running it there fixed it. Dont know where you have it though.?

---

### Post by Yggdrasill on 2006-08-05
I was trying to install the progam from Desktop.  I'm still getting the same error message when launching the program from /home.

---

### Post by william_nbg on 2006-08-05
I just installed the program:

sudo sh et?.run

and it worked fine

---

### Post by FindWaldo on 2006-08-05
> **Yggdrasill said:**
> After entering my root password, I get a "authentication failure" message.

You using the correct password right? Try "update manager" or similar with the same password.

---

### Post by Yggdrasill on 2006-08-05
Yup, same password worked for Update Manager.  I have no idea why the game will not install.

---

### Post by FindWaldo on 2006-08-05
Maybe try re-downloading it, i dont know what else.

---

### Post by Yggdrasill on 2006-08-05
re-downloading now. . .

---

### Post by Yggdrasill on 2006-08-06
Just finished downloading the file and it is working.  However, I don't have permission to write to the default install folder.  How can I gain permission?

---

### Post by Iskander on 2006-08-06
Right Click On The .Run File set the perm. where you can execute the file and then go into terminal and type su -, then type cd /home/usr/Desktop, then type ./file-name.run

And Follow up on the instructions

---

### Post by Yggdrasill on 2006-08-06
When I type in my root password, I get an authentication failure message.

---

### Post by Yggdrasill on 2006-08-06
What is a symbolic link?  I set the file to install in /home/yggdrasil/enemy-territory.

---

### Post by Iskander on 2006-08-06
> When I type in my root password, I get an authentication failure message.

Reboot when its gives you that swift option to press escape Hit esc and then choose the 2nd option from the kernel list which is recovery modem and then when you are in the cmd prompt youll be in full root access, then type passwd, and it asks for your new root password and then do the retype, and then when you return to the cmd prompt after that command type reboot. thats one way I can say you might be able to regain root access Besides you getting auth failure I do not know.

---

### Post by K.Mandla on 2006-08-06
If I remember right there's a funny little quirk in that installer. It will accept the installation directory you give it and *make* that directory if it doesn't exist, but it doesn't do the same thing for the symbolic links.

For example, I usually put it in ...

```
/home/kmandla/games/enemy-territory
```
And the installer is fine with that. I like the symbolic links in ...

```
/home/kmandla/games
```
But if the games directory doesn't exist already, I get an error like you describe. I don't know, but maybe that's what you're seeing.

Either way, you might want to make the directories you want to install to before you run the installer. Does that make any sense at all? :confused:

---

### Post by Yggdrasill on 2006-08-06
I got the game to work!  Thanks for all the replies, guys.  I appreciate the help and effort.  How do create a shortcut on my desktop?

---

### Post by FindWaldo on 2006-08-06
Right click on your desktop, choose create launcher
Name it (Enemy Territory)
goto command >browse (go to the file you use to lanch the game and choose it..."ET.sh" but it will probably just say "et" in that window)
Then click OK
Right click your new icon and go properties>click on the icon picture and go back to your ET folder and choose the ET icon.
(You could skip the last step and choose you icon durring making it, but for some reason some icons types dont let me choose them until after Ive created the launcher, IDK?)
Good to here you got it going, now install the TC-Elite mod. Im addicted to it.

---

### Post by Yggdrasill on 2006-08-06
I'll look into the TC-Elite mod.  Is there a linux equivalent of the enhancement pack?

---

