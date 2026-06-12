---
title: "Aero Snap for Linux"
date: 2014-09-04
forum: Desktop Environments
---

### Post by kakashi_12 on 2014-09-04
Anyone know of an equipvelant for Linux? I've read that OpenBox will do the trick. But I can't figure it out.

---

### Post by vasa1 on 2014-09-04
> **kakashi_12 said:**
> Anyone know of an equipvelant for Linux? I've read that OpenBox will do the trick. But I can't figure it out.What exactly can't you figure out?

---

### Post by kakashi_12 on 2014-09-04
How to configure it.

---

### Post by vasa1 on 2014-09-04
Read [https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse)
Read pclosmag.com/html/Issues/201107/page08.html

Openbox is for people willing to take some trouble setting things up.

---

### Post by kakashi_12 on 2014-09-05
Followed directions exactly, but it didn't work.
When I press the key combinations specified, nothing happens.

---

### Post by vasa1 on 2014-09-05
What is your operating system?
What is the output of **lsb_release -a**?
What is the output of **env | grep XDG_CURRENT_DESKTOP**?
What is the output of **echo $DESKTOP_SESSION**?
Install **wmctrl** and then post the output of **wmctrl -m**.
Run **ls /usr/share/xsessions** and post that output here.
Run **ls ~/.config | grep openbox** and post that output here.

**Please use code tags for each output.**

---

### Post by vasa1 on 2014-09-05
BTW, if you prefer, Xubuntu also offers aerosnap, IIRC. You may find that more user-friendly.

---

### Post by kakashi_12 on 2014-09-05
> **vasa1 said:**
> What is your operating system?
What is the output of **lsb_release -a**?
What is the output of **env | grep XDG_CURRENT_DESKTOP**?
What is the output of **echo $DESKTOP_SESSION**?
Install **wmctrl** and then post the output of **wmctrl -m**.
Run **ls /usr/share/xsessions** and post that output here.
Run **ls ~/.config | grep openbox** and post that output here.

**Please use code tags for each output.**

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

```
XDG_CURRENT_DESKTOP=Unity
```
Don't know why it says Unity, 'cause I actually use Metacity.

```
gnome-fallback
```

```
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A
```

```
gnome.desktop                  gnome-fallback.desktop  ubuntu.desktop
gnome-fallback-compiz.desktop  openbox.desktop
```

```
openbox
```

---

### Post by vasa1 on 2014-09-06
Well, it looks like you have Openbox installed but it it isn't your window manager. You're using metacity.

Also, when you post code, please include the command so it's easy to tell what the output is related to.

---

### Post by vasa1 on 2014-09-06
If you want to run Openbox as your window manager (wm) instead of anything else, you need to run```
openbox --replace
``` or prevent any other wm from autostarting and have openbox autostart. I myself use Openbox with a distro, Lubuntu, that has Openbox as the only wm and so there's no confusion.

I'm not in a position to assist anyone who has multiple wms and wants to switch between them.

---

### Post by kakashi_12 on 2014-09-06
ok, how would I switch back if I wanted to leave that option open?

---

### Post by vasa1 on 2014-09-06
> **kakashi_12 said:**
> ok, how would I switch back if I wanted to leave that option open?
As I said, I don't have any experience in switching between window managers. Maybe someone who has such experience can help.

---

### Post by steeldriver on 2014-09-06
... metacity also has a --replace option

```

man metacity

       --replace
              a window manager which  is  running  is  replaced  by  metacity.
              Users  are encouraged to change the GNOME window manager by run&#8208;
              ning the new WM with the --replace or -replace option, and  sub&#8208;
              sequently saving the session.

```

---

### Post by Rob Sayer on 2014-09-07
Installing openbox ... which you may not realize is an older and much more basic window manager than you have in unity ... just to simulate something like aero snap seems to me a very convoluted way to just enable snap top grid.  You're just introducing a ton of complexity and potential problems that you won't be able frankly to fix without a lot of help.

And you're quite unlikely to be happy running the unity DE with openbox because it's a lightweight WM that doesn't have nearly the features metacity has.  I strongly suspect you'll be more happy living without grid snap than all this bother.

I haven't used the unity DE version of ubuntu for a while so I don't know how snap to grid works there.  But you *must* be able to do it more simply than this.  Or maybe not.  Actually KDE (kubuntu) does this automatically if you turn off all effects.  I think.  It's been a while since I configured it.

---

### Post by kakashi_12 on 2014-09-07
what types of features does metacity offer that this won't?

---

### Post by kakashi_12 on 2014-09-08
This seems to work pretty well for the *most part*!
I did the openbox replace command. And it immediately switched to the new Window Manager. Then I was able to "snap" windows left and right with no problem (since I editted the rc.xml file).
Problem is that when I close the terminal, it switches back to Metacity. And then Metacity is 'funked'. It looses the Title Bar.
Only way to fix it is to log out and log back in. Then Metacity comes back normal.
How do I get OpenBox to stay the default?
Cause when I enter the command, it does not go back to the normal 'prompt' where it shows your username. It goes to a blank line where you have to close or press Ctrl + C.

---

### Post by vasa1 on 2014-09-08
Just a guess but what happens if you try
```
openbox --replace & exit
```?

---

### Post by kakashi_12 on 2014-09-08
worked this time. Except after logging out and back in. Goes back to MetaCity.
Anyway to get it to stick? Or should I just make it a Start Up Application to make things easier. Unless there is a better way.

---

### Post by vasa1 on 2014-09-08
> **kakashi_12 said:**
> worked this time. Except after logging out and back in. Goes back to MetaCity.
Anyway to get it to stick? Or should I just make it a Start Up Application to make things easier. Unless there is a better way.
No idea :(

---

### Post by kakashi_12 on 2014-09-08
Only other problem I'm having is that when I switch to this Window Manager, some of my Keybindings are lost/reset. I had Ctrl + Left OR Right to Switch between workspaces. And now it's not working.

---

### Post by kakashi_12 on 2014-09-08
Ok, fixed that. Figured out that dconfig editor only applies to metacity. Or at least for certain keybindings.
I had to go back into the openbox config file in /home/.config/openbox.
Then add in the keybindings. then run ```
openbox --reconfigure
```
I found the approriate keybindings here
[HTML]http://melp.nl/2011/01/10-must-have-key-and-mouse-binding-configs-in-openbox/[/HTML]
I used a C for Ctrl instead of W for Windows.

Also, made the script file in gedit. Then saved and made executable. Then put it in startup apps.

Anyone understand the difference between Desktop Environment and Window Manager? I just saw at login screen that OpenBox shows up as a DE now too.
Not sure if it works, and frankly don't want to mess with it 'cause it works just perfectly the way I want now so. I'll just leave it. But just wondered.

Thanks for your help!

---

### Post by kakashi_12 on 2014-09-08
_Final Resolution_:

01. Install OpenBox from Ubuntu Software Center.
02. open /$home/.config/openbox/rc.xml with gedit.
03. search for a line that has just ```
</keyboard>
```. Then, just above that line, paste in all the code from this url.
([https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse))
05. Add keybindings in for OpenBox Window Manager to switch between workspaces...
  ```
<keybind key="C-Right">   <action name="DesktopRight"><wrap>no[COLOR=#000000]</wrap[COLOR=#000000]>[/COLOR]</action[COLOR=#000000]>[/COLOR]</keybind[COLOR=#000000]>[/COLOR][/COLOR]
[COLOR=#009900][COLOR=#000000]<keybind[/COLOR] [COLOR=#000066]key[/COLOR]=[COLOR=#ff0000]"C-Left"[/COLOR][COLOR=#000000]>[/COLOR][/COLOR]    [COLOR=#009900][COLOR=#000000]<action[/COLOR] [COLOR=#000066]name[/COLOR]=[COLOR=#ff0000]"DesktopLeft"[/COLOR][COLOR=#000000]>[/COLOR][COLOR=#000000]<wrap[COLOR=#000000]>[/COLOR][/COLOR][/COLOR]no[COLOR=#009900][COLOR=#000000]</wrap[COLOR=#000000]>[/COLOR][/COLOR][COLOR=#000000]</action[COLOR=#000000]>[/COLOR][/COLOR][COLOR=#000000]</keybind[COLOR=#000000]>[/COLOR][/COLOR][/COLOR]
```  
04. save and exit.
05. run ```
openbox --reconfigure
```
06. Open gedit and paste the text below. save and close.
```
openbox --replace & exit
```
07. make the file executable. ```
chmod +x filename
```
08. Go to Applications, System Tools, Preferences, Startup Applications. Then point to the file I created.
09. open gedit and past the text below. save and close.
```
metacity --replace
```
10. make the file executable. ```
chmod +x filename
```
11. Drag both of these script files (openbox and metacity) to the GNome panel so they can become Launchers.
Use these to easily switch back and forth between Window Managers when necessary.
12. Open the openbox config file back up again. Find the keybind to take a screenshot. Make sure it is set to use Control and Alt.
13. Find the keybind for W-Up. Change this so that y is 0 and height is 100%.
14. Save file and exit. Run the reconfigure cmd above.

---

