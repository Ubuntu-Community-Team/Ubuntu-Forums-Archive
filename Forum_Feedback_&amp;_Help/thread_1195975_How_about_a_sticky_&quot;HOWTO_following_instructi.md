---
title: "How about a sticky &quot;HOWTO: following instructions&quot; thread?"
date: 2009-06-24
forum: Forum Feedback &amp; Help
---

### Post by andrew-sayers on 2009-06-24
Hi guys,

I'm an experienced Linux user with an interest in making life easier for people during their first Linux install.  I'm normally more involved in the developy end of Ubuntu, but one particular issue brought me here.  I hope the following isn't too presumptuous.

**Summary:**

[Criterion 2]("http://ubuntuforums.org/showthread.php?t=677396") for threads in the Tutorials and Tips section is "tutorials should be written to the level of a complete Linux newcomer".  That's a laudable goal, but one that is becoming impractical as Ubuntu becomes more popular.  For example, new Ubuntu users can no longer be assumed to know what a terminal is, let alone how to use one.  People coming straight from Windows expect guides to be in the form "Here's what your computer looks like <screenshot>.  Click such-and-such button.  Here's what your computer should look like now <screenshot>".

Obviously it's impractical to get provide that level of detail for every tutorial, so I'd like to suggest a sticky "HOWTO: following instructions" thread linked from the top of every tutorial, which would expand on the shorthand the tutorials use.  I'd be willing to put time into writing an initial version of the howto, but as I'll explain below, it would need to be a community effort in the long-run.

**Here's my thinking:**

I talked briefly with ubuntu-learning about this.  Ubuntu-learning strikes me as a valuable project for people who are a couple of months in, but not right for people who have half a Sunday left to get their new OS working.  I also tried writing an [interactive tutorial]("http://bazaar.launchpad.net/%7Eandrew-bugs-launchpad-net/+junk/terminal-tutorials/changes"), which turned out to be similarly inappropriate.  Based on my previous failure, I think there are three properties a good solution needs: to be accessible to anyone that ever reads a forum guide, to be modifiable by any forum moderator, and to let readers provide immediate feedback.

If beginners' instructions aren't visible to everyone that reads a guide, then some readers won't think to look for the instructions.  If beginners' instructions aren't editable by forum moderators, then the instructions won't keep up as new guides are produced.  And if beginners can't provide immediate feedback, then writers can only rely on their intuition about what to write.

So if a good solution has to be as readable as a forum thread, as writable as a forum thread, and as commentable as a forum thread, then it seems to me the solution would be a forum thread :)

**Bottom line:**

I'm willing to do put in the time to create an initial version of the howto, and generally getting it going.  But other people will need to change it as time goes by, and explain things in more detail where I've skipped a step.  Is this something you guys would be interested in, and if so, what would you suggest the next step should be?

	- Andrew Sayers

---

### Post by andrew-sayers on 2009-06-24
A slight modification to my original proposal: instead of a normal HOWTO with one post at the top explaining things, and many posts below asking questions, I suggest getting people to post step-by-step guides in replies, and making the top post into an index.

So the first post would read something like:

"
This thread gives step-by-step explanations for things that tutorials often ask you to do.  Tutorials should link to the relevant guides, but here is a list for the curious:

Copying commands into a terminal: <link to post 1>
...
Saving a file into a text editor: <link to post 5>
...
Reversing the polarity on the warp core: <link to post 42>
"

This would let tutorial writers add a comment at the top of their tutorial like:

"
This tutorial requires you to copy commands into a terminal.  For instructions on how to do this, click here: <link to post 1 in the "following instructions" thread>
"

Putting guides in replies would let tutorial writers add guides that are missing, without bothering forum administrators.  It would also allow them to link to the specific tutorial their readers needed, instead of asking readers to wade through loads of irrelevant tutorials before getting to the relevant one.

	- Andrew

---

### Post by Arthur_D on 2009-06-24
I got no power in this forum, but if I had, I would for sure support something like this!
An approach like this would be awesome; there's so many duplicate threads; something like this is almost necessary in my humble opinion. :D

---

### Post by bodhi.zazen on 2009-06-24
I like your suggestions.

Do you know how to IRC ?

I suggest you come to the Beginners Team ;)

We are on freenode at #ubuntu-beginners

---

### Post by andrew-sayers on 2009-06-25
Following a discussion on IRC, here is an example for what the "copying commands into a terminal" guide might look like.  This guide could be referenced from other tutorials by saying *"[open a terminal]("http://ubuntuforums.org/showpost.php?p=7517429") and do: [noparse]```
...
```[/noparse]"* or *"[in a terminal]("http://ubuntuforums.org/showpost.php?p=7517429"), type: **apt-get moo**"*

	- Andrew

[SIZE=5]**Running commands in a terminal**[/SIZE]

Many guides on this forum will ask you to run commands in a terminal.  This guide explains how to run commands in a terminal.

[SIZE=3]**Method 1: With Firefox**[/SIZE]

[Install TerminalRun]("https://addons.mozilla.org/en-US/firefox/addon/9738").  You will need to restart Firefox before you continue.

Once you have installed TerminalRun, you can run commands by selecting them, right-clicking on them, and clicking "Run in Terminal":

[ATTACH]118965[/ATTACH]

*Scroll down to the bottom to try the example command*

[SIZE=3]**Method 2: With Ubuntu, Kubuntu or Xubuntu**[/SIZE]

1. hold down the *Alt* key and press the *F2* key.  A window like this will appear:

[ATTACH]118972[/ATTACH]

2. In the text box, type: **x-terminal-emulator**

3. Click Run:

[ATTACH]118967[/ATTACH]

4. You should see a window like this:

[ATTACH]118970[/ATTACH]

This is a terminal.  Your terminal might have different colours, different fonts, and a different window border.  That doesn't matter so long as the text is the same.

You can type commands in to a terminal, or copy and paste from a guide:

5. Select the text from the tutorial

6. Right click on the text from the tutorial

7. Click "copy"

8. Right click on the terminal

9. Click the middle mouse button to paste

Ubuntu and Kubuntu users can also paste with ctrl-shift-v, or by right-clicking and clicking "paste"

10. The program will run.  Depending on the command, you might need to wait a few minutes, and might need to type in a password.  You can tell the program has finished when the last line of text looks like this:

[ATTACH]118971[/ATTACH]

11. Close the window

Scroll down to the bottom to try these steps on an example command

[SIZE=3]**Method 3: With another desktop or distribution**[/SIZE]

All Linux distributions have a terminal emulator available, usually through the menu system.  If you have installed a different distribution (like Fedora), or a different window manager (like Fluxbox), then you will need to find the terminal yourself.  If you're not sure, don't worry - you would know if you had installed one of these.

Once you have found the terminal, follow the Ubuntu/Kubuntu/Xubuntu instructions, starting at step 5.

[SIZE=3]**Example command**[/SIZE]

This is an example terminal command.  It will print "you have run a terminal command".  Select the text in the **code** block, and follow the instructions above:

```

echo You have run a terminal command

```If your terminal prints "You have run a terminal command", then you have successfully finished this tutorial.

---

### Post by andrew-sayers on 2009-06-25
In case people read here and not in the cafe, I thought I'd mention that I've [put up a poll]("http://ubuntuforums.org/showthread.php?t=1197074") about whether this is a good approach, and asked what other basic guides would be useful.

I'd quite like to move discussion about *whether* to do this, and *what* to do, over there.  I'd also like to keep discussion about *how* to implement it here.  That should make things a bit easier to follow.

	- Andrew

---

### Post by bodhi.zazen on 2009-06-25
While I applaud your efforts IMO this material is easier to organize on the wiki. Have you contacted the wiki team ?

What happened to opening a terminal from the menu ? It may be easier then installing a firefox extension.

---

