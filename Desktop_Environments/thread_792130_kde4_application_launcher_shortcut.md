---
title: "kde4 application launcher shortcut"
date: 2008-05-12
forum: Desktop Environments
---

### Post by larry_zsh on 2008-05-12
Hi guys, I'd like to assign a shortcut key ( ie the window key  hehe :) ) to the kde4 plasma application launcher. Is it possible to do it?

I noticed that in
"system settings" --> "keyboard and mouse" --> "keyboard shortcuts"

it is possible to add/remove shortcuts to some preselected actions. However it doesn't look like you can add items to it.


cheers
-larry_zsh

---

### Post by Xiong Chiamiov on 2008-05-13
This used to be the default, but was removed in KDE for several reasons.
From [here]("http://www.howtogeek.com/howto/ubuntu/use-the-windows-key-for-the-start-menu-in-ubuntu-linux/"):
> 
To get the windows key to be interpreted as one key, do this:
Make a task that starts with the session (I don't know how you do this in GNOME) by creating a new link to application in your ~/.kde/Autostart directory. Make it so that it runs the following command: xmodmap ~/.xmodmap
Now we need to create a plain text file in your home folder called .xmodmap and make sure it says the following in it:
keycode 115 = F13
keycode 116 = F14

The second line is only needed if your keyboard has two windows keys. Essentially, this maps these keys to the two imaginary keys F13 and F14, so you don't need to worry about the Win + something problem anymore. 115 and 116 are the keycodes that I've seen most, if not all, keyboards give for the winkeys. Check by running xev if it is the same for you. I got this from somewhere else long ago, so don't give the credit to me for it.

Haven't tried it myself, but it sounds right.

---

### Post by larry_zsh on 2008-05-13
Thanks Xiong, it sounds right. xev and xmodmap seem to be handy tools.

The guy you quoted in your post actually posted a follow up:

> 
Sorry for the double-post, but I forgot something. To actually set the shortcut in KDE, open the Control Center, go to Regional & Accessibility and then to Keyboard Shortcuts. The setting is called "Popup Launch Menu". For kubuntu specifically, you have to go to System Settings, then Keyboard and then Keyboard Shortcuts.


This is the bit I can't do... there isn't anything in KDE4 like "Popup Launch Menu" or equivalent entry. 

Thanks for you help so far
-larry_zsh

---

### Post by larry_zsh on 2008-05-14
doesn't have to be the window key, any combination of keys is also good.

cheers
-larry_zsh

---

### Post by Xiong Chiamiov on 2008-05-15
Oh gosh, I booted into KDE4 for a minute to try and see it, and forgot how broken I left it...

Do you get the right windows, with all the options, just there isn't an option for "Popup Launch Menu"?  What about if you press alt+f2 and run kcontrol?

---

### Post by larry_zsh on 2008-05-15
> **Xiong Chiamiov said:**
> 
...
Do you get the right windows, with all the options, just there isn't an option for "Popup Launch Menu"?  What about if you press alt+f2 and run kcontrol?

Yes that is exactly the case : the right window with all the options, but no entry for "Popup Launch Menu"

AFAIK kcontrol is only for ked 3.5 , it won't work with kde4



cheers
larry_zsh

---

### Post by Xiong Chiamiov on 2008-05-17
Hmm, well then, I'm at a loss.  You might be able to find something asking at a more KDE-centric place, since this is rather GNOME-focused.

---

### Post by larry_zsh on 2008-05-17
Thanks anyway Xiong. If I find a solution I will post it on this thread.

---

### Post by alidm on 2009-08-06
Well, I'm not sure what you mean by "plasma application launcher", larry_zsh; though here is the process I followed to assign a global keyboard shortcut (key 'F12') to launch "konsole" (in KDE 4.2.2). Hope it helps you too.
[LIST=1]
[*]Go to "System Settings > Input Actions".
[*]On the left-pane, right-click over a free area, and select "New Global Shortcut > Command/URL"
[*]On the right-pane, in "Trigger" section, choose your desired shortcut.
[*]In "Action", and next to "Command/URL" text area, type the command you usually use in terminal to launch the target application (i.e. application launcher, etc).
[*]Apply the changes you made, and enjoy!
[/LIST]

---

### Post by nossifer on 2009-12-12
> **alidm said:**
> 
[LIST=1]
[*]Go to "System Settings > Input Actions".
[*]On the left-pane, right-click over a free area, and select "New Global Shortcut > Command/URL"
[*]On the right-pane, in "Trigger" section, choose your desired shortcut.
[*]In "Action", and next to "Command/URL" text area, type the command you usually use in terminal to launch the target application (i.e. application launcher, etc).
[*]Apply the changes you made, and enjoy!
[/LIST]

AWESOME.
I wanted META-G to launch googlizer.  Now it does.  Instant google, all the time.  Thanks so much.

---

