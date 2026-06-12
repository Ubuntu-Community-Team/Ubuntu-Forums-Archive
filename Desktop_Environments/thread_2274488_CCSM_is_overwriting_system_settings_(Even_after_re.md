---
title: "CCSM is overwriting system settings (Even after removal)"
date: 2015-04-20
forum: Desktop Environments
---

### Post by Misterio7 on 2015-04-20
**Hey everybody, i've spend my whole morning trying to figure this out:**

Well, a few hours ago i installed an application named **CCSM** *(CompizConfig Settings Manager)*.
It just glitched out my desktop, so i tried to uninstall it (Using **sudo apt-get remove compizconfig-settings-manager**) but even after removal i can't change certain settings!
For example, i can't use system settings to enable launcher auto-hide, nor i can use unity tweak tool to change the launcher color.
Any help would be greatly appreciated!

Thanks,

**~[COLOR=#4b0082]Misterio[/COLOR]**

*PS*: It's my first time on this forums, so sorry if i posted in the wrong session.
*PS*[SUP]2[/SUP]: And also english is not my first language, sorry if i mispelled something =P

---

### Post by buzzingrobot on 2015-04-20
Perhaps the configuration files created by CCSM need to be removed.

'apt-get remove ....' does not remove any configuration files created by the package you are removing.  Try adding '--purge', i.e.,'sudo apt-get remove --purge ...'.

Also, CCSM is just a tool that allows users to easily configure compiz, which is a window manager.  Unity is implemented as a plugin to Compiz. So, when you use CCSM, what you are doing is creating config files for compiz. 

Log out and back in afterwards.

---

### Post by Misterio7 on 2015-04-20
Thanks for the reply, i'll try that and let you know if it worked.

**~[COLOR=#4b0082]Misterio[/COLOR]**


EDIT: Nope, the problem still persists. =/

---

### Post by mc4man on 2015-04-20
run this & post file, may show something (generally only settings that aren't at defaults
```
dconf dump /org/compiz/  > setting.txt
```

---

### Post by Misterio7 on 2015-04-21
Here you go: [http://paste.ubuntu.com/10861711/](http://paste.ubuntu.com/10861711/)
Thanks for helping me ^-^

**~[COLOR=#4b0082]Misterio[/COLOR]**[COLOR=#4b0082][/COLOR]

---

### Post by mc4man on 2015-04-21
**Edit:** What release of Ubuntu are you on. If 12.04 then ignore below & post that. If 14.04 or newer then read on, ect.

It could be that you've gone & deleted the unity profile & now are running unity on the Default profile which can cause issues & limitations. 
Your dconf dump only mentions the Default profile when it should show 2 - example (top 3 lines of my dump
> [/]
existing-profiles=['Default', 'unity']
current-profile='unity'
......

If that's the case then it's probably not straightforward to fix. 
To start - 
re-install compizconfig-settings-manager
open it up & go > Preferences > Profile
What is it set on ? If on "Default",   is "unity" available in the dropdown?  **If "unity" is available** then pick it, wait for a bit then close ccsm out. After that open a terminal & run these 2 commands - 
```
dconf reset -f /org/compiz/
```
```
setsid unity
```

If unity is not available as a profile then please post back with that info

---

### Post by Misterio7 on 2015-04-22
Oh, it does make sense, i'll try that and let you know if it works!
Thanks for your help,

PS: Yeah i'm on 14.04

---

### Post by Misterio7 on 2015-04-22
Ok, Default is selected but i don't see any Unity option on the drop-down menu =/.
Actually there is 2 Default options, apparently if i select one or another nothing happens at all.
**~[COLOR=#4b0082]Misterio[/COLOR]**

---

### Post by mc4man on 2015-04-22
Well then it's possible to fix. One way I tested was - 
Open up a terminal, move to side of screen
Open up ccsm > Preferences, move so you can see the terminal. The idea is you need to get to the terminal no matter what.

In the Preferences window click on the green + button to add a profile, type in unity  (that's all  lowercase, see screen). Then close ccsm. 
In the terminal run the 2 commands I previously posted, after that log out/in. (you may want to write down the commands first.

---

