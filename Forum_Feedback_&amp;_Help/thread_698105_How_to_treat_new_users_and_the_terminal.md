---
title: "How to treat new users and the terminal"
date: 2008-02-15
forum: Forum Feedback &amp; Help
---

### Post by PurposeOfReason on 2008-02-15
You just installed Ubuntu for your first time and you're dead excited. You've seen all the videos of compiz and what linux is capable of but something isn't working whether it be your graphics drivers or you didn't have an active internet connection when you installed so you can't get packages for your new OS. For the later, and easy fix is just to type sudo gedit /etc/apt/sources.list and then remove the comments; however that requires the dreaded terminal.

When I help a new users on the absolute beginners talk section, I try to get them to use a terminal first and then a full out GUI method second (in this example it'd be opening up nautilus and going through the file system). As you would expect, most new users prefer the later as it's "friendly". Much slower, but still "friendly". Then they go along in their GUI ways until boom, they mess up something and their stuck in the command line and have no idea what to do. What is nano or vim? Startx? "Help, I'm in a terminal screen and don't know what to do!" usually isn't going to get help because let's be honest, there are many things that could have gone wrong.

I believe that help should be given so that users are at least terminal aware and know a few basic commands. I'm not saying pick on them by saying to sudo rm rf anything, but that does have it's understanding that users should know what they're doing. Linux started with CLI and it shouldn't be cast aside so easily. If someone can tell me that a GUI is **always** more powerful than a CLI and back it up, then we can move on. Until that day, new users should be taught what to do if "the worst" comes or a quicker way to do something.

Your thoughts on this?

---

### Post by LaRoza on 2008-02-15
> **PurposeOfReason said:**
> You just installed Ubuntu for your first time and you're dead excited. You've seen all the videos of compiz and what linux is capable of but something isn't working whether it be your graphics drivers or you didn't have an active internet connection when you installed so you can't get packages for your new OS. For the later, and easy fix is just to type sudo gedit /etc/apt/sources.list and then remove the comments; however that requires the dreaded terminal.

Your thoughts on this?

Press F2 and type "gksudo gedit /etc/apt/sources.list"

Or, go to Synaptic and enable the repositories.

---

### Post by LaRoza on 2008-02-15
> **PurposeOfReason said:**
> 
When I help a new users on the absolute beginners talk section, I try to get them to use a terminal first and then a full out GUI method second (in this example it'd be opening up nautilus and going through the file system). As you would expect, most new users prefer the later as it's "friendly". Much slower, but still "friendly". Then they go along in their GUI ways until boom, they mess up something and their stuck in the command line and have no idea what to do. What is nano or vim? Startx? "Help, I'm in a terminal screen and don't know what to do!" usually isn't going to get help because let's be honest, there are many things that could have gone wrong.

I believe that help should be given so that users are at least terminal aware and know a few basic commands. I'm not saying pick on them by saying to sudo rm rf anything, but that does have it's understanding that users should know what they're doing. Linux started with CLI and it shouldn't be cast aside so easily. If someone can tell me that a GUI is **always** more powerful than a CLI and back it up, then we can move on. Until that day, new users should be taught what to do if "the worst" comes or a quicker way to do something.

Your thoughts on this?

Personally, I dislike doing GUI walk throughs because I usually have to do it myself so I can describe it correctly.

I will do it on some occasions. Although it is too much to expect a new user to know the command line, I do expect them do try their best. Installing operating systems isn't something the average computer user has to do, and a higher level of patience is expected.

This is aggravated when the user isn't using an english setup.

(I once changed my entire system to Arabic to help someone, except I couldn't get out of it. Why? Because it makes everything backwards, including all dialog boxes, and when I clicked "Just for this session", I really clicked "Make Default")

---

### Post by aysiu on 2008-02-15
> **LaRoza said:**
> Press F2 and type "gksudo gedit /etc/apt/sources.list" Why type when you can copy and paste?

---

### Post by LaRoza on 2008-02-15
> **aysiu said:**
> Why type when you can copy and paste?

Because then I have to explain how to copy and paste....

Yes, copying and pasting is prefered, but I usually don't say it because it seems to exclude the possibility of typing it out if they can't figure out how to copy and paste. Anyone who knows how to copy and paste (or highlight and paste) will do it

---

### Post by PurposeOfReason on 2008-02-15
> **LaRoza said:**
> Press F2 and type "gksudo gedit /etc/apt/sources.list"

Or, go to Synaptic and enable the repositories.
Alf F2 is a run box though with is essentially a terminal as far as I'm concerned. Telling them to use synaptic just gets more confusing because then you have to explain what synaptic is. Either way, that was just an example. There are many more (and probably better examples) when a terminal should be used.

---

### Post by LaRoza on 2008-02-16
> **PurposeOfReason said:**
> There are many more (and probably better examples) when a terminal should be used.

Yes:

* Moving large numbers of files
* Deleting large number of files
* Copy...
* Text editing (Vim user here)
* Compiling (non IDE user here)
* Getting information
* Installing software
* Uninstalling software

---

### Post by PurposeOfReason on 2008-02-16
Which is my point. If you started using Ubuntu since about 6.10 (and it was your first distribution), to copy a file you opened nautilus, right click (or ctrl c) and choose copy and then pasted instead of a far more practical cp ~/file /path/to/new/location. Now it is almost a lost art to see any new users even showing interest in doing things this way. They don't know (I don't either because I haven't used a debian based distro in a while) all the aptitude commands for removing packages but instead rely on synaptic. Make clean is forgotten when people use apt-get and it can cause problems later on. While a GUI works, a CLI can get the job done better and cleaner and I believe new users should see this power and realize that this isn't the windows command prompt where it only comes out when something bad happens.

---

### Post by LaRoza on 2008-02-16
Is this a thread you want in the Forum Feedback and Help?

I think the CLI is vastly better than GUI's in most cases, and I use it in Windows often as well.

---

### Post by PurposeOfReason on 2008-02-16
> **LaRoza said:**
> Is this a thread you want in the Forum Feedback and Help?

I think the CLI is vastly better than GUI's in most cases, and I use it in Windows often as well.
I figured it'd go here so for feedback on how to treat new users. Wrong forum?

---

### Post by LaRoza on 2008-02-16
> **PurposeOfReason said:**
> I figured it'd go here so for feedback on how to treat new users. Wrong forum?

No, but you would get more community input in the Cafe. I don't know if you want so many opinions though.

---

### Post by PurposeOfReason on 2008-02-16
> **LaRoza said:**
> No, but you would get more community input in the Cafe. I don't know if you want so many opinions though.
I prefer more opinions if they could be acted upon. But if this couldn't be done, even in some form of a sticky, then it can just die. Thanks either way.

---

