---
title: "The dangers of messing with /etc/sudoers?"
date: 2009-05-06
forum: General Help
---

### Post by monsterstack on 2009-05-06
The sudoers file controls which users run what and can be modified to allow certain users to run commands without having to type their passwords. Only trouble is, editing this file can bork your computer, or completely ruin your security settings if you do it wrong!

Ubuntu's help wiki has a detailed howto on modifying the sudoers file [here]("https://help.ubuntu.com/community/Sudoers") [help.ubuntu.com], but if you're too lazy for that and you're desperate to start mashing away aimlessly at the keyboard, at least have some rudimentary advice.

First of all: why do you want to edit this? if your goal is never having to type your password ever, then you need to learn a few things about security. If you want to edit it so that a few trusted commands don't require entering passwords, then editing this file is very much for you.

First of all, [color=red]never edit /etc/sudoers directly[/color]! There is a special application made especially for editing this important file, called visudo. It checks the file for errors before saving anything, and is therefore highly useful. You can start editing by running this command in the terminal,

```
sudo visudo
```

The intended way to edit this file is specifying aliases for certain things and then allowing user specifications that use those aliases. here's an example of a couple of command aliases:

```

# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot
Cmnd_Alias MY_BASH_SCRIPT = /home/bob/myscript.sh

```

As you can see, I've added shutdown commands and some bash script I have that requires the root account to work properly. Command aliases are always labelled "Cmd_Alias", and they can accept multiple commands so long as you separate them with commas.

So how do I make it so I don't need a password for these items? Go to the bottom of the file, below the line that reads "%admin ALL=(ALL) ALL" and add a user specification:

```

# my permissions
bob    ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS:MY_BASH_SCRIPT
```

Now the user bob will never have to type his password if he wants to use the shutdown command, or use his mysterious bash script. Here, the aliases have to separated with colons.

Save the file and just to be sure you haven't ruined everything, double-check that it's safe by running

```
sudo visudo -c
```

Remember to only add things you trust to the sudoers file. For all I know, bob's mystery shell script might well go ahead and reformat his hard disk. Silly bob.


[size=1]**Original post:**
I was looking around here and saw a thread with some chap asking for a way to use sudo for a specific command without having to type his password each time.

It got me thinking about the security aspect of my sudoers file. I edited it a while back to allow me to run "shutdown -h now" and the like without having to type my password. But what are the dangers of doing so, if any? Is there another way of doing this?

Apart from modifying sudoers to allow anyone to run anything as the superuser without ever asking for a password, which is obviously daft, what dangers can I inflict on myself by messing with this file?[/size]

---

### Post by whoop on 2009-05-06
> **monsterstack said:**
> I was looking around here and saw a thread with some chap asking for a way to use sudo for a specific command without having to type his password each time.

It got me thinking about the security aspect of my sudoers file. I edited it a while back to allow me to run "shutdown -h now" and the like without having to type my password. But what are the dangers of doing so, if any? Is there another way of doing this?

Apart from modifying sudoers to allow anyone to run anything as the superuser without ever asking for a password, which is obviously daft, what dangers can I inflict on myself by messing with this file?

Having syntax errors in your sudoers file can render your root account unusable. That's pretty dangerous. So never edit it directly.

---

### Post by monsterstack on 2009-05-06
That's all right. I used visudo and checked it with the -c option afterwards.

But are there any other dangers?

---

### Post by bodhi.zazen on 2009-05-06
use visudo and it will check your syntax.

Second problem would be to add in too many permissions -> security compromise .

Other then those two things not much you can do wrong.

---

### Post by monsterstack on 2009-05-06
Thanks for the info. It's pretty much what I expected, but I have seen some odd things around the net about sudo. If nobody minds I'm going to edit my original post to make it a bit more useful if anybody stumbles here from a google search.

---

### Post by bodhi.zazen on 2009-05-06
> **monsterstack said:**
> Thanks for the info. It's pretty much what I expected, but I have seen some odd things around the net about sudo. If nobody minds I'm going to edit my original post to make it a bit more useful if anybody stumbles here from a google search.

There is a lot of mis-information about ubuntu and sudo on the net.

Always confirm information you read on the net.

---

