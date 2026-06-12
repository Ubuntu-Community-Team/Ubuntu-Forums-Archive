---
title: "Elements of n00b Success"
date: 2006-07-03
forum: Desktop Environments
---

### Post by artux on 2006-07-03
Strange title when I am a linux n00b myself. 

However as I am going to format my Hard Drive now start a fresh Ubuntu system to recover from the mistakes I've gone through. I need some help and will also give some suggestions to what will contribute to me or any n00b's success.

***Tell me if you agree with me:***

1. Whenever I read advice with written codes.. "sudo ...." I must know exactly what I am typing. Maybe I won't bug the person who is trying to help but will try at least to search and know the commands/programs being used and their attributes. I won't be a typewriter again what will I learn then?

2. I should know "Red Zone" what is safe and what is not safe to try, and what will be the consequences of executing the code. 

3. Most importantly I must know how to UNDO what I just wrote in case it caused problems. Sometimes backing-up configuration files, but most of the time I must know the other side of the "command" implemented to restore what I just did (install Versus Clean?). I rarely find "UNDO" advices anywhere, which is needed at least of the prescribed command didn't work. How can I UNDO most things? Is there any way?

4. I need to know which source of information to trust and which not to trust. As you know there are many sources on the Internet and many ways to either "truly solve" the problem, or "workaround it". How can I know the right trustworthy source?

5. Finally before I ask I will do my best and try reading all the Ubuntu system administration guide. I remember there was one.

I think if those 5 elements are considered, Ubuntu will be re-installed only after 6 months ;) What do you think?

---

### Post by glotz on 2006-07-03
1. Definitely. Echoing random stuff in console is the worst idea.

2. Basically you know you could be in trouble if anything needs root priviledges. (e.g. commands start with sudo or gksudo and thus require password)

3. In a general case there's no undo.

4. This is a very tricky question. There's never certainty. Stuff in help.ubuntu.com can be flawed and downright dangerous. (usually because it was written by imcompetent or careless people possibly for other versions, etc etc)

Patience and humility are key concepts. Required of the helped and the helper. Ask if you're unclear about something. If somebody bothers to help you online, they won't mind. Besides that way you'll get some vague idea of who you're dealing with and if they actually have a clue or are they just others newbies guessing around trying to be helpful.

Also, often trying to fix some issue by yourself can lead to considerably  more complex problems. If in doubt, ask somebody.

A community can be of great use or a source of neverending sorrow... Usually it is both. Handle with care.

---

### Post by Ptero-4 on 2006-07-03
If you follow the advice correctly, you don't even need to reinstall each 6 months at all. All you need to do is to change the names of the repositories in /etc/apt/sources.list with the name of the version you're upgrading to (e.x: if you're on breezy you just change breezy with dapper.) and type:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
the first tells apt (the backend of apt-get, synaptic, adept and aptitude) to download the indexes for the new version packages from it's repositories. And the second upgrades from whatever you're using to the newer version of ubuntu in a smart way resolving intelligently all dependency issues it may encounter in the way, both commands are safe as long as they don't get interrupted mid-way.

---

### Post by aysiu on 2006-07-03
[QUOTE=artux]
1. Whenever I read advice with written codes.. "sudo ...." I must know exactly what I am typing. Maybe I won't bug the person who is trying to help but will try at least to search and know the commands/programs being used and their attributes. I won't be a typewriter again what will I learn then? [/quote] I think it's up to you. If you want to learn what's behind a command, good for you. If you don't, then you don't. When I first started Ubuntu, I just copied and pasted commands because my primary concern was getting things working. It was only later that I tried to understand the commands. Let people work at their own paces.

> 2. I should know "Red Zone" what is safe and what is not safe to try, and what will be the consequences of executing the code. People are fairly good at giving warnings. Other people *heeding* those warnings--that's a different story. I can't tell you how many times I've seen people be told to back up their Windows partitions before installing Ubuntu and them saying, "Yeah, but how can I be sure I don't destroy my Windows data? I really don't want to lose it?" Yes, to be sure--back up.

> 3. Most importantly I must know how to UNDO what I just wrote in case it caused problems. Sometimes backing-up configuration files, but most of the time I must know the other side of the "command" implemented to restore what I just did (install Versus Clean?). I rarely find "UNDO" advices anywhere, which is needed at least of the prescribed command didn't work. How can I UNDO most things? Is there any way? People should ask.

The number one problem, though, is people saying "Oh, just *sudo apt-get install whatever*," and then people saying, "Yeah, how do I remove whatever?" Well, *sudo apt-get remove whatever* doesn't remove the dependencies or the desktop environment you just installed.

Use *aptitude* to install stuff, and you'll be able to remove it later. [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

>  4. I need to know which source of information to trust and which not to trust. As you know there are many sources on the Internet and many ways to either "truly solve" the problem, or "workaround it". How can I know the right trustworthy source? If someone says "Yeah, just paste this command in the terminal," ask what that command does. Or wait until another person posts a response. You'll often hear stuff like, "Yes, so-and-so's advice is good," or "Actually, that may not be the best way to do it because..." Validation is one of the best things about a forum, and it's a very good reason not to ask for support via private message.

---

