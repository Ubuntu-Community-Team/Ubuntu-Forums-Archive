---
title: "Simple Xubuntu Question"
date: 2006-05-30
forum: Desktop Environments
---

### Post by dirtvoyles on 2006-05-30
I seem to have "lost" my XFCE menu. It does not point to the correct file, just a blank one. At this point I cannot access even CLI (unless I use Failsafe). 

Can anyone tell me the default path so that I can edit where the button looks?

---

### Post by aysiu on 2006-05-30
What do you mean you can't even access CLI...? That seems far more problematic than having a blank menu in Xubuntu.

What happens when you press Control-Alt-F1?

By the way, the default menu is /etc/xdg/xfce4/desktop/menu.xml

---

### Post by douga on 2006-05-30
[QUOTE=dirtvoyles]I seem to have "lost" my XFCE menu. It does not point to the correct file, just a blank one[/QUOTE]

If you remove the menu from the panel, then replace it, does it still have no entries? If that's the case, I would suspect a corrupt file.

Or were you referring to the desktop menu?

---

### Post by dirtvoyles on 2006-05-30
I should have chosen my explanation more carefully.

I had chosen "Edit Menu" while I was poking around and my session froze. At that point I rebooted. Apparently the path changed to my customized version which I hadn't customized. THAT is why I couldn't get the menu to open. 

I did put the default path in as you listed it and it worked fine.

The CLI shortcut worked, I'm just not knowledgeable enough to have it memorized. I apologize for the waste of time/mis-wording, and thank you very much for your assistance.

---

### Post by Game_Ender on 2006-05-30
I had the same thing happen to me a few minutes ago.  It turns out all the settings files in the ~/.config/xfce4/ directory were deleted when I clicked "Settings->Menu Editor" for the first time.  I got them back by adding the command line bar to the panel, and then opening an xterm.  I then copied all the files in /etc/xdg/xfce4/ to my ~/.config/xfce4 directory from the command line.  Then everything worked.  Trying to edit the menu again does not do this.  This is a very odd bug, and you have to be kind of resourceful to recover from it.

---

### Post by oyvindaa on 2006-06-01
[QUOTE=Game_Ender]I had the same thing happen to me a few minutes ago.  It turns out all the settings files in the ~/.config/xfce4/ directory were deleted when I clicked "Settings->Menu Editor" for the first time.  I got them back by adding the command line bar to the panel, and then opening an xterm.  I then copied all the files in /etc/xdg/xfce4/ to my ~/.config/xfce4 directory from the command line.  Then everything worked.  Trying to edit the menu again does not do this.  This is a very odd bug, and you have to be kind of resourceful to recover from it.[/QUOTE]

I'm having the same problem. Tried what you said, but it didn't work. 


EDIT: Nevermind, sorted. Thanks!

---

### Post by dsmalley on 2006-06-01
Actually, it seems rather worse than that. I've found that while copying the contents of /etc/xdg/xfce4 restores the default menus, any attempt to use the menu editor to actually edit the menus puts you pack in the same position, with no menus defined at all. So customization through the GUI appears to be completely broken.

Of course the files are pretty straight-forward XML, so hand editing can be done, I guess.

Dave

---

### Post by Neobuntu on 2006-06-01
I'm having the exact same problem on a laptop but not desktop for some reason (different upgrade perhaps). 

Is this bug reported?

---

### Post by Sukarn on 2006-06-02
[QUOTE=Game_Ender]I had the same thing happen to me a few minutes ago.  It turns out all the settings files in the ~/.config/xfce4/ directory were deleted when I clicked "Settings->Menu Editor" for the first time.  I got them back by adding the command line bar to the panel, and then opening an xterm.  I then copied all the files in /etc/xdg/xfce4/ to my ~/.config/xfce4 directory from the command line.  Then everything worked.  Trying to edit the menu again does not do this.  This is a very odd bug, and you have to be kind of resourceful to recover from it.[/QUOTE]
I did what you said, and it fixed my menu.
I had a blank menu as well, and well, now I have my good old menu back.

---

### Post by Neobuntu on 2006-06-02
I fixed mine by adding that command window to the task bar(right click it).

Then typing in it:

gksudo nautilus (with super powers. BE CAREFUL!)

...and moving (right click and copy) the "desktop" folder from...

 /etc/xdg/xfxce4 

...and pasted it into

/home/<YOU!>/.config/xfce4

...and letting it overwrite. Then restart.

Of course "<YOU>" above is you. Your directory name.

Oh and I dared it to vanish again by selecting the menu editor and it stayed. (You have to dare it real good I guess) :)

---

### Post by captainpotato on 2006-06-03
FWIW, I can also confirm that I have this bug. I've just installed Xubuntu 6.06, and about ten minutes after booting, my menu disappeared. I only noticed it after adding an item to the panel, so perhaps it's due to that? Mind you, maybe it happened earlier and I didn't notice.

---

### Post by mikketeve on 2006-06-03
I second that bug too. After opening Menu Editor for the first time, my menu disappeared. Oddly, when looking closely I noticed that when right-clicking or pressing the menu-button a tiny, 4x4 pixel square appeared, like an empty menu?

Deleting config files did not work. Oddly, this fixed it: Right-clicking menu button > properties > uncheck "show icons in menu". Then, magically, the menu reappeared. Check "show icons..." again, and all is well. Weird, huh?

---

### Post by johnnymac on 2006-06-04
I'm having same issues....I figured it out before I read this thread; however, I still can not edit my menu through the GUI.  I get the menu editor open but when I chose to edit an entry the GUI crashes - but the menu stays.

Ahhhhhhh

---

### Post by captainpotato on 2006-06-04
[QUOTE=mikketeve]I second that bug too. After opening Menu Editor for the first time, my menu disappeared. Oddly, when looking closely I noticed that when right-clicking or pressing the menu-button a tiny, 4x4 pixel square appeared, like an empty menu?

Deleting config files did not work. Oddly, this fixed it: Right-clicking menu button > properties > uncheck "show icons in menu". Then, magically, the menu reappeared. Check "show icons..." again, and all is well. Weird, huh?[/QUOTE]

Wow, thanks mikketeve - that's fixed it for me as well. That's really odd - hopefully it won't happen again, as I'm preparing this machine for my mother, and she won't cope with that :P

---

### Post by captainpotato on 2006-06-04
Having said that it worked, now that I'm setting up an account for my mother to use, it's broken again, and the previously suggested solution doesn't fix it. Bugger :P

*edit* to get it back, I did the following:

1. Changed the default menu file to /etc/xdg/xfce4/desktop/menu.xml
2. cp /etc/xdg/xfce4/desktop/menu.xml /home/user/.config/xfce4/desktop/menu.xml (using the shell)
3. Reverted back to the file /home/user/.config/xfce4/desktop/menu.xml

Editing the menu now seems to work.

---

### Post by uhu_maotouying on 2006-06-06
I like xfce4 very much, because I have got a machine ( IBM TP600x ) with scarce resources only. However, several days after updating Breezy to Dapper both installed xfce4-panels ( 1 & 2 ) were gone. Although the terminal command "xfce4-panel" produced a new panel with a single launcher, this poor thing disappeared when I closed the terminal :-(

I have an unconventional temporary fix for you : I created a new user called "fix" and logged on to xfce4. Then I copied the two directories /home/fix/.config/xfce4 & /home/fix/.config/xfce4-session to my home directory /home/myname/.config/ . Then I changed the owner of the two copied directories, including their children from "fix" to "myname" using chown -R myname /home/myname/.config  

Bingo. 

Because I am warned, I made a copy of the new /home/myname/.config/xfce4 & /home/myname/.config/xfce4-session :-)

Now lets be thankful and hope that the nice guys from [www.xfce.org](www.xfce.org) can fix the hiccup.

---

### Post by mikketeve on 2006-06-06
I found that this is in fact a "known issue" (see [xubuntu release notes]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes") - there's a recommended fix, too). GUI menu-configuration is broken. Seems the bug is because xubuntu is using a beta version of xfce 4.4, so they should issue an update for this when the xfce people fix it.

---

### Post by woot on 2006-06-21
[QUOTE=Neobuntu]I fixed mine by adding that command window to the task bar(right click it).

Then typing in it:

gksudo nautilus (with super powers. BE CAREFUL!)

...and moving (right click and copy) the "desktop" folder from...

 /etc/xdg/xfxce4 

...and pasted it into

/home/<YOU!>/.config/xfce4

...and letting it overwrite. Then restart.

Of course "<YOU>" above is you. Your directory name.

Oh and I dared it to vanish again by selecting the menu editor and it stayed. (You have to dare it real good I guess) :)[/QUOTE]

it seems to be a common problem, the above can simply be done with the following command: 
```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

it does exact the same, and you dont need root nautilus...you just read from root-owned files and write in your home, watch out with root nautilus!

(i just replied for the completeness...thought id help some people who stumble upon this)

---

### Post by barb3tta on 2007-08-27
Hi all,
I have the same problem in Xubuntu 7.10 Tribe 3.
copying the default menu.xml to my config dir doesn't solve the problem.
If I try to add a new xfce-menu panel item, the property window appears for a second and then disappears.
Menu button dieappeared the first time i logged in xubuntu.
I did a dist-upgrade, but nothing changed.
don't know how to solve it, 'cause I don't see any log.

Can you help me?
Thanks in advance!

---

