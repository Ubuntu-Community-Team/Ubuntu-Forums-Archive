---
title: "top panel dissappeared now can't even shutdown"
date: 2010-07-31
forum: Desktop Environments
---

### Post by shultzjr on 2010-07-31
somehow I right clicked on the panel at the top and then left clicked on something that made the panel disappear permenantly.  now when I turn the computer on it goes to the login screen, I put in my password and the desktop has no panel bar across the top of the screen (no way to even run a program)  to turn in off I have to push the power button.

how do I get my panel back?  standard ubuntu 10.04 64 bit not server.

thanks,
charles.......

---

### Post by Version Dependency on 2010-07-31
I'm sure someone will come along and give you help on getting your panel back.  But I can at least help you shutdown your computer without having to resort to the power button.

In terminal: 
```
gnome-session-save --shutdown-dialog
```

---

### Post by shultzjr on 2010-07-31
can't even bring up a terminal window so how would I run the command?

---

### Post by Version Dependency on 2010-07-31
> **shultzjr said:**
> can't even bring up a terminal window so how would I run the command?

Right-click on your desktop and create a document with the above code.  Save it.  Right-click on it again and go to properties and make it executable.  Now when you click in it, it should give you the option to "run in terminal."  

You can do this to open up any program you need...such as gnome-terminal, avant-window-navigator (or whatever dock you may have), etc.

---

### Post by shultzjr on 2010-07-31
what "above code"?

---

### Post by Version Dependency on 2010-07-31
> **shultzjr said:**
> what "above code"?
gnome-session-save --shutdown-dialog

---

### Post by shultzjr on 2010-07-31
isn't there some text file I can change to get my panel back?

doing your instructions will take me a little bit, computer is in another room.

thanks.

---

### Post by Version Dependency on 2010-07-31
> **shultzjr said:**
> isn't there some text file I can change to get my panel back?

doing your instructions will take me a little bit, computer is in another room.

thanks.

I have no idea what's wrong with your panel.  But try the following:

Do what I suggested with creating a document.  Type this into the new document: 
```
gnome-terminal
```Save the document.  Right-click the new document, go to Properties, and make it executable.  Exit out of this.  Now click on the new document and choose "run in terminal".  Now we have a terminal open.

Now type in the terminal:
```
gnome-panel
```Tell us what happens and copy any error messages if any.

---

### Post by Raymond2201 on 2010-07-31
you can reset your whole desktop to as it was when you first installed Ubuntu (all your prgrams you have installed will be fine, this will just restore your desktop settings to default)

hit ALT+F2 to get the run terminal copy paste the following in

```
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
```

check the "run in terminal" checkbox.

hit ALT+F2 again
```
 sudo reboot
```

When you log back in you should have all the default settings for your desktop restored.


good luck!

---

### Post by Ginsu543 on 2010-08-01
If you want to get your top panel back, try the following:
1) Press Alt+F2
2) Type "gnome-terminal" and ENTER (this will launch the Terminal)
3) Inside Terminal, type "gconftool --recursive-unset /apps/panel" and ENTER
4) Then type "rm -rf ~/.gconf/apps/panel" and ENTER
5) Then type "pkill gnome-panel" and ENTER

That should restore the top panel factory fresh.

---

### Post by markMDW on 2010-08-19
Hi there.  I lost my start Panel as well, but I have Xubuntu 9.10 with the XFCE 4.6.1 manager rather than Gnome.  Fortunately I can right click on the xfce desktop and do most everything as I could with the start panel applets, but what I CAN'T do is run the network manager applet to connect to the wi-fi internet.
 
I posted a new thread in General Help yesterday and there have been 18 views and 0 replies, so I figured I better search for another thread that's active and getting responses.  
 
Do you have a script that could load the Xubuntu Panel back?   Thanks!

---

### Post by markMDW on 2010-08-21
> **markMDW said:**
> I researched and solved the problem with the  missing starting Panel in Xubuntu.  If it ever inadvertently gets  deleted then just do the following to get it back permanently:

Right click in the empty desktop area> Create Launcher
[the Create Launcher dialog box opens]

type into the empty "Command:" text field the command below:
xfce4-panel

type into the empty "Name:" text field whatever suits your fancy:
Xubuntu Panel

Under "Options" check this box:
[x] Use Startup Notification

Under "Icon" keep the field at default for no icon:
[No icon]

then create the launcher by pressing the create button at the bottom of the dialog box:
[Create]

all done!   you can create an icon if you like but it pops up on the  desktop, which is unnecessary since you want this Panel to start every  time you login without clicking the icon on the desktop.

I'm relatively new to Linux so pardon me if I posted something too  elementary.  I guess some may have thought I had an incurable case of  ignorance and didn't bother to posts.  ):PHave a great day!

I found my own answer: For an  Xubuntu starting panel that gets deleted, this should work

---

### Post by ericmarceau on 2010-12-05
This worked for me.  You´re a life saver!
Thx,

EM

=================================

> **Ginsu543 said:**
> If you want to get your top panel back, try the following:
1) Press Alt+F2
2) Type "gnome-terminal" and ENTER (this will launch the Terminal)
3) Inside Terminal, type "gconftool --recursive-unset /apps/panel" and ENTER
4) Then type "rm -rf ~/.gconf/apps/panel" and ENTER
5) Then type "pkill gnome-panel" and ENTER

That should restore the top panel factory fresh.

---

### Post by karthick87 on 2010-12-05
Mark it as[COLOR=Red] [SOLVED][/COLOR]

---

