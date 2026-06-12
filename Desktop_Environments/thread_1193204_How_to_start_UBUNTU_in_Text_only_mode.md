---
title: "How to start UBUNTU in Text only mode?"
date: 2009-06-21
forum: Desktop Environments
---

### Post by sanketvaidya on 2009-06-21
Hi all,

I have UBUNTU 8.10 desktop with genome.

I want to make UBUNTU boot in text only mode & switch to GUI only if I require.
How to accomplish that?

In KNOPPIX I used to do that by simply changing runlevel in init script. Then I use to start GUI by typing
startx manager name
eg. startx icewm
How to do that in UBUNTU.?

Also How can we change the default manager. Again in KNOPPIX I used to do simply by changing it from init script. How to do that with UBUNTU?

Kindly provide a step by step.

---

### Post by blackgr on 2009-06-21
Its all about init scripts in Ubuntu too :).  All the init scripts are inside /etc/init.d/ and the ones which start on boot are inside /etc/rc* folders, which are links to the first folder. To register or unregister a script from starting on boot, use update-rc.d command. For example

```
sudo update-rc.d ScriptName defaults
```

this will register the "ScriptName" to start on boot and it must by inside /etc/init.d in the first place. To unregister a script just do

```
sudo update-rc.d -f ScriptName remove
```

So to your problem, just unregister gdm.
```

sudo update-rc.d -f gdm remove

```
and you can register it back whenever you like.

To change manager, just edit 

```
/etc/X11/default-display-manager
```

and register new manager with update-rc.d.
Good luck

---

### Post by Woody1987 on 2009-06-21
I also wanted the same thing to be done. Look at my thread about it:

[http://ubuntuforums.org/showthread.php?t=929115](http://ubuntuforums.org/showthread.php?t=929115)

Essentially run

```
sudo update-rc.d -f gdm remove
```

then reboot and you should have a terminal only, to start gnome run

```
sudo /etc/init.d/gdm start
```

---

### Post by sanketvaidya on 2009-06-22
Both the replies sound good.:)

But Before I try I have few more questions:

1. In the thread provided by Woody1987 to enable gdm script again the command was

sudo update-rc.d gdm defaults 13 01

what is 13 & 01? Do we add the scripts by using 'defaults'? Is there no option like 

sudo update-rc.d gdm add (contrasting to remove) ?

2. Also where are the changes made by update-rc.d command reflected? i.e. which file or script is updated after using this command?

3. I have installed fluxbox using sudo apt-get install? So what I have to do to invoke fluxbox at startup or from text only mode instead of gdm? Which script I have to place in init.d for fluxbox?

Waiting for answers.

---

### Post by dazman19 on 2009-06-22
You should look into using runlevel 3. 

The GUI is ran in runlevel 7. I think there is a way to get your boot loader to start runlevel 3 instead of runlevel 7. 

I usually jump around by pressing <CTRL>+<ALT>+F3 and <CTRL>+<ALT>+F7 to jump back to gnome. but this wont solve your problem of stopping gnome desktop manager to start.

---

### Post by sanketvaidya on 2009-06-22
Hi Woody1987 & [blackgr,]("http://ubuntuforums.org/member.php?u=732179")

I visited the below How To
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

It mentions that:

> To deactivate a script (meaning that it will not be executed at bootup), remove the corresponding symlink from /etc/rc?.d. Do **not** use the **update-rc.d** command for this purpose! It is only used in package installation scripts, and not designed for this kind of runlevel management. 

Both of you or Anyone from the forum Kindly elaborate the above sentence.

Also it would be great if someone answer my questions in reply#4

waiting for your replies.

---

### Post by sanketvaidya on 2009-06-22
Hi,

I have tried what woody1987 & blackgr suggested & its working. Thanks:)

---

