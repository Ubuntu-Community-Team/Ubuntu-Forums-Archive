---
title: "Keyboard shortcut to hide/unhide the top panel?"
date: 2009-12-04
forum: Desktop Environments
---

### Post by jjsonp on 2009-12-04
I want to hide the top panel via a keyboard shortcut. I don't much like auto-hide, and don't want to have to click the buttons to hide/unhide.

Is there some preset keyboard command for this? If not, is there a command (or a script) to which I can link a keyboard shortcut? Thanks.

---

### Post by aysiu on 2009-12-05
I don't believe there is. If you try the command ```
man gnome-panel
``` you'll see there are very few options there.

---

### Post by martin-alsinet on 2010-03-20
> **jjsonp said:**
> I want to hide the top panel via a keyboard shortcut. I don't much like auto-hide, and don't want to have to click the buttons to hide/unhide.

Is there some preset keyboard command for this? If not, is there a command (or a script) to which I can link a keyboard shortcut? Thanks.
You can use Alt+F1 to show the Application Menu, which will unhide the top panel, then Esc to hide it back again. I changed it to Ctrl+F1, which is easier to hit for me

---

### Post by asmoore82 on 2010-03-20
You can save this as a "HidePanels"
```
[COLOR="Purple"]#!/bin/bash[/COLOR]

count=0
while read line
do
   keys[$((++count))]="${line}/auto_hide"
done <<EOF
$( gconftool-2 --all-dirs "/apps/panel/toplevels" )
EOF

case $( gconftool-2 --get "${keys[1]}" ) in
   "0" | "false" | "False" )
      new="true"
      ;;
   * )
      new="false"
      ;;
esac

for key in "${keys[@]}"
do
   gconftool-2 --set "$key" --type bool "$new"
done

[COLOR="Purple"]#End of File[/COLOR]
```

Then, copy it to a common folder and make it executable:
```
sudo cp HidePanels /usr/local/bin/HidePanels
sudo chmod +x /usr/local/bin/HidePanels
```

and set it as a custom keyboard shortcut command:
```
gconftool-2 --set "/apps/metacity/keybinding_commands/command_1" --type string "/usr/local/bin/HidePanels"
gconftool-2 --set "/apps/metacity/global_keybindings/run_command_1" --type string "<Control>F1"
```
^adjust "command_1" and "<Control>F1" as necessary

:KS

---

### Post by laman259 on 2010-09-02
Hey I want to do the same thing

I created a new panel with all my useful applications on it, don't want to use the auto-hide but can't be bothered clicking on the arrows to hide it.

Don't really understand anything said above as a solution due to my newness to Linux. :S

Would be sweet as if i could have a keyboard shortcut to hide and un-hide :D

Cheers

---

### Post by stinkeye on 2010-09-03
This will basically do the same as asmoore82's post but without using the terminal.
You'll find later on that for some things it's easier to use the terminal.
Especially when you might be getting answers to something,
it's a lot easier for someone to give a terminal command you can copy and paste 
rather than typing go here ..click this ...right click here etc etc. 

From asmoore82's post, copy the script in the first code box.
Open up your home folder.
Right click on an empty space ....create document > empty file
Change the name to **HidePanels** 
Open the HidePanels file and paste in the script you copied.
Hit the Save button and close.

Right click on the new  HidePanels file.
Properties > permissions .....and tick execute.

Go to the main menu > system > preferences > keyboard shortcuts 

Click the add button 
Name: **HidePanels**
Command: **/home/[COLOR="Magenta"]your_username[/COLOR]/HidePanels**

[COLOR="#ff00ff"]Substitute for your username[/COLOR]
Hit the apply button.
Click the shortcut field and add your own shortcut.

---

### Post by wei2912 on 2010-10-08
It works quite well. However, is there a way to make the panel not show up even when your mouse is over it? I can't delete the top panel.

---

### Post by stinkeye on 2010-10-08
> **wei2912 said:**
> It works quite well. However, is there a way to make the panel not show up even when your mouse is over it? I can't delete the top panel.

Is this what your after .... [**_[COLOR="DarkRed"]Remove all gnome panels on ubuntu lucid lynx[/COLOR]_**]("http://balotp.wordpress.com/2010/08/10/remove-all-gnome-panels-on-ubuntu-lucid-lynx/")

---

### Post by Sotanaht on 2011-08-03
I want to use a floating panel as sort of a system management tool, with resource monitors and a force close button, but I don't know what part of that script to alter to make it hide and show my floating panel instead of the one at the top.  I'm guessing I have to replace "toplevels" in line 8 with something, but idk what that something is.

---

### Post by Sotanaht on 2011-08-03
After looking in gconf-editor, I navigated to apps > panel > toplevels, and I determined that the panel I wanted to hide was panel_8 by right clicking it, and setting it to autohide in properties, and then searching for the only panel with autohide enabled in gconf-editor (I double-checked by disabling autohide in gconf-editor and seeing if it changed it for the panel as well, which it did).  So I changed line 8 in the script to the following
```
$( gconftool-2 --all-dirs "/apps/panel/toplevels/panel_8" )
```
but when I run the script, it merely opens a terminal for a split-second and does nothing.
What am I missing here?  Does this script simply not work with floating panels?

---

### Post by peskydonut on 2011-08-24
> **wei2912 said:**
> It works quite well. However, is there a way to  make the panel not show up even when your mouse is over it? I can't  delete the top panel.
You can set the **unhide_delay** to 1000 before hiding and to 0 before showing.
*Source: *[http://reachbeyondgrasp.blogspot.com/2007/04/hide-and-show-panels-with-keyboard.html](http://reachbeyondgrasp.blogspot.com/2007/04/hide-and-show-panels-with-keyboard.html)

---

### Post by DorianScholz on 2011-11-04
just as a hint for those looking to do this on gnome3. gconf is not the right way to go anymore, use gsettings instead:
```
$ gsettings set org.gnome.gnome-panel.toplevel:/org/gnome/gnome-panel/layout/toplevels/toplevel-0/ unhide-delay 10000
$ gsettings set org.gnome.gnome-panel.toplevel:/org/gnome/gnome-panel/layout/toplevels/toplevel-0/ auto-hide true

```

---

### Post by BaroqueBloke on 2012-09-07
EDIT 3: I've managed to [achieve a floating panel]("http://opensourceexcedio.wordpress.com/2010/12/29/gnome-wingpanel/") after a fashion.  Not entirely legit... but it gets the job done.  

EDIT 2:  Never Mind!  I got just the top panel to  hide by adding the path to the top panel to the script.  
in my case I had to add "panel_0"  

Still just working on having it unhide as a floating panel...  Will get back to you when I figure it out.
  
Hope this helps someone!

```

#!/bin/bash

count=0
while read line
do
   keys[$((++count))]="${line}/auto_hide"
done <<EOF
$( gconftool-2 --all-dirs "/apps/panel/toplevels/**panel_0**")
EOF

case $( gconftool-2 --get "${keys[1]}" ) in
   "0" | "false" | "False" )
      new="true"
      ;;
   * )
      new="false"
      ;;
esac

for key in "${keys[@]}"
do
   gconftool-2 --set "$key" --type bool "$new"
done

#End of File

```

EDIT:  I should also note that I realize this is an old thread... but any help I can find is welcome.  

Thanks everyone for the info.  So far so good, the scripts provided work.  

Question however.  I have a left side/vertical panel, and a top panel.  How should I edit the script so that only the top panel is hidden/shown via the keyboard command?  I would like the left hand panel to always be visible.  

As an after thought, how would I go about making the top panel, when shown, to sit ontop of open windows, rather than pushing them down?  

Any info is appreciated, regardless or not its possible.  

Thanks!

-Baroquebloke-

---

