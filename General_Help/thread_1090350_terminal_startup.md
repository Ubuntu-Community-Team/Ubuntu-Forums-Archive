---
title: "terminal startup"
date: 2009-03-08
forum: General Help
---

### Post by hydcozz on 2009-03-08
[INDENT][/INDENT]Hi there,

Firstly, sorry for my english but it's not my main lenguage.

Now the problem, I've got two profiles on gnome terminal, de default and anathour that I create, XPTO.

Evry time a startup the gnome terminal, it'll start on home directory.
What I would like to do is to associate different startup directories for different profiles.

I'm a noob and I've been googling it for a wile, with different search paramters.

Does any one knows if it's possible and how?

Thank you,

[INDENT][/INDENT]hy.d

---

### Post by taurus on 2009-03-08
Well, one way you can do is to create a launcher in the upper panel and in the Comm_a_nd: field, just put it

```
gnome-terminal --working-directory=/what_ever_directory_you_want
```

Of course, there are other ways too.

---

### Post by hydcozz on 2009-03-08
Thanks taurus.

I had tought on that, but unfortunatly it doesn't do it :(

The thing is that it would be helpfull because I have a aplication that uses a terminal embedded on it, and evry time I open the aplication I've to cd what I want.

I wanted to avoid this taking the advantege of profiles.

I've found how to do it but to _all_ profiles, and I just want that on one profile so I use it in that aplication :(

---

### Post by unutbu on 2009-03-08
If your profile is called Default2, you can start a gnome-terminal using Default2 by running
```

gnome-terminal --window-with-profile=Default2
```

---

### Post by Nepherte on 2009-03-08
You could to something like:
```
gnome-terminal --window-with-profile=<ProfileName> --execute="cd <your startup directory>"
```

---

### Post by hydcozz on 2009-03-08
Thaks unutbu and nepherte. I apreciate your help.

But as I alredy tould taurus, I use an aplication that has a terminal embedded on it, and evry time I open that aplication I've to cd what I want.

I would like to avoid use the command cd evry sigle time I open the aplication.

So, commands that open a gnome terminal with arguments do not help :(

---

### Post by lloyd_b on 2009-03-08
What terminal type does that application's terminal report?
```
echo $TERM
```
If this is something other than "xterm", you may be able to trap this value in "~/.bashrc", and have it "cd" to the correct directory for you.

Lloyd B.

---

### Post by hydcozz on 2009-03-08
Thanks for the help Lloyd B..

Unfortunately it's xterm :( . So, this means that it's not possible?! I'll have to use the command always?! :( To bad...

---

### Post by unutbu on 2009-03-08
What application are we dealing with here? 
(Just out of curiosity -- is it a gnome-terminal embedded in the application, or just some terminal?)
What is the output of 

```
env
```

Maybe there is some other environment variable we could use...

---

### Post by kerry_s on 2009-03-08
> **hydcozz said:**
> Thanks for the help Lloyd B..

Unfortunately it's xterm :( . So, this means that it's not possible?! I'll have to use the command always?! :( To bad...

you can script it.

#!/bin/sh

cd /path/to 
xterm -e program

than you only need to launch the script: /path/to/script
use "hold" if it's a program that runs and closes: xterm -hold -e program

---

### Post by lloyd_b on 2009-03-08
> **hydcozz said:**
> Thanks for the help Lloyd B..

Unfortunately it's xterm :( . So, this means that it's not possible?! I'll have to use the command always?! :( To bad...

Take a look at the output of the "env" command when running the application's terminal, versus the results when running gnome terminal.  If there is *anything* that is being set by that application that isn't being set by gnome terminal, it could be used in the fashion I suggested using TERM.

I see another possibility, but it'll be trickier to do - by looking at the PPID (parent process ID) of the current shell, it may be possible to determine if the current shell was spawned by that application or not.

Try the "env" idea first, as it'll be *much* easier to accomplish, provided you have something in the environment to use as a key.

Lloyd B.

---

### Post by hydcozz on 2009-03-08
Firstly, thanks for the feedback.

Secoundly, in case it maybe of same help, the application I'm using is Anjuta and it's terminal plugin.

I've used "env" on the terminals, the difference I see is that the one on Anjuta does not have the line
```
COLORTERM=gnome-terminal
```
What makes sence to me, because the difference in them.

I've notice two variables pointing to the startup path, PWD and HOME. But I don't see anything that looks to be helpfull (maybe thous two?).

The only options available in the Anjuta's configurations for the terminal are
> Use GNOME terminal profile: to select the profile,
and a check item to use the current profile on the terminal (doesn't look very helpfull)

Tanks a lot for the help. I'm very glad for the feedback :)
Hope to find the answer.

---

### Post by hydcozz on 2009-03-08
Sorry kerry_s, I'm a noob.
I didn't understood what you mean.

---

### Post by unutbu on 2009-03-08
Judging from [http://fahadshaon.wordpress.com/2008/02/01/configuring-anjuta-for-nasm/](http://fahadshaon.wordpress.com/2008/02/01/configuring-anjuta-for-nasm/)
it looks like you can Click Settings>Commands and set what command you wish to use to launch terminals.

Can you use something like this to set your default directory?
```

gnome-terminal --working-directory="$(current.file.dir)"
```

---

### Post by hydcozz on 2009-03-09
I don't have de settings on the menu :S .

Only File, Edit, View, Goto and Help.

I've also instaled AutoGen 5 as well, but Anjuta still says I don't have it. I don't know if that the problem :S .

---

### Post by lloyd_b on 2009-03-09
> **hydcozz said:**
> Firstly, thanks for the feedback.

Secoundly, in case it maybe of same help, the application I'm using is Anjuta and it's terminal plugin.

I've used "env" on the terminals, the difference I see is that the one on Anjuta does not have the line
```
COLORTERM=gnome-terminal
```
What makes sence to me, because the difference in them.

Tanks a lot for the help. I'm very glad for the feedback :)
Hope to find the answer.
That should be enough.  Add the following to the end of the file "~/.bashrc":
```
if [ "COLORTERM" != "gnome-terminal" ]; then
    cd /wherever
fi
```substituting the correct directory for "/wherever", and see if that works for you.

Lloyd B.

---

### Post by hydcozz on 2009-03-09
It didn't changed only on Anjuta. :(
It also have changed the terminal it self.

---

