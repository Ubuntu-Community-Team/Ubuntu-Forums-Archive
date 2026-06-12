---
title: "Effectie use of Lubuntu? alt? ctrl + super (windows button) + arrow?"
date: 2012-10-23
forum: Desktop Environments
---

### Post by Alcareru on 2012-10-23
Hi

How do I make Lubuntu usable?

I've been using Unity for some time now and it has some awesome features. It is however very much a resource hog, so I'm looking into alternatives. Now I'm toying with Lubuntu. However, ctrl + super (windows button) + arrow is an absolutely awesome feature. I love it so much. Alt + mouse middle button is another great feature (that actually existed long before Unity) not working in Lubuntu. How do I make ctrl + shift + arrow move windows from one virtual desktop to another? Where do I even find shortcut options in Lubuntu?

Obviously, one of the greatest things about Unity is that you never ever need to use your mouse to navigate through some horrible horrible menus desperately searching for the right submenu that hosts the launcher of the application you desire to launch. So instead of wondering where might I find the place where I can check status of my hard drives, I'd just press super + a and probably type "hard drive" or "disk" (and I didn't actually test this) and it would suggest me gnome-disks (though it would display the localized name for me). Is there any way of getting anything like that working on Lubuntu. Don't tell me to install Unity. What I want is a good search application functionality not fancy pants semitransparent compiz thingy to clog up my computer.

I appreciate the snappiness and the lightness, but if the only way to use it effectively is by the console then why even bother with the GUI...

Ty for all your tips of how to effectively use of Lubuntu!

---

### Post by netipot on 2012-10-23
I installed from the software center "synapse" for instant search. All you have to do is press ctl+space & start typing. It is very fast & accurate. 
Also I have made the "Start" button open the menu.
You go into pcmanFM & open file ~/.config/openbox/lxde-rc.xml with leafpad.

Scroll down to the keyboard section and enter a new key bind. 

    <keybind key="Super_L">
       <action name="Execute">
          <command>lxpanelctl menu</command>
       </action>
    </keybind>
          
save the file, log out and back in and the menu will now open with the left Windows button. 
If you want to use the right, substitute Super_R for Super_L or you can even add a binding for both. 
You might need to log out & back in.

---

### Post by Alcareru on 2012-10-23
Thanks mate, this is exactly the kind of stuff I'm looking for! If anybody has some more cool tips and tweaks like this I'm all ears. :) This config file is a gold mine! :) And the search utility is pretty nice too. Though a tad bit disappointing fact is that it can't find calculator.. unless you happen to know that the default calculator application is actually called galculator. I don't know if Unity actually does any better there, but in the perfect world it should suggest all calculator applications if I type in calculator. I mean galculator is quite close to calculator and I'm sure the word calculator is mentioned somewhere in the description of the package or something..

Anyhow, the config file you are referring to is btw (atleast with Lubuntu 12.10, that is):
~/.config/openbox/lubuntu-rc.xml
there is no file:
~/.config/openbox/lxde-rc.xml

My current changes to the default hotkeys are:
- Added that super button binding as you suggested
- Reverted to standard Ctrl+Shift+Arrow for moving things from one desktop to another, IMHO it's easier to use than the Lubuntu default. I did this like as follows:

I replaced these lines:
```

<keybind key="S-A-Left">
<keybind key="S-A-Right">
<keybind key="S-A-Up">
<keybind key="S-A-Down">

```
With these:
```

<keybind key="C-S-A-Left">
<keybind key="C-S-A-Right">
<keybind key="C-S-A-Up">
<keybind key="C-S-A-Down">

```

I also noticed that the "standard" alt + middle mouse button has a weird new usage and what I expected it to do is mapped for alt + right mouse button drag. I didn't change it though cos there seemed to be quite a lot of stuff related and I could almost see why they changed that... In any case I very much recommend that everybody who tries out Lubuntu should check out this file as the first thing to get familiarized with the OS.

Is there any documentation for the available actions? Can someone more familiar with this stuff tell me if I can make keybinding C-Super_L-Left take the currently focused window and snap it to the left side of the screen and resize it to occupy full height of and half of the width of the screen?

P.S. The synaptic thingys hotkey don't work unless the app is running (on background). In order to make sure it's running fire it up and look for a tiny little radio button on the right at the right edge of the window on the same height as the category labels are. Click on it and open the settings and tick the box telling it to start it on login (I got Finnish UI so I'm not sure about the exact wordings.)

P.P.S.
You don't need to logout, just issue the following command:
```
openbox --reconfigure
```

---

### Post by Rex Bouwense on 2012-10-23
See this site for some great tips.
[http://lxlinux.com/#index](http://lxlinux.com/#index)

---

### Post by netipot on 2012-10-23
Here are some other things I use.

If you want a different time/date display or different format, 
the available codes can be seen at  [http://linux.die.net/man/3/strftime](http://linux.die.net/man/3/strftime)  .
I use %A %d, %l:%M %P  =  day, date, time, am-pm   [lowercase "a" for abbreviation]
%B, %Y  =  month, year

Also an easy way to add docky  or cairo-dock.
Go to synaptic and install xcompmgr and docky or cairo-dock.
Type alt-F2/gksudo & type "leafpad" then open file & navgate to
 /etc/xdg/lxsession/Lubuntu/autostart

at the end add @xcompmgr
Save, reboot.
To  get cairo-dock to open on boot there is a button in it's configuration, for docky there might be the same.
If not add
@docky   the same as you did for xcompmgr.

---

### Post by vasa1 on 2012-10-23
> **Alcareru said:**
> ...
Is there any documentation for the available actions?...
Yes. Plus people have been posting tips here and you should be able to find them using appropriate search terms.
Unfortunately, since there are so many threads on similar topics, you may find the information you want several times over.

---

### Post by Alcareru on 2012-10-24
@Rex Thanks! Checked out that link. It had some useful stuff there.

@netipot Thanks! Configured the clock to be nicer.

@vasa1 Ok, could you by any change share this information with me? Would really like to get my hands on the documentation of those files. Btw. found your thread that had one more interesting link: [https://bbs.archlinux.org/viewtopic.php?id=93126](https://bbs.archlinux.org/viewtopic.php?id=93126) There's some cool looking tweaks going on there. Very close to what I was looking for! And yeah certainly you can find virtually anything from the internet.. so long as you can come up with the appropriate search terms. Tips or tweaks with lubuntu or lxde seem to yield at least some interesting results, but there's a lot to scour.

---

### Post by netipot on 2012-10-24
I started using LXDE with wattOS & you may find their forums to be easier to search & find stuff. They are doing great things over there.
[http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by vasa1 on 2012-10-24
> **Alcareru said:**
> ...
@vasa1 Ok, could you by any change share this information with me? Would really like to get my hands on the documentation of those files. ...
... so long as you can come up with the appropriate search terms. Tips or tweaks with lubuntu or lxde seem to yield at least some interesting results, but there's a lot to scour.

I suggest you add **openbox** to your search terms because that's the default manager that Lubuntu uses:
[http://openbox.org/](http://openbox.org/)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/) though some things may be a bit dated.
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks) (many of the links point back here).

A one-stop place would be ideal but given the *vibrancy* (that's the most neutral term I could come up with) of the community, there are nuggets all over the place!

---

