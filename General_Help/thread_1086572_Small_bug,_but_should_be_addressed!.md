---
title: "Small bug, but should be addressed!"
date: 2009-03-04
forum: General Help
---

### Post by HighCommander540 on 2009-03-04
This is a bug that I think should be addressed right away, it is a really big goof up on some programmers part. No offense.

I used this command:
```
sudo uptime >> awesome
```

And it gave me this error

```
-bash: awesome.txt: Permission denied
```

To my knowledge that is never supposed to happen. Sudo is supposed to overwrite every security protocol there is (well at least the permission denied).

Here is proof:

[http://www.allteris.com/zac/impossible-zac.png](http://www.allteris.com/zac/impossible-zac.png)

---

### Post by MadMan2k on 2009-03-04
> **HighCommander540 said:**
> This is a bug that I think should be addressed right away, it is a really big goof up on some programmers part. No offense.
yeah. on your part. the sudo statement ends ant the redirect arrow, so you end up only executing uptime with sudo.

---

### Post by HighCommander540 on 2009-03-04
Ok, well here is my proposal then. IMO this is a bug. If I type that ant sign it should use the sudo command on the whole line.

I am just saying one way or another I enter that as though it was one command so it should run like on command.

---

### Post by Brynster on 2009-03-04
> **HighCommander540 said:**
>  IMO this is a bug. If I type that ant sign it should use the sudo command on the whole line.



So the whole way in which a sudo command works should be changed to suit you?

Or maybe you should learn CLI better to achieve what you need/want to do.

---

### Post by MacUntu on 2009-03-04
sudo sh -c "uptime >> awesome"

or

uptime | sudo tee -a awesome

should work.

Redirection is set up before any command execution by the shell so your sudo won't help. It's not a bug, it's a feature.

---

### Post by forumache on 2009-03-04
And, as some links are labeled "Not work safe", meaning you shouldn't try to click on them at work (for obvious reasons), you should have labeled your link "Beware, Vista in background".

Just kidding... it burnt my eyes :)

---

### Post by Nullack on 2009-03-04
Its not a bug, its a feature that has a depth of wisdom to it that might not be immediately visible :)

---

### Post by HighCommander540 on 2009-03-04
Ok, ok. The n00b has been defeated. So, can you share that bit of wisdom with me? I like to learn and I want to know what is going on with the command that I issued.

Also, yea. I know Vista. Hey, I got to play my games that don't work on Wine somehow. lol.

Oh, and WTF is everyone so god damn hostile on Ubuntu forums? I was making a suggestion gheesh.

---

### Post by Buffalo Soldier on 2009-03-04
> **HighCommander540 said:**
> Ok, ok. The n00b has been defeated. So, can you share that bit of wisdom with me? I like to learn and I want to know what is going on with the command that I issued.

I humbly present to you the collective wisdom of the ubuntu community regarding sudo -> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Technoviking on 2009-03-04
Everyone is harshing my mellow in this thread :).

I would suggest [http://www.commandlinefu.com](http://www.commandlinefu.com) on some great command line examples.

(Moved thread to General Help, since it is not a direct Jaunty issue)

---

### Post by HighCommander540 on 2009-03-04
Hey, thanks to the people that actually helped me instead of just being assholes. Oh, and I will check and absorb both of those links into my knowledge. Ty, for the help and the move!

---

### Post by scaine on 2009-03-04
> **HighCommander540 said:**
> Hey, thanks to the people that actually helped me instead of just being assholes.

You didn't actually ask for help.  You just insulted your way into getting some.

> **HighCommander540 said:**
> This is a bug that I think should be addressed right away, it is a really big goof up on some programmers part. No offense.

No offence.

---

### Post by The Cog on 2009-03-04
I'm a bit late to the party but...

It's not a problem with sudo. Its an issue with the way shells work. A command like:
*program* >> *file*
happens in this order:
1: Open *file* for writing (append)
2: Launch *program* and connect its output to the file write stream
You are of course failing at step 1. sudo never even launches.

---

### Post by emarkay on 2009-03-04
FWIW I have no idea what the OP is talking about...


"awesome.txt"???

Hostility?  No, just not everyone knows what everyone else is assuming, implying or thinking... ;)

---

