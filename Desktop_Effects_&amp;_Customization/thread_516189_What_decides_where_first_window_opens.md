---
title: "What decides where first window opens?"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by chrisstankevitz on 2007-08-02
When I open a terminal with an empty workspace, it appears somewhere on my workspace.  Open a few more and they tile nicely on my workspace.

Question: What decides where the first window opens?

I would like it to open in the upper-left corner, but it opens offset from upper left.  As a result, I cannot squeeze as many terminal windows in as I would like.

Thank you,

Chris

---

### Post by Kent84 on 2007-08-02
I think it is the composite manager that determines this. The behavior can be changed in the beryl settings under Window Management -> Place windows. You are then given the choice of Cascade, Centered, Random or Intelligent. I hope this is correct.

---

### Post by chrisstankevitz on 2007-08-02
Hello,

Thank you for your reply.  Where can I find "beryl settings under Window Management -> Place windows"?  I am running gnome and could not locate an entry by this name under System | Preferences.

Thank you,

Chris

---

### Post by airtonix on 2007-08-02
The chap is refferring to the use of Beryl.

which it seems you dont have installed? if you doo you would have noticed either : wobbly windows when being dragged or drop shadows beneath windows.

i assume you dont so : 

waht you want is devilspie.
it will allow you to control how a program opens up, on which desktop, at what pixel co-ord, etc etc.

read this thread for how to use devils pie to automate the controll of your windows 
> [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

ps: beryl wont give you the amount of control that devils pie will...it might come close ....but it really needs to be a part of beryl. in my opinion.

---

### Post by chrisstankevitz on 2007-08-02
Hello,

Thank you for your reply.  I do not have Beryl or DevilsPie installed.

Question: What decides where windows open on my non-Beryl, non-DevilsPie system?

Thank you,

Chris

---

### Post by coolen on 2007-08-02
What desktop are you using? I'm assuming KDE, but there are many different options out there.
We need to know more to help you out. Each window manager has its own way to tweak things.

---

### Post by chrisstankevitz on 2007-08-03
Hello, thanks for your reply.

I made a typo in my previous post which ash been fixed.  I am using gnome in the default Feisty install.

Thank you,

Chris

---

### Post by coolen on 2007-08-03
> **chrisstankevitz said:**
> Hello, thanks for your reply.

I made a typo in my previous post which ash been fixed.  I am using gnome in the default Feisty install.

Thank you,

Chris

Okay, good.
I now have to tell you that there is no easy, native way to do this in Gnome.
Wondeful though I think the Gnome desktop is, the developers feel that the one most celebrated strength of Linux (configurability) is not really for them. Try finding your screensaver preferences, and you'll see what I mean.
You can use gconf-editor for many things. This is kind of like the registry under Windows. It looks like the most relevant options for you cannot be edited there, though, and there seems to be no corresponding directory under ~/.gconf
Other window managers are available, which may be more easily configured. Apart from the obvious Compiz and Beryl, it should be fairly easy to install a more established window manager. As I mentioned, there are many to choose from, and most respect our need to personalise.

---

### Post by hardKNOXbz on 2007-08-03
> **chrisstankevitz said:**
> Hello,

Thank you for your reply.  I do not have Beryl or DevilsPie installed.

Question: What decides where windows open on my non-Beryl, non-DevilsPie system?

Thank you,

Chris

compiz?

---

### Post by coolen on 2007-08-03
No Compiz. He'd be using Metacity.

---

