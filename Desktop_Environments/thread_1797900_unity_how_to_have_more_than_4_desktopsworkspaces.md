---
title: "unity: how to have more than 4 desktops/workspaces?"
date: 2011-07-05
forum: Desktop Environments
---

### Post by nevbear666 on 2011-07-05
hi fellow ubuntu users.

the topic really says it all, i was used to my 8 desktops on gnome, but i cannot find the setting in unity...

any help is greatly appreciated.
thx in advance
nb666

---

### Post by Rasa1111 on 2011-07-05
open gconf-editor.

(alt+F2) type in gconf-editor, and open it.

Click Apps>Metacity>General
and in the "General" menu , find "num-workspaces" and change it to 8.
Save and exit.

---

### Post by nevbear666 on 2011-07-05
hi Rasa1111

first of all, thanks for the fast answer.

the problem is, that metacity is not the unity desktop manager, metacity is not running, if i try to metacity --replace, i get a bailout and some screen blinking, before it crashes and freezes the desktop.

---

### Post by Rasa1111 on 2011-07-05
ahh nevbear,
Youre welcome, and my apologies. 
You seem to be correct.

I just tried to change mine and it did noting.. 

However, I did just find this~ [http://ubuntuforums.org/showthread.php?t=1723321](http://ubuntuforums.org/showthread.php?t=1723321)

> In  Unity, the default windows manager in Ubuntu 11.04, there is no obvious  way to change the number of available workspaces/virtual desktops so I  had to dig to find a way to do it. Here it is:
1. Go to the power icon in the top right hand corner and select it.
2. Press 'Systems Settings'
3. In the Systems Settings go to Compiz Config Settings Manager
4. In the Compiz Config Menu select 'General Options'
5. Go to the 'Desktop Size' and change your desktop settings by adjusting the number of vertical desktops.

That's it! Good luck and post if you have any questions. 
Also if any one wants to add an easier way to change the number of  workspaces the time to do it is now while 11.04 is still in beta.
                                                                                                  
                                                                        [URL="http://ubuntuforums.org/newreply.php?do=newreply&p=10647335"]
[/URL]I wonder if that will do it for you? 

Or this> [http://www.omgubuntu.co.uk/2011/05/quickly-adjust-the-number-of-workspaces-in-unity-with-indicator-workspaces/](http://www.omgubuntu.co.uk/2011/05/quickly-adjust-the-number-of-workspaces-in-unity-with-indicator-workspaces/)
[IMG]http://cdn.omgubuntu.co.uk/wp-content/uploads/2011/05/Selection_002.png[/IMG]
 Good luck mate. <3

---

### Post by nevbear666 on 2011-07-05
thx Rasa1111

the power applet option didnt work, was not there in my power applet, installing that 3rd party indicator workspaces worked like a charm.

hah, nice, unity is definitely feeling alot more at home now=)

---

### Post by beew on 2011-07-05
> **nevbear666 said:**
> hi fellow ubuntu users.

the topic really says it all, i was used to my 8 desktops on gnome, but i cannot find the setting in unity...

any help is greatly appreciated.
thx in advance
nb666

Open the Compiz Configuration Settings Manager aka CCSM (if you haven't, install it)
Go to General > General Options and click on the tab "desktop size" where you can set the number of desktops horizontally and vertically

---

### Post by Rasa1111 on 2011-07-05
No problem, Glad it worked out. :)

---

### Post by nevbear666 on 2011-07-05
hi beew

also thanks for looking into it.

just to let you know, i tried your tip too, using ccsm to set this didnt work.

---

### Post by Rasa1111 on 2011-07-05
> **nevbear666 said:**
> hi beew

also thanks for looking into it.

just to let you know, i tried your tip too, using ccsm to set this didnt work.


Since 11.04, 
It seems CCSM has more things that do not work, than things that do. lol

---

