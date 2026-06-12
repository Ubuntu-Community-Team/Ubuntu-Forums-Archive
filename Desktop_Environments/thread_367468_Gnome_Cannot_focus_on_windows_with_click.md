---
title: "Gnome: Cannot focus on windows with click"
date: 2007-02-22
forum: Desktop Environments
---

### Post by ksenos on 2007-02-22
For a week or more I been dealing with a very frustrating problem in my gnome environment. When I login everything seems OK, but after a while I can't bring windows in front by clicking in their contents. I have to either click on title bar, on the task bar or use ALT+TAB. 

I ve posted this in another thread, but the people on that one were using beryl. I am not using beryl or anything else of these fancy stuff. And I can't find any solution by googling. Does anyone have an idea of what may be going wrong? Thanks.

---

### Post by ksenos on 2007-02-23
anyone?

---

### Post by mcduck on 2007-02-23
System/Preferences/Windows and there's a setting for 'raise on click' or something like that. (I can't check the exact name as I'm running Beryl now)

---

### Post by ksenos on 2007-02-23
There is an option about raising windows on mouse hover... but that's not what i want. I need the normal/standard function to bring in front a window by simply clicking on it. That's what goes wrong!

---

### Post by ksenos on 2007-02-26
The problem persists! Anyone else having the same problem? Do I really need to wipe all my drive and start a new and fresh install to have it gone? Damn!:frown:

---

### Post by ComplexNumber on 2007-02-26
i wonder if it has anything to do with such settings as auto-raise delay or focus-mode. fire up gconf-editor, go to Edit in the menu, then Find. type in "metacity" (WITHOUT clicking on either of the 2 tickboxes underneath). have a look through the settings there. when you change them, the change takes place automatically so you will be able to test it as you go along.
let me know how you get on.

---

### Post by ksenos on 2007-02-26
Some voodoo happened and the problem is gone for now. It comes and goes and I still haven't found a way to reproduce it. I ll post again if it occurs again, after trying your suggestion. Thanks.

---

### Post by ksenos on 2007-02-26
Problem came back with any apparent reason. I opened gconf-editor and went to /apps/metacity/general. I tried some of the options and here is what I noticed.

raise_on_click=true. 
focus_mode=click
focus_new_windows=smart

if i check the auto_raise and set focus_mode on sloppy on mouse, the expected behavior (raise on mouse hover) works fine. I tried the application_based option but without any noticeable effects. I also changed the focus_new_windows option but again without any effect. :confused:

---

### Post by ComplexNumber on 2007-02-26
it does seem odd, and i've never heard of it before. its almost obviously a metacity problem (or at least, i'm betting with 90% certainty).
you could try this (it won't do any harm, but may solve the problem as it would bring metacity back to its initial state):
-logout and choose failsafe terminal as your session, then log back in. 
-delete the .metacity directory in your home directory
-exit from that to go back to the login screen
-choose gnome as the session and log back in again.

don't worry, it'll just recreate the directory when you login, but in its initial state.

---

### Post by ksenos on 2007-02-26
Tough luck... It won't login without the ~/.metacity directory and the .ms files in ~/.metacity/session.

---

### Post by ComplexNumber on 2007-02-26
> **ksenos said:**
> Tough luck... It won't login without the ~/.metacity directory and the .ms files in ~/.metacity/session.
i doubt it.  when you first install ubuntu and log in, it loads the sessions(you can see it in the splash screen) if they are present. and if there is no directory present (as in the case of a new install), it creates them.

---

### Post by ksenos on 2007-02-27
I agree... but I am telling you the truth. Removing the ~/.metacity directory makes metacity hang when trying to login (while loading gnome it only shows the metacity icon on the gnome splash). I ll create a fake user and copy the ~/.metacity directory to my own to see what happens.

---

### Post by ksenos on 2007-04-21
For a couple of months the problem I described at the beginning of this thread (not being able to focus on windows by clicking inside them) had disappeared without doing anything. But unfortunately, after upgrading to Feisty and after one day of use, this issue re-emerged.

What did I do today? I installed Java6 with netbeans 5.5 and eclipse. I also changed the appearance of wine apps. Nothing else. I don't use the special effects (not compiz nor beryl), and I cannot reproduce the problem. Is there anyone who has any idea what the heck is going on and how to fix this? It is nearly impossible to work like this. Thanks in advance.

---

### Post by ggeldenhuys on 2007-05-03
Finally somebody that is experiencing the same problem as I.  This is driving me nuts!  It never happened in any other versions of Ubuntu. I installed Ubuntu 7.04 over the weekend on two computers and both are giving me this problem.

As a work-around (though very annoying) is to set the Focus and Bring To Front when the mouse hovers over a window.  

I do programming under Ubuntu ever day, and the IDE I use have loads of separate windows and this bug is really driving me up the wall. So much so, I am considering going back to Ubuntu 6.10

I home somebody can come up with a solution.

---

### Post by gh81 on 2007-11-28
I have the same problem, on and off. Sometimes it works, sometimes it doesn't. It doesn't seem to make any difference whether I use compiz or not. The various focus options such as "sloppy" do what they're supposed to, but no matter how I set the "raise on click", it doesn't raise on click! Sometimes it doesn't even focus on click!

I see this thread is quite old, I found it by googling for a solution. Did anyone find the answer?

---

### Post by HueponiK on 2008-06-03
> **gh81 said:**
> I have the same problem, on and off. Sometimes it works, sometimes it doesn't. It doesn't seem to make any difference whether I use compiz or not. The various focus options such as "sloppy" do what they're supposed to, but no matter how I set the "raise on click", it doesn't raise on click! Sometimes it doesn't even focus on click!

I see this thread is quite old, I found it by googling for a solution. Did anyone find the answer?


Hi! 

I've had this problem, it turned out that one of the side buttons (ones for thumb) of my mouse STUCK in pressed position. Try changing your mouse or fixing old one!

---

