---
title: "command name conventions"
date: 2005-05-26
forum: Desktop Environments
---

### Post by halus on 2005-05-26
Hi

I did an update on my parents computer yesterday, from Warty to Hoary+backports. Everything was ok I thought before going for sleep.

My mother did not want to wake me early this morning, but she made it clear that the email was not working. She thought it had something to do with child restrictions or something like. 

After my sleep I turn on their computer to check wat that was all about. OK, clicking on the Evolution icon on the panel gives this error:

> Details: Failed to execute child process "evolution-2.0" (No such file or directory)

For now my presumption is this: She did not read that message properly, but the mail program did not start and she catched that the problem involved "a child".

(LOL)

The problem is that the panel launcher use an edition number suffix in the command, like evolution-2.0(Warty) and evolution-2.2(Hoary). And the dist-upgrade do not change this suffix properly.

Hope Ubuntu can do this better for later upgrades, maybe with proper panel-launcher upgrading, or, why not drop that suffix? (the command "evolution" works too).


Small things like this is important I think. I guess there are many like my mother, which does not have time or interest to fix easy fixable "small errors". And they want to check their mail before their off to work.

---

### Post by jasmuz on 2005-05-26
[QUOTE=halus]Hi

I did an update on my parents computer yesterday, from Warty to Hoary+backports. Everything was ok I thought before going for sleep.

My mother did not want to wake me early this morning, but she made it clear that the email was not working. She thought it had something to do with child restrictions or something like. 

After my sleep I turn on their computer to check wat that was all about. OK, clicking on the Evolution icon on the panel gives this error:



For now my presumption is this: She did not read that message properly, but the mail program did not start and she catched that the problem involved "a child".

(LOL)

The problem is that the panel launcher use an edition number suffix in the command, like evolution-2.0(Warty) and evolution-2.2(Hoary). And the dist-upgrade do not change this suffix properly.

Hope Ubuntu can do this better for later upgrades, maybe with proper panel-launcher upgrading, or, why not drop that suffix? (the command "evolution" works too).


Small things like this is important I think. I guess there are many like my mother, which does not have time or interest to fix easy fixable "small errors". And they want to check their mail before their off to work.[/QUOTE]
 It's as easy as changing the parameters of the launcher to the new evolution :)

---

