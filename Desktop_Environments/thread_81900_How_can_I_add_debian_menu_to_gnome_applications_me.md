---
title: "How can I add debian menu to gnome applications menu?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by lux on 2005-10-25
I have installed many applications that don't show up in gnome applications menu, so I thought it would be nice to be able to view the debian menu that automatically shows all installed apps. How can I add debian menu to gnome applications menu?

I found "menu editor" from gnome applications menu but I don't know how to use it to add debian menu as a submenu in gnome applications menu. There seems to be an entry for debian menu in the menu editor but the "visible" box beside this entry is empty, and when I click the "visible" box in order to make debian menu visible, nothing happens. I have installed the "menu" package via Synaptic.  :confused: 

Any ideas?

---

### Post by angkor on 2005-10-25
sudo apt-get install menu ?

---

### Post by matthew on 2005-10-25
[quote=angkor]sudo apt-get install menu ?[/quote]

After it has been installed you need to do this in a terminal:

```
update-menus
```

---

### Post by lux on 2005-10-25
Like I said in my initial post, I **have** installed menu. "update-menus" doesn't help. Debian menu works fine in wmaker, I'd just like to have it available also in gnome menu.

Any more ideas?

---

### Post by matthew on 2005-10-25
[quote=lux]Like I said in my initial post, I **have** installed menu. "update-menus" doesn't help. Debian menu works fine in wmaker, I'd just like to have it available also in gnome menu.

Any more ideas?[/quote]

That's weird. Sorry for the mis-info. That was what I did under Hoary and it got me the Debian menu just fine. I just tested in in Breezy and had the same results as you did. I have no idea why.

---

### Post by SilentCacophony on 2005-10-25
It should work if you install menu-xdg:

**sudo apt-get install menu-xdg**

I found that I needed that to get it to show up in gnome's Applications menu.

---

### Post by matthew on 2005-10-25
[quote=SilentCacophony]It should work if you install menu-xdg:

**sudo apt-get install menu-xdg**

I found that I needed that to get it to show up in gnome's Applications menu.[/quote]
That was the missing step...worked beautifully for me. Thanks!

---

### Post by xsence on 2005-10-25
Do you have a picture of those menus?

i'm trying to get rid op the ubuntu logo/ applications/ locations/ system thingies.

i want to configure it just like windows.. start bart/ quickstarts/ taskbar etc.

i have seen it in some themes also.

can someone help me with this.

---

### Post by lux on 2005-10-25
> It should work if you install menu-xdg:

sudo apt-get install menu-xdg

I found that I needed that to get it to show up in gnome's Applications menu.
Thanks. :)

---

### Post by angkor on 2005-10-25
[QUOTE=xsence]Do you have a picture of those menus?

i'm trying to get rid op the ubuntu logo/ applications/ locations/ system thingies.

i want to configure it just like windows.. start bart/ quickstarts/ taskbar etc.

i have seen it in some themes also.

can someone help me with this.[/QUOTE]

Just right-click the panel and add what you like. I don't know what you mean by 'configure it just like windows' nor why you would want to.

Add some application launchers, a windows list and a notification area and you'll have the same functions you had in Windows.

Note you can also drag items from the applications menu to the panel to create launchers.

---

### Post by xsence on 2005-10-25
[QUOTE=angkor]Just right-click the panel and add what you like. I don't know what you mean by 'configure it just like windows' nor why you would want to.

Add some application launchers, a windows list and a notification area and you'll have the same functions you had in Windows.

Note you can also drag items from the applications menu to the panel to create launchers.[/QUOTE]

Please look on this picture, this is what i want to do with it.

[http://gnome-look.org/content/preview.php?preview=1&id=26757&file1=26757-1.jpg&file2=26757-2.png&file3=26757-3.png&name=Graphite+Suite](http://gnome-look.org/content/preview.php?preview=1&id=26757&file1=26757-1.jpg&file2=26757-2.png&file3=26757-3.png&name=Graphite+Suite)

---

### Post by fannymites on 2005-10-25
Not sure if this is what you mean but try right-clicking on the panel, select "add to panel" then select main menu (not menu bar)

---

### Post by xsence on 2005-10-25
Yes thats it :) thanks man.

it looks cleaner now and all the menu's are in this one.

---

### Post by ArukiRei on 2005-10-26
[QUOTE=SilentCacophony]It should work if you install menu-xdg:

**sudo apt-get install menu-xdg**

I found that I needed that to get it to show up in gnome's Applications menu.[/QUOTE]

This isn't working for me. I keep getting this...

Reading package lists... Done
Building dependency tree... Done
Package menu-xdg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package menu-xdg has no installation candidate

any help is appreciated :D

---

### Post by matthew on 2005-10-26
[quote=ArukiRei]This isn't working for me. I keep getting this...

Reading package lists... Done
Building dependency tree... Done
Package menu-xdg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package menu-xdg has no installation candidate

any help is appreciated :D[/quote]

Try this [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) and then
```
sudo apt-get update
``` and try again to install menu-xdg

---

### Post by ArukiRei on 2005-10-26
I got menu-xdg to finally install, but the debian menu to pop up. I'm also trying to get all the apps to appear on my menu, but I only get the starting apps.

---

### Post by fannymites on 2005-10-26
I couldn't get the debian menu to appear either.  I think I did "killall gnome-panel" or logged out and back in again.

---

### Post by SilentCacophony on 2005-10-26
> I couldn't get the debian menu to appear either. I think I did "killall gnome-panel" or logged out and back in again.

If you haven't done:

**update-menus**

in a terminal yet, since installing menu and menu-xdg, try that.

Otherwise, you might want to run smeg (in Breezy, Applications > System Tools > Applications Menu Editor) and see if you can tick it on in there.

---

### Post by ArukiRei on 2005-10-26
[QUOTE=SilentCacophony]If you haven't done:

**update-menus**

in a terminal yet, since installing menu and menu-xdg, try that.

Otherwise, you might want to run smeg (in Breezy, Applications > System Tools > Applications Menu Editor) and see if you can tick it on in there.[/QUOTE]

Still can't click the Debian option in the menu. I've tried the "update-menus" in the terminal but it doesn't seem to be a valid command. :(

---

### Post by SilentCacophony on 2005-10-27
[QUOTE=ArukiRei]Still can't click the Debian option in the menu. I've tried the "update-menus" in the terminal but it doesn't seem to be a valid command. :([/QUOTE]

That's odd. The **update-menus** script should have been installed with the **menu** package. Just to be clear, you have to install both the **menu** and **menu-xdg** packages for it to work, then you should run update-menus, then you may have to log out of gnome and log back in. This is all I had to do:

```
sudo apt-get install menu menu-xdg
update-menus
```

Then the panel should update when you access the Applications menu. You may have to logout/login to gnome, though I didn't have to.

---

### Post by ArukiRei on 2005-10-27
[QUOTE=SilentCacophony]

```
sudo apt-get install menu menu-xdg
update-menus
```

Then the panel should update when you access the Applications menu. You may have to logout/login to gnome, though I didn't have to.[/QUOTE]

Having that extra **menu** in the install command did the trick. Finally got the Debian menu to appear, Thanks guys. Now the next step is to get the anti-virus program in the get application menu to appear in the menu as well. :S

---

### Post by qpackard on 2006-05-02
Using 5.10
I still can't get deb menu to appear although I've downloaded it (and I can't find it but SPM says it's here). I ran the commands found in the thread with these results:

qp@Home:/$ sudo apt-get install menu menu-xdg
Reading package lists... Done
Building dependency tree... Done
menu is already the newest version.
menu-xdg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
qp@Home:/$ update-menus
qp@Home:/$

Yet the menu does not appear in Applications. In Add Applications a search for Menus did not show it, a search for Debian brought up debian configure.
Right-click on the menu bar did reveal it. A system search for menu brought up over 200 items but nothing that looked like debian menu.

What have I missed?

---

### Post by dysfunctional on 2006-10-17
> **qpackard said:**
> Using 5.10
I still can't get deb menu to appear although I've downloaded it (and I can't find it but SPM says it's here). I ran the commands found in the thread with these results:

qp@Home:/$ sudo apt-get install menu menu-xdg
Reading package lists... Done
Building dependency tree... Done
menu is already the newest version.
menu-xdg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
qp@Home:/$ update-menus
qp@Home:/$

Yet the menu does not appear in Applications. In Add Applications a search for Menus did not show it, a search for Debian brought up debian configure.
Right-click on the menu bar did reveal it. A system search for menu brought up over 200 items but nothing that looked like debian menu.

What have I missed?

I'm having the exact same problem... and i've read this thread several times and done everything..... i'm running dapper.. it works fine on another computer though,.... so i'm really missing this menu on this computer!! :( :(. any suggestions??

---

### Post by deserthowler on 2007-09-11
> **SilentCacophony said:**
> It should work if you install menu-xdg:

**sudo apt-get install menu-xdg**

I found that I needed that to get it to show up in gnome's Applications menu.

That worked for me too.  Thank you so much.

Earl

---

### Post by glantucan on 2007-09-24
I've installed all you said and when I try:
```
update-menus
```

I get this:
```

No se pudo abrir el fichero «/etc/menu-methods//etc/menu-methods/menu.h».
install-menu: /etc/menu-methods/jwm: abortando
update-menus[24655]: El guión /etc/menu-methods/jwm devolvío un estado de error 1.

```

Which more or less means:
```
The file «/etc/menu-methods//etc/menu-methods/menu.h» couldn't be open
install-menu: /etc/menu-methods/jwm: aborting
update-menus[24655]: The script /etc/menu-methods/jwm released an error state of 1.

```

Help :(

---

