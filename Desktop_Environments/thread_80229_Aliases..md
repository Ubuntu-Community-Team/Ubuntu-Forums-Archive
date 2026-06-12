---
title: "Aliases."
date: 2005-10-21
forum: Desktop Environments
---

### Post by Emerzen on 2005-10-21
I'm trying to set up some Bash aliases and have followed the following steps w/ no luck:

-in /home/user/.bashrc -> I uncommented the lines referring to the  if/then ".bash_aliases" file if it exists.

-I then create a file in the /home/user titled .bash_aliases

-I put my aliases in there w/ the following command format
alias x='command'

when I open a terminal and try the alias, I get the "command not found error" even after a relogin/ reboot.  Can someone explain what I've done wrong?

---

### Post by Kyral on 2005-10-21
Can I see your .bashrc and .bash_aliases files? (Just paste'em here)

---

### Post by Emerzen on 2005-10-21
Kyral, I'm at work at won't get to my home computer 'til the morning.  I'll paste them then though.  Thanks!

---

### Post by Emerzen on 2005-10-21
Hey, btw, very much appreciated your guide.  It was there that I got the idea learn aliases too.  Awesome work.

---

### Post by jrib on 2005-10-21
I just set mine up and it seems to have worked.  I did exactly what you did.  Here are some things I thought could go wrong (these are all careless mistakes just check to make sure none of them happened accidentily):

1) did you accidently uncomment the "# Define your own aliases here ..." line
2)typo with the .bash_aliases filename?
3)Try using the alias I made to test whether the problem is a syntax error with the alias...

```
alias letstest='echo hey'
```

4) be sure to have an empty line at the bottom of .bash_aliases (don't know if it is necessary but it is good practice)


After I did all of this no aliases worked of course.  So I did: ```
source .bashrc
```.  Rebooting should have ran the .bashrc anyway in your case but I didn't want to reboot.

---

### Post by Kyral on 2005-10-21
[quote=_jason]I just set mine up and it seems to have worked. I did exactly what you did. Here are some things I thought could go wrong (these are all careless mistakes just check to make sure none of them happened accidentily):

1) did you accidently uncomment the "# Define your own aliases here ..." line
2)typo with the .bash_aliases filename?
3)Try using the alias I made to test whether the problem is a syntax error with the alias...

```
alias letstest='echo hey'
``` 
4) be sure to have an empty line at the bottom of .bash_aliases (don't know if it is necessary but it is good practice)


After I did all of this no aliases worked of course. So I did: ```
source .bashrc
```. Rebooting should have ran the .bashrc anyway in your case but I didn't want to reboot.[/quote]

You don't need to reboot. Just close out your current terminal window and open a new one :D

---

### Post by jrib on 2005-10-21
[QUOTE=Kyral]You don't need to reboot. Just close out your current terminal window and open a new one :D[/QUOTE]

ah thanks for the info

---

### Post by Emerzen on 2005-10-21
Hey guys, I'll give it a go when I get out of work, thanks for all the info.

---

### Post by Emerzen on 2005-10-22
Hey guys, thanks for the info...I got it working.  The test alias you posted worked _jason.  My aliases all needed sudo priveleges...I was leaving the 'sudo' out of the alias and typing it at the command line.  When I included sudo in the alias it worked fine.  Thanks again guys.

---

