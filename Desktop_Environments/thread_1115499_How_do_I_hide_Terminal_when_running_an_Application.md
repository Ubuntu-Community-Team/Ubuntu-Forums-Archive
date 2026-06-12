---
title: "How do I hide Terminal when running an Application in Terminal?"
date: 2009-04-03
forum: Desktop Environments
---

### Post by TheBernok on 2009-04-03
I created a Launcher for an Application in Terminal:

The program runs but I get a window for MATLAB and one for Terminal. How do I do it so that Terminal is hidden?

---

### Post by Giblet5 on 2009-04-03
> **TheBernok said:**
> I created a Launcher for an Application in Terminal:

The program runs but I get a window for MATLAB and one for Terminal. How do I do it so that Terminal is hidden?

What runs when you click the launcher? Provide the command info.

Is MatLab starting the terminal session so that it can log warnings where you'll see them?

---

### Post by TheBernok on 2009-04-04
> **Giblet5 said:**
> What runs when you click the launcher? Provide the command info.
I did this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108651&stc=1&d=1238850619[/IMG]

> **Giblet5 said:**
> Is MatLab starting the terminal session so that it can log warnings where you'll see them?
When I click the launcher, Terminal pops up, and then MATLAB starts. So I end up with two windows, MATLAB and terminal.

If I close Terminal, MATLAB is also terminated. Same if I close MATLAB, terminal is closed.

I want to be able to keep MATLAB open but hide the Terminal window.

---

### Post by roblloyd on 2009-04-04
It sounds like the terminal window is part of matlab. you might just have to live with it. Theres a possibility that you could set up alias and run matlab from the commandline with a program like guake (a termial that drops down from the top of the screen). Then the terminal would still be there but in a window that you cant see unless you press f12 (guake's hotkey).

This is just an idea though, you'd have to check. 

Hope this helps in some way

---

### Post by TheBernok on 2009-04-04
Yeah, meanwhile I'm just keeping the terminal window on a different workspace.

I'll try your suggestion.

---

### Post by zhocchao on 2009-04-04
ok
just curious.
Is it necessary to run your App in terminal?

---

### Post by TheBernok on 2009-04-04
That's what I was curious too. Last time i tried without terminal it didn't load completely. But I installed it in the wrong path.

(I'm new to linux) I'm going to re-install and try again.

---

### Post by roblloyd on 2009-04-04
Hi, I've been meaning to install my University version of MATLAB for a while. Which version is yours? I have R2007B or R2008A. Then I can do a check on my own install. might even be able to work something out for you. Let me know

---

### Post by TheBernok on 2009-04-04
OK. Issue fixed.

I have R2008a but I managed to solve the problem. I missed a few steps in the installation process. 

I followed this guide this time:
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

Thanks for everyone's prompt help.

---

### Post by kancil_biru3 on 2010-01-09
> **TheBernok said:**
> OK. Issue fixed.

I have R2008a but I managed to solve the problem. I missed a few steps in the installation process. 

I followed this guide this time:
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

Thanks for everyone's prompt help.


Could you advice which step that you missed.  I tried twice but still having the terminal issue.  I'd blame my heavy breakfast just now.  ;)

---

