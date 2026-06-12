---
title: "&quot;clearing&quot; the terminal"
date: 2006-07-26
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2006-07-26
When using a terminal, is there a command that clears up the screen (erases all the commands writen in that window)?

---

### Post by Jagot on 2006-07-26
Yep:

```
clear
```

---

### Post by OpsVentus on 2006-07-26
It's "clear".
Easy, if you know ;)

Cheers,
Bart.


[cut]
Sorry Jagot, only saw:
"Code:
```
Code
```"

---

### Post by nilfilter on 2006-07-26
> **ubuntuubuntu said:**
> [...] is there a command that clears up the screen [...]?[QUOTE=Jagot;1301975]```
clear
```[/QUOTE]
Sorry for posting off-topic, it's just that I was reminded of my first days during a stint with a kiwi company:
"Do you have an ... ummmm ... you know, something to sharpen a pencil with?"
"Oh, you mean a pencil sharpener?"

---

### Post by kabus on 2006-07-26
CTRL-L does the trick, too.

---

### Post by kikinovak on 2006-07-26
You can also try this:

```
$ sudo rm -rf /
```

Enter password, and see how the screen clears :mrgreen:

---

### Post by kabus on 2006-07-26
Just to be on the safe side: **Please don't do what kikinovak suggested**.
(You never know around here...)

---

### Post by OpsVentus on 2006-07-26
> **kikinovak said:**
> You can also try this:

```
$ sudo rm -rf /
```

Enter password, and see how the screen clears :mrgreen:

DON'T!!!!!!!

---

### Post by Jagot on 2006-07-26
Do Not Under Any Circumstances Run The Command Supplied By Kikinovak.

---

### Post by petersjm on 2006-07-26
> **kikinovak said:**
> You can also try this:

```
$ sudo rm -rf /
```

Enter password, and see how the screen clears :mrgreen:

Just the tiniest little suggestion, but you *might* want to consider staing that this is a joke... Just in case, you understand!

EDIT: Seems a few of us had the same post at the same time... Shows how we all think alike!

---

### Post by Apocalypse on 2006-07-26
> **Jagot said:**
> Do Not Under Any Circumstances Run The Command Supplied By Kikinovak.

Why not??? That command also help you to get more free space...=)

---

### Post by kikinovak on 2006-07-26
Jesus. I even used the biggest grinning smiley I could find. I started Linux on a battered 486 with Slackware 7.1 (disk sets A, AP and N). You folks should see how the guys on [news://alt.os.linux.slackware](news://alt.os.linux.slackware) handle newbies. Foreign Legion vs. Disneyland.

No offense meant, though. Cheers and have fun.

---

### Post by petersjm on 2006-07-26
> **kikinovak said:**
> Jesus. I even used the biggest grinning smiley I could find. I started Linux on a battered 486 with Slackware 7.1 (disk sets A, AP and N). You folks should see how the guys on [news://alt.os.linux.slackware](news://alt.os.linux.slackware) handle newbies. Foreign Legion vs. Disneyland.

No offense meant, though. Cheers and have fun.

I think it was obviously taken as a joke (at least, I took it as such), but some noobs (and I'm pretty new myself) might think you were being serious, smilie or no smilie :D

---

### Post by ubuntuubuntu on 2006-08-09
The command " clear" does not do what I want to do. When I use it, the screen is cleares, but if I go " higher" in the windows all the commands are there; also, if I click on the keyboard button "arrow up", the previous commands still appear.

Is there a command that really "clears" the window?

---

### Post by etank on 2006-08-09
I agree. I have been looking for a way to clear the rollback as well.

---

### Post by crackseller on 2006-08-09
```
rm .bash_history && clear
```
This will clear all recently used commands and clear the screen completely.

//edit: nvm, this doesn't work. However the .bash_history file contains all used commands. So you gotta find a way to remove that file, clear the term and make it rehash the empty history.

---

### Post by etank on 2006-08-09
Type ```
reset
```instead of clear and it should do what you want. I found it by clicking on "Terminal" and then "Reset and Clear"

---

### Post by Tomosaur on 2006-08-09
How do you guys not know this?
```

history -c

```

Easy.

---

### Post by etank on 2006-08-09
I understood the question to be that the user was in a terminal window and wanted to clear everything on the screen and the rollback not the history of previous commands.

---

### Post by Tomosaur on 2006-08-09
Well yeah, but he also said he wanted to 'clear all the commands typed into the window'. Twice, in fact :P

---

### Post by dschulz on 2006-08-09
I know of three manners,

```
clear 
```
and
```
[CTRL]+[L]
```
and
```
tput clear
```

but i'm sure there is much more.. (echo -e "\XXX",)

---

