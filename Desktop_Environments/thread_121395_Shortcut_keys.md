---
title: "Shortcut keys"
date: 2006-01-25
forum: Desktop Environments
---

### Post by ponzio on 2006-01-25
Hi! I have been adding keyboard shortcuts from

System->Preferences->Keyboard Shorcuts 

but I've been having a few problems with it. I like to put the windows key into some use and now I can start my terminal with Win+T and move between workspaces with Win+Arrowkeys, but for some odd reason it won't work with firefox or with my home folder and a few others. For instance Win+F won't start firefox, but Shift+F or Alt+F will start it, but I would like to be able to start to those with the Win-key. My alt/win-key behaviour is that "Hyper is mapped to the Win-keys", and in the keyboard shortcuts program the win key is shown as <Mod4>.

I am sorry if there is a thread about this matter already, I wasn't able to find one with this kind of problem.

---

### Post by endersshadow on 2006-01-25
Metacity unfortunately recognizes the Super_ keys (ironically named, but the proper name for the "Windows key") as standalone keys, meaning that you cannot combine them with another key for a command.

I'd recommend Ctrl+Alt+Letter for your system commands.  Sorry to deliver bad news :-|

---

### Post by Bou on 2006-01-25
[QUOTE=ponzio]now I can start my terminal with Win+T[/QUOTE]

I thought the Win key was not a modifier o_O

---

### Post by endersshadow on 2006-01-25
Fun fact I just discovered: You can use it in xfwm4 :-D

---

### Post by ponzio on 2006-01-25
The problem is that the I can't get firefox opened with the Win+F, but I can open my terminal with Win+T or with some other key. I can also switch workspaces with Win+Arrows or choose a specific workspace with Win+1/2/3/4, but most of the shortcuts don't work with the win-key. I am wondering why is this. Because it would be logical if all of them worked or if all of them didn't work, but this is just plain odd that some of them work and some of them don't.

---

### Post by endersshadow on 2006-01-25
[QUOTE=ponzio]The problem is that the I can't get firefox opened with the Win+F, but I can open my terminal with Win+T or with some other key. I can also switch workspaces with Win+Arrows or choose a specific workspace with Win+1/2/3/4, but most of the shortcuts don't work with the win-key. I am wondering why is this. Because it would be logical if all of them worked or if all of them didn't work, but this is just plain odd that some of them work and some of them don't.[/QUOTE]

What window manager are you using?

---

### Post by ponzio on 2006-01-25
"What window manager are you using?"

Metacity

---

### Post by carlosqueso on 2006-01-25
[QUOTE=endersshadow]Fun fact I just discovered: You can use it in xfwm4 :-D[/QUOTE]


HOW?!?!?  Where are the settings for that....I use xubuntu, and it doesn't do anything for me.

---

### Post by frodon on 2006-01-25
You should give a try to xbindkey, then you will not use metacity to create the keyboard shortcut : [http://www.ubuntuforums.org/showthread.php?t=79560](http://www.ubuntuforums.org/showthread.php?t=79560)

---

### Post by carlosqueso on 2006-01-25
thanks...I'll check that out when I get home....

---

### Post by endersshadow on 2006-01-25
[QUOTE=carlosqueso]HOW?!?!?  Where are the settings for that....I use xubuntu, and it doesn't do anything for me.[/QUOTE]

Run xfce-setting-show, and under Window Manager, go to the keyboard tab :-D

---

### Post by carlosqueso on 2006-01-25
coolness...thanks.

---

### Post by joehill on 2006-02-26
I've gotten the Win key to work in combinations by changing settings in the System -> Preferences -> Keyboard : Layout Options dialogue.  I went into Alt/Win behavior and checked "Hyper is mapped to the Win-keys".

---

