---
title: "&quot;Startmenu&quot; complete gone!"
date: 2005-04-03
forum: Desktop Environments
---

### Post by Vince-E on 2005-04-03
Hello,
Im quite new to linux, and started with Ubuntu. I got some things installed and I must say it comes close to replace my XP install... however I need to find a good replacement for MM Fireworks still... If I can find that I will be completely over... (still have to look at Gimp)....

But ok, that is not my question... 
When I logged in today in Ubuntu, I noticed that my "Startmenu" is completely gone. So no more menu for me on my desktop, Also the bar with the icons of the desktop and trashcan and such is gone. The only thing i have now on my desktop are icons and the background. Nothing more than that... Please help, because this is really frustrating...

I didnt do anything strange (I think) just removed the games through Synaptic the session before.

Thnx!
 Vince

---

### Post by bored2k on 2005-04-03
[QUOTE=Vince-E]Hello,
Im quite new to linux, and started with Ubuntu. I got some things installed and I must say it comes close to replace my XP install... however I need to find a good replacement for MM Fireworks still... If I can find that I will be completely over... (still have to look at Gimp)....

But ok, that is not my question... 
When I logged in today in Ubuntu, I noticed that my "Startmenu" is completely gone. So no more menu for me on my desktop, Also the bar with the icons of the desktop and trashcan and such is gone. The only thing i have now on my desktop are icons and the background. Nothing more than that... Please help, because this is really frustrating...

I didnt do anything strange (I thing) just removed the games through Synaptic the session before.

Thnx!
 Vince[/QUOTE]
 right click on a panel > add to panel > menu bar [custom]

---

### Post by Vince-E on 2005-04-03
bored2k,
ok, like i said, I am new. You are mentioning to click on a panel, but I dont think I even have this on my desktop. With "startmenu" i mean that menu you have in windows, and also the bar that shows all your active programs and the clock and stuff...  Maybe this is called panel in linux... I really dont know...

Like I said before... only icons are visible that I put on my desktop... nothing else..

---

### Post by kassetra on 2005-04-03
[QUOTE=Vince-E]I noticed that my "Startmenu" is completely gone. So no more menu for me on my desktop, Also the bar with the icons of the desktop and trashcan and such is gone. The only thing i have now on my desktop are icons and the background. Nothing more than that... Please help, because this is really frustrating...

I didnt do anything strange (I thing) just removed the games through Synaptic the session before.[/QUOTE]

Ok, both of your panels are gone - top and bottom?  No more bars?

---

### Post by Vince-E on 2005-04-03
[QUOTE=kassetra]Ok, both of your panels are gone - top and bottom?  No more bars?[/QUOTE]
 oke its called panels... At least learned something again (like every other minute I am using Ubuntu)... both panels are gone..  Nothing at the top nor bottom...

---

### Post by kassetra on 2005-04-03
[QUOTE=Vince-E]oke its called panels... At least learned something again (like every other minute I am using Ubuntu)... both panels are gone.. Nothing at the top nor bottom...[/QUOTE]

Try this:
1. Right click on your desktop to bring up a menu.
2. Left click on "Open Terminal"
3. Type in:
 ```
gnome-panel
``` 
and press enter...

4. Tell me if the bars come back up.

---

### Post by bored2k on 2005-04-03
[QUOTE=Vince-E]oke its called panels... At least learned something again (like every other minute I am using Ubuntu)... both panels are gone..  Nothing at the top nor bottom...[/QUOTE]
 Hit alt+F2, write gnome-terminal in it and press enter. In here type gnome-panel. What happens?

---

### Post by Vince-E on 2005-04-03
it says "command not found". I all ready tried this before because I saw something like this on this forum however it  doesnt work. I tried again also as superuser but it didnt make a difference... "command not found"

Thnx for the fast reactions, i am impressed :D

---

### Post by kassetra on 2005-04-03
[QUOTE=Vince-E]it says "command not found". I all ready tried this before because I saw something like this on this forum however it doesnt work. I tried again also as superuser

Thnx for the fast reactions, i am impressed :D[/QUOTE]

Ok... command not found is what I was afraid of.

Can you type in:
```
sudo synaptic
``` 
and press enter (you'll have to enter your password in as well)

Then do a search for gnome-panel - and then tell me if you find it?

---

### Post by bored2k on 2005-04-03
sudo apt-get install gnome-panel [btw, linux is caps sensitive].

---

### Post by Vince-E on 2005-04-03
[QUOTE=kassetra]Ok... command not found is what I was afraid of.

Can you type in:
```
sudo synaptic
``` 
and press enter (you'll have to enter your password in as well)

Then do a search for gnome-panel - and then tell me if you find it?[/QUOTE]
 ok, i found 2 hits, both of them I am installing, because they were not installed according synaptic. Strange, because I know for sure I didnt touch it....
I will let you know what happens... after install

---

### Post by bored2k on 2005-04-03
[QUOTE=Vince-E]ok, i found 2 hits, both of them I am installing, because they were not installed according synaptic. Strange, because I know for sure I didnt touch it....
I will let you know what happens... after install[/QUOTE]
 Kassetra you're like thinking the same I do 2 minutes before LOL..

---

### Post by bored2k on 2005-04-03
Kassetra you're like thinking the same I am 2 minutes before LOL..

---

### Post by kassetra on 2005-04-03
[QUOTE=Vince-E]ok, i found 2 hits, both of them I am installing, because they were not installed according synaptic. Strange, because I know for sure I didnt touch it....
I will let you know what happens... after install[/QUOTE]

Most likely when you installed/uninstalled something, those went along with it - because of dependencies and such...

Once they're re-installed, you should be ok.  :)

---

### Post by kassetra on 2005-04-03
[QUOTE=bored2k]Kassetra you're like thinking the same I am 2 minutes before LOL..[/QUOTE]

I've done this same thing X number of times to myself... so I'm just "right there!"  heh.  :)

---

### Post by Vince-E on 2005-04-03
[QUOTE=bored2k]Kassetra you're like thinking the same I am 2 minutes before LOL..[/QUOTE]
 ok... I installed through synaptic, rebooted and it worked. Both panels are back. Thnx a lot both of you... 

I got this message at this moment I logged in :
[I]The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
Details: Failed to resolve, or extend '!prefs_key=/apps/panel/profiles/default/applets/mixer/prefs;background=none:;orient=up;size=x-small;locked_down=false[/I]

Should I delete?

---

### Post by kassetra on 2005-04-03
> **Vince-E]ok... I installed through synaptic, rebooted and it worked. Both panels are back. Thnx a lot both of you... 

I got this message at this moment I logged in :
[i]The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
Details: Failed to resolve, or extend '!prefs_key=/apps/panel/profiles/default/applets/mixer/prefs said:**
> 

Should I delete?

Yes, and then re-add your mixer applet by right clicking on the top panel and then left clicking on "Add to panel"

---

### Post by Vince-E on 2005-04-03
thnx alot kassetra, everything seems to work normally again...

---

### Post by kassetra on 2005-04-03
[QUOTE=Vince-E]thnx alot kassetra, everything seems to work normally again...[/QUOTE]

Yay!  :)

---

### Post by chantal on 2005-04-26
Thanks Kassetra for the "sudo synaptic" and re-installing "gnome-panel", "gnome-applets" and suchlike. The same thing had happened to me on my old Pentium 133 with 128 RAM. I was about to re-install everything being a Linux Ubuntu Warty newbie myself. I realise now that the panels disappeared when I uninstalled the Evolution Set and especially the Evolution Data Server. I was thinking of installing a smaller E-mail Client like Sylpheed. By the way, for other newbies, don't forget to right-click an Auto-install package such as Abiword version "Rob" and enable "execute" under the permissions tab.

---

