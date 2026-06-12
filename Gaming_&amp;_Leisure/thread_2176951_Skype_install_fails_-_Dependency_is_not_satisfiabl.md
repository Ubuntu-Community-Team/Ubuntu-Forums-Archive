---
title: "Skype install fails - Dependency is not satisfiable: libasound2"
date: 2013-09-26
forum: Gaming &amp; Leisure
---

### Post by Crinkle on 2013-09-26
Can someone tell me how to solve this? Please have an easy to follow guide or step by step instructions because I am new to linux. Unable to find anything on google that means anything.


[B]Solved By:
[/B]
[LIST]
[*][B]alt+f2
[/B]
[*][B]type "xterm" in box and select the icon
[/B]
[*]**in black and white window, type "**sudo apt-get update**" then "**sudo apt-get upgrade[B]"
[/B]
[*][B]let both commands finish, and hit Y to download and install extra files with the "upgrade" procedure.
[/B]
[*][B]Try install skype again!
[/B]
[*]**I think this problem occurred for me as during Linux installation, i did not download updates during install.**
[/LIST]

---

### Post by Bashing-om on 2013-09-26
Crinkle; Hi !
Presently we do not have enough information to make any determination.
So get some info; ubuntu uses a package management system to maintain the stability of the operating system. One way of determining the state of the installed packages is obtained by terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
This code will give indications of any problems within the package management system. 

Post back -between the code ("#") tags- the output of "sudo apt-get update".

[INDENT][INDENT]generalities will lead us to specifics
[/INDENT][/INDENT]

---

### Post by Crinkle on 2013-09-26
Hi there, can you tell me what I do with that code? I've no idea...

---

### Post by Crinkle on 2013-09-26
Ok i used google to learn where to type sudo code, and ran xterm, but both commands it asks me for a password (presumably the one from during installation). When i enter it, nothing appears (no characters or asterisks), but i enter it anyway. It tells me the password, which I know is correct, is wrong. What do i type there?

---

### Post by Crinkle on 2013-09-26
ok got it working again, it took a chatacter off my password for some reason.

sudo apt-update seems to install some stuff. not sure what and theres no way to copy and paste (right click deselects the selection, and CTRL+C does nothing)

"urgrade" lists a lot of stuff, and says "after this operation  21.2MB of disk space will be used", pressing Y seems to make it be downloading or installing lots of stuff.

---

### Post by Bashing-om on 2013-09-26
Crinkle; Sure !

We are going to go to the "Command Line Interface" - CLI - ... not a scary thing at all, just not familiar with it or how to use it . We can help !
One method to get that CLI  from the GUI desk top is to do keycombo "ctl+alt+t" -> that yields the terminal where the commands will be entered.
1st enter into the terminal this command:
```

sudo apt-get update

```
to preclude errors in typing one may copy and paste - commands must be letter, case, space exact.
OK, "sudo" is Super User DO, that gives you temporary administrative privileges. That privilege requires authentication - your pass word. When you enter that pass word will get no response to the screen, security reasons.
Now "apt-get update" syncs your databases with those on the server that maintains all the files for your particular system.
"apt-get upgrade" makes the comparison between your data base files and what resides on that server, and then will attempt to bring all your installed packages up to date with what is available on that server. If that update cannot be done, in this instance, then the package manager will indicate why it was unable to comply.
This is but the 1st step in what could be a long process to find out why "Skype" is problematic to install.
Code tag usage:
Are you familiar with copy paste ?
when you are ready to insert the info into you post, at the top of the post are 3 rows (tool bars) 2nd row, 3rd from right end is "#"; click it and the application will be in your post at the cursor placement, right click and "paste" will place the contents from the clipboard into the post.

[INDENT][INDENT]we can make this happen
[/INDENT][/INDENT]

---

### Post by Crinkle on 2013-09-26
I know how to CTRL+C and CTRL+V on windows, but that doesnt work for xterm. Cant right click on the text either as it deselects everything.

At the moment, "upgrade" is still running, its been running for about 45 minutes so i guess I must have a few things that need fixing!

Edit: uh oh, tried CTRL+C whilst it was doing stuff, it quit out of it. Looks like CTRL+C means "cancel" in Linux!!

---

### Post by Bashing-om on 2013-09-26
Crinkle;
Let's get on a page we both can read.
What version are you running and what is the desk top you have installed ? 
Most 'buntu versions the key combination of Ctl+ALT+t will give you a terminal.
"apt-get upgrade" should have only taken a matter of minutes.
Show me - using the code tags - the outputs of:
```

uname -a
echo $DESKTOP_SESSION
sudo apt-get update

``` 
And next will look at what "upgrade "is not doing.

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by Crinkle on 2013-09-26
Ahh ok, after the upgrade procedure finally finished, I retried skype from the application store, and it appears to have installed OK now!

---

### Post by Bashing-om on 2013-09-26
Crinkle; Outstanding ! You do good work.

Please mark this thread as solved - 1st post, thread tools.
This will aid others seeking a similar solution, and help keep the forum tidy.

[INDENT][INDENT]happy trails to you ->
[/INDENT][/INDENT]

---

