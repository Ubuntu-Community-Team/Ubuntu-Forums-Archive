---
title: "Where is .profile?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by nrwilk on 2005-12-05
I'm taking a fundamentals of unix course right now, and one of the things we've learned about is how to change what my teacher calls our "path."  Although I don't think this is the name for it, he is referring to a line within the .profile file, which resides in our home directories.  The line directs the shell at directories to look in for a command to execute when we type it in at the prompt.  the paths in the line are separated with colons (:), and it it ended with a semicolon (;).

Where is this stored in Linux, or ubuntu (if there's a difference)?
Is there a .profile file somewhere other than ~?
Or, is this "path" stored in a different file?

---

### Post by nrwilk on 2005-12-05
You always see these things RIGHT after you post a question about them, huh?

It looks like the equivalent file is .bash_profile, but it's contents are setup differently, and it's missing some stuff.  Am I wrong?  Is there another file somewhere I should be aware of?

I'm used to the .profile setup under HP-UX, and BSD unix.

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=Fealos]I'm taking a fundamentals of unix course right now, and one of the things we've learned about is how to change what my teacher calls our "path."  Although I don't think this is the name for it, he is referring to a line within the .profile file, which resides in our home directories.  The line directs the shell at directories to look in for a command to execute when we type it in at the prompt.  the paths in the line are separated with colons (:), and it it ended with a semicolon (;).

Where is this stored in Linux, or ubuntu (if there's a difference)?
Is there a .profile file somewhere other than ~?
Or, is this "path" stored in a different file?[/QUOTE]

Well, it depends on what shell program you are using.  For example, the default shell installed with Ubuntu is bash.  In bash, there are two startup files: ".bash_profile" and ".bashrc".  Both are located in your home directory (~).  ~/.bash_profile is only run when you start a login shell (basically once when you log in from the console-- not the GUI).  ~/.bashrc is run every time you start a bash shell.

There are other shells like sh, csh, ash, zsh, ksh -- the list goes on.  I think ~/.profile is for sh, the Bourne Shell.  It is one of the first shells, and you find it on just about every UNIX.

Your PATH variable in bash does not end with a semicolon.  It should look something like:
```

PATH=$PATH:/home/tux/usr/bin:/usr/local/games
export PATH

```

---

### Post by nrwilk on 2005-12-05
Right, we use bourne, csh, and ksh is unix class.  Thanks so much for the breakdown between the differences between .bash_profile and .bashrc.  I was wondering where I could edit a file to run a script when opening a GUI shell window.

---

### Post by SickTwist on 2005-12-06
[LinuxCommand.org]("http://www.linuxcommand.org/") is a good resource that gives an introduction to using BASH, doing work via the command line and the basics of scripting. It contains information about the .bash_profile and .bashrc files so you may want to check it out.

---

### Post by nrwilk on 2006-02-14
oh man, I just found this again, and I really feel bad about it, but I forgot to thank you for suggesting linuxcommand.org.  What an excellent site!

My favorite section is the descriptions of all the directories in the root folder.  That was one of the ABSOLUTE most annoying things to me when I started.  I'm still not completely solid on them, but I have a much, much better idea of what each is for now.

Thank you for the link!  Still soakin' up the info.

---

