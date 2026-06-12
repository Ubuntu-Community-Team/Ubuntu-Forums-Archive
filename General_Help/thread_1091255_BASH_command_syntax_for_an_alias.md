---
title: "BASH command syntax for an alias"
date: 2009-03-09
forum: General Help
---

### Post by oomingmak on 2009-03-09
I've been struggling for hours now to come up with the correct BASH syntax to achieve the following task:

I'd like to be able to type a word into terminal and have an alias triggered that would sudo su me to another account and at the same time change the colour of the existing terminal prompt (so that I have a visual reminder that I'm temporarily working as another user). The idea is to have a different colour terminal prompt appear for each of my two accounts as I switch between them, and a 3rd colour (red) for when I'm performing a task in the terminal as root.

I've set up an alias to do the sudo su part, and that works fine. I've also set one up an alias that can do the terminal prompt colour change, and that also seems to work. But I can't get the two to work at the same time triggered from the same alias.

I tried using & and && but then either the sudo su part works but the colour does not change at all or (if I swap the commands around) the colour does change but you get this weird number displayed "[1] 31575" above the new prompt.

Also, I'm not sure whether [[COLOR=DarkOrange]**this method**[/COLOR]]("http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/")[COLOR=DarkOrange][COLOR=Black] is the best way to achieve the colour change, as I've noticed strange things happening if I use the 'home' key to try to insert text at the beginning of a line. Instead going to the very beginning of the line, it only jumps back about half way, and no amount of back spacing can get you to the beginning of that line. This problem disappears as soon as you restart the terminal (so that the temporary prompt change is no longer in effect).

I know that there are various ways of achieving this simple task, but I'd rather not be calling separate scripts if possible. I'd rather just have some commands in my alias or bashrc file, so that I know where all my customisations are kept rather than having bits and pieces scattered about.

Any advice on how best to achieve the above would be much appreciated, because despite wading through loads of different online guides, I'm getting nowhere.

[/COLOR][/COLOR]

---

### Post by phinullfermata on 2009-03-09
You could try putting a function in your .bashrc ...  I don't think you would need an alias then, either, but I'm not sure - just a suggestion.

I'm not sure why you would want a script to change the prompt, though.  Couldn't you just change the other account's prompt colour in the .bashrc?

---

### Post by oomingmak on 2009-03-09
> **phinullfermata said:**
> You could try putting a function in your .bashrc ...  I don't think you would need an alias then, either, but I'm not sure - just a suggestion.

I'm not sure why you would want a script to change the prompt, though.  Couldn't you just change the other account's prompt colour in the .bashrc?
Thanks for the suggestion.

I tried it out and it does the trick, although it does mean more separate files to keep track of (the .bashrc from each home folder).

The method that you suggest also allows me to still use an alias to amend the prompt, so that I can retain the colour associated with a particular user account, but can have prompts for different purposes while running as that user. This seems to be the best of both worlds.

Of course, that still does leave me wondering how to execute a sequence of commands from a single alias, but maybe that's for another day.

Thanks.

---

