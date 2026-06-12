---
title: "Super_L key opens terminal, in 11.04"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Tony_Harrison on 2011-04-30
Previous to upgrading to Natty Narwhal, I had my left "Windows" key set to open a terminal. I removed the Super_L from the xmodmap with this command:
```
xmodmap -e "remove mod4 = Super_L"
```
Which enabled it as a standalone key. Then, through System->Preferences->Keyboard Shortcuts I assigned the key to Run Terminal.
Anyway, this no longer works since the upgrade. xmodmap shows that the Super_L is not assigned as a modifier key(i.e. it IS a standalone key) and the keyboard shortcut is properly set.
Any ideas why this doesn't work or what changed in 11.04?:icon_frown:

---

### Post by coffeecat on 2011-04-30
The Windows key opens the dash in Natty. I don't believe it's possoble to assign the super key to a shortcut for that reason.

---

### Post by mc4man on 2011-04-30
If you really wanted you could use super+l to open a terminal (current default is Ctrl+Alt+t
You have to set in ccsm > Gnome Compatability > Commands

The super has other bindings that may be reserved for unity, super+l isn't one
The super opens dash on a tap, with super(hold)+ you can use what isn't already taken

If you use keyboard shortcuts for stuff watch out for conflicts, there is no checking atm against compiz binding

---

### Post by Tony_Harrison on 2011-04-30
I have disabled Unity. From what I can tell, now, the Super_L key does nothing. I run in Ubuntu Classic and have enabled several Compiz functions to return the draggable windows and title bars and things like that.

---

### Post by mc4man on 2011-04-30
> **Tony_Harrison said:**
> I have disabled Unity. From what I can tell, now, the Super_L key does nothing. I run in Ubuntu Classic and have enabled several Compiz functions to return the draggable windows and title bars and things like that.
Doesn't matter if logged into Ubuntu or Classic - I'm in Classic right now and changed to super+l, no issue

If you messed around with this setting other than as mentioned things may be a bit borked - simple test
Create a temp new user, log in to it and see if you can change there 
(in ccsm > Gnome Compatibility > Commands

---

### Post by Tony_Harrison on 2011-04-30
Okay, I see the issue now. Thanks for your help mc4man.

I think really what I am asking is, how do I assign super+l as a stand alone key? Previously it was only a matter of removing the value from the xmodmap entry. Now, however, it would seem something else is forcing it as a modifier key.

I realize it may seem petty that I'm too lazy to push a whole extra key to open a term, but it really has become the handiest darn thing. :redface:

---

### Post by Tony_Harrison on 2011-05-03
I believe I have found a solution.

What I did:
open ccsm
Gnome Compatibility->set Open a Terminal key to "Super" 
Commands->set Command 0 to "gnome-terminal"

[INDENT][/INDENT]->set Run Command 0 key to "Super"
open terminal
```
xmodmap -e "clear mod4"
```

This may seem to be drastic and/or excessive to enable this function, but then so are the changes in Natty :mad:

Whatever the case, this has enabled the left Super key to open a terminal with one push. I haven't been able to check if the changes to xmodmap stay after reboot/cron cycles, but I will cross that bridge when/if I come to it and post back.

UPDATE:
I have done a full reboot and waited over an hour. These settings seem static. Success! Thanks everyone for your input!

---

### Post by Tony_Harrison on 2011-05-05
I spoke too soon. :( Inexplicably, this solution ceased to work and I have not been able to reproduce the phenomenon. I restarted a time or two and it continued to work. Then, after a hibernate and awaken it no longer worked. This solution does not work.

Your continued consideration is appreciated.

---

### Post by Krytarik on 2011-05-05
I'm wondering how you actually apply the 'xmodmap' command so that it's run at login?

Usually setting it in "~/.Xmodmap" is the best way, like this (the previous and imo sufficient way):

"~/.Xmodmap":
```
remove mod4 = Super_L
```The next time you log in, you will be asked if you want to use those file, then choose it with "Add" and confirm with "OK".

Then run this command to set specifically Super_L as the shortcut key:
```
gconftool-2 /apps/metacity/global_keybindings/run_command_terminal --type string --set Super_L
```

---

### Post by Tony_Harrison on 2011-05-05
Previously, I had just put the command in my .bashrc file. I followed your recommendation. Really no change. I don't really know gconftool-2, I suspect that it does a similar job that the gconf-editor does? I've set the run_command_terminal value there to Super_L as well in the past. Unfortunately, this does not solve the issue.

I just can't shake the notion that something in Natty is receiving the Super_L key push, forcing it to be a modifier.

---

### Post by Krytarik on 2011-05-06
> **Tony_Harrison said:**
> I don't really know gconftool-2, I suspect that it does a similar job that the gconf-editor does?
Exactly, I just wanted to omit the GUI hassle.

That's indeed weird then!

How about mapping it to another keysym?
Do you need the Menu key?

"~/.Xmodmap":
```
remove mod4 = Super_L
keycode 133 = Menu
```

---

### Post by Tony_Harrison on 2011-05-06
In fact, I use it a great deal for Context Menu in Open(Libre)Office writer.

I think for now, I will just stick with the Super_L+t shortcut for terminal. It is just frustrating when something works before an upgrade and not after. I am open to suggestions about rolling back to 10. Natty just tried to implement too many bells & whistles for its own good.

Thanks for all your suggestions! :)

---

### Post by Tony_Harrison on 2011-05-11
Final Update:

I created the ~/.Xmodmap file containing this:
```
clear mod4
```
I think it might be okay to just remove mod4 = Super_L, but at this point I'm leaving everything as it is because it works.
Completely ignoring ccsm, I opened the Keyboard Shortcuts in System->Preferences. The "Run a Terminal" action does not work anymore (for whatever reason). I created a new, custom action called "term" and set the command to ```
gnome-terminal --working-directory=~
``` Set teh shortcut to Super_L and PRESTO! push the Windows key, get a Terminal.

Thanks again to Krytarik & mc4man for your input! \\:D/

---

### Post by maximus3d on 2011-05-17
Any news on finding the problem with Super_L key? It does not respond even in the "Show Current Layout".

---

### Post by Tony_Harrison on 2011-05-17
> **maximus3d said:**
> Any news on finding the problem with Super_L key? It does not respond even in the "Show Current Layout".

I'm not sure where "Show Current Layout" is. I know that Unity uses the Super_L key for some functionality. Unfortunately, I swore off Unity a few short minutes after installing Natty so I'm not much help there.

As far as this thread is concerned, the real problem (apparently) was with the "Run a Terminal" in Keyboard Shortcuts & xmodmap. What "Problem with Super_L key" are you referring to?

---

