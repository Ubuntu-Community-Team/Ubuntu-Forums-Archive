---
title: "Places menu's nautilus windows"
date: 2005-05-02
forum: Desktop Environments
---

### Post by GoneWacko on 2005-05-02
Hi,

Not too long ago (about 1 week ago now, I think) I decided to install Ubuntu. I was pleasantly surprised; Everything I wanted was on the CD, everything I didn't want, wasn't.
Where my previous linux distro, Debian Sarge, gave me some irritating errors and made it hard (read: impossible) for me to install the nvidia drivers, Ubuntu did it without me having to answer any questions or fix anything.

Great!

There are only a couple of problems/minor issues I'm having, and this is one of them:
The places menu.

I like it. I use it a lot. But when I open something, it pops up a nautilus window which I do not like as much. It has no address bar, it's tiny, every time I open a different directory the window jumps to a different area of the screen and/or resizes itself, and in some cases, a new window is opened entirely. :(

I have my File Management preferences set just the way I like them, but nothing works.
Am I missing something? Can anyone tell me what I could do in order to have the Places menu open windows just like it does when I go to Applications->System Tools->File Browser ? :)

I have intermediate skills with linux, so I'm confused why I can't get something as simple as this fixed :)

Thanks in advance.

---

### Post by Professor X on 2005-05-02
Go to Applications -> System Tools -> Configuration Editor.  Then go to apps -> nautilus -> preferences.  Check 'always_use_browser'.  Now all windows will be browsers.

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=GoneWacko] But when I open something, it pops up a nautilus window which I do not like as much. It has no address bar, it's tiny, every time I open a different directory the window jumps to a different area of the screen and/or resizes itself, and in some cases, a new window is opened entirely.[/QUOTE]

This is called "spatial behavior", and some people love it, others get annoyed. Before you switch back to old behavior, though, give it  a try. It is actually quite logical - but the logic is different. You do not "use the file manager to look at the folder" -- instead, the window you see is the folder. 
Which means: every directory opens in the same place you left it open the last time, you can only have one window showing a given directory at a time, and so on.
 
Address bar is not there (folder can not have address bar, right?) but you can pres Ctrl-L to get address entry field. 

But if you decide it is not for you, go to Preferences->File Management, open "Behavior" tab and select option "ALways open in browser windows" to switch back to the old behavior.

---

### Post by GoneWacko on 2005-05-02
Ahh, how stupid of me to totally miss that checkbox :)

Thanks for the help, both of you :)

---

