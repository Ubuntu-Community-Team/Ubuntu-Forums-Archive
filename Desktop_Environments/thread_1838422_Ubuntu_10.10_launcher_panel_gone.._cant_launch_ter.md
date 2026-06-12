---
title: "Ubuntu 10.10 launcher panel gone.. cant launch terminal"
date: 2011-09-03
forum: Desktop Environments
---

### Post by BHEJU on 2011-09-03
Hi
I launched gconf-editor and removed the "gnome-panel" from panel key. I just wanted to get rid of the bottom panel.

However, after reboot I lost the top panel as well. 
I googled this and found out that I can create a command to launch terminal on desktop and run some commands to fix it.

However when I create a launcher command for terminal and launch it. I get error saying :"failed to launch child process 'terminal' (no such file or directory)".

So can't launch terminal.

However, I do have access to nautilas as there is a drive mounted and the icon's on desktop. so I can access the file system.

Please help me get my top panel back.

---

### Post by sikander3786 on 2011-09-03
Right click your desktop and create a new launcher with the command:

```
gnome-terminal
```

No capital letters involved. Then double click it and run:

```
gconf-editor
```

And re-enable the panels.

---

### Post by josephmills on 2011-09-03
> **BHEJU said:**
> Hi
I launched gconf-editor and removed the "gnome-panel" from panel key. I just wanted to get rid of the bottom panel.

However, after reboot I lost the top panel as well. 
I googled this and found out that I can create a command to launch terminal on desktop and run some commands to fix it.

However when I create a launcher command for terminal and launch it. I get error saying :"failed to launch child process 'terminal' (no such file or directory)".

So can't launch terminal.

However, I do have access to nautilas as there is a drive mounted and the icon's on desktop. so I can access the file system.

Please help me get my top panel back.


Ahh crap I hate it when things like that happen:) 

there are a couple of options here first we can reinstall the pannel 
```
sudo apt-get install gnome-panel
``` or we can try and rest it to og stause yo-yo (look I am a thug ) :) 

[COLOR=Black][COLOR=#FF0000]******[/COLOR][/COLOR]
```
gconftool - -recursive-unset /apps/pannel && rm -rf ~/.gconf/apps/pannel && pkill gnome-pannel
```

hopes this helps 
[COLOR=#FF0000]***[FONT=Verdana][/FONT]***[/COLOR]

---

### Post by BHEJU on 2011-09-03
Thank you Guys. Problem solved. I gave shot to "gnome-panel" instead of terminal. It worked. Back in business.

Cheers,

---

### Post by Catlike on 2011-09-06
> **sikander3786 said:**
> Right click your desktop and create a new launcher with the command:

```
gnome-terminal
```No capital letters involved. Then double click it and run:

```
gconf-editor
```And re-enable the panels.

But how does one re-enable the panels?

---

### Post by BHEJU on 2011-09-07
Well simple, once I was able to launch the panel once...

I just reversed my steps which caused the panel to go away..

What I did to cause the panel to go away :
I launched gconf-editor and REMOVED the "gnome-panel" from panel key.

What I did to get the panel back:
I launched gconf-editor and ADDED the "gnome-panel" from panel key.

---

### Post by Catlike on 2011-09-08
> **BHEJU said:**
> Well simple, once I was able to launch the panel once...

I just reversed my steps which caused the panel to go away..

What I did to cause the panel to go away :
I launched gconf-editor and REMOVED the "gnome-panel" from panel key.

What I did to get the panel back:
I launched gconf-editor and ADDED the "gnome-panel" from panel key.

What is the "panel key"? Where or how do I find it? Once I find it, how do I add the "gnome-panel"? 
I've looked through lots of "gnome" items in the gconf-editor, and I don't see anything that looks right.

Thank you for replying.

---

### Post by BHEJU on 2011-09-09
Well.. you run goconf-editor.. it opens up GUI.. navigate to :
/desktop/gnome/session/required_components_list/ Panel

Panel is the key here and the value for it should be "gnome-panel".

This worked for me because I had removed the value for the key and lost the panel. So, once I was able to run the gconf-editor.. I just added the value back.

I am not really sure what the issue is with your system. You can try these steps.. if it does not work.. you should post the details of the issue. So, someone who knows more about this can enlighten you (and me both).

Cheers,

---

### Post by Catlike on 2011-09-10
Thank you. In my gconf-editor, in /desktop/gnome/session , there is no components list. There is a folder called "required_components" but it has only one item in it -- something called "windowmanager" .
This leads me to think I need to re-load Natty Narwhal.

---

### Post by sikander3786 on 2011-09-13
> **Catlike said:**
> Thank you. In my gconf-editor, in /desktop/gnome/session , there is no components list. There is a folder called "required_components" but it has only one item in it -- something called "windowmanager" .
This leads me to think I need to re-load Natty Narwhal.
If you are having problems with Unity in Natty, please take a look here:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by psrdotcom on 2011-09-13
The Keyboard Shortcut to open the terminal Ctrl+Alt+T

---

