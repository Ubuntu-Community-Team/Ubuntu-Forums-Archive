---
title: "Openbox keyboard shortcuts in Lubuntu Saucy"
date: 2014-03-25
forum: Desktop Environments
---

### Post by Matthew_Bird on 2014-03-25
Hey all!

In my previous incarnation of lubuntu, I had keyboard shortcuts set up from the lubuntu-rc.xml file such as the following:

```
    <keybind key="W-Left">        # HalfLeftScreen      
    <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><height>100%</height><width>50%</width></action>
    </keybind>
    <keybind key="W-Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>-0</x><y>0</y><height>100%</height><width>50%</width></action>
    </keybind>
```

This enabled me to quickly right/left maximise a window, which was a really useful tool. However, after upgrading to Saucy, the windows no longer move and resize to the specifications in the xml file. [Here's an example.]("http://i.imgur.com/tFYH4OS.png") (For those who can't see that, there is a gap at the bottom of the window (different sized for each window), and each window is slightly moved to the left, causing the left-maximised window to be partially off the screen, and creating a gap on the right side of the right-maximised window.)

For some reason, editing the xml file seems to have no effect - for instance, I can change the <height> to 10000000000000% and nothing changes. So I'm guessing the problem is something to do with Saucy bypassing this file altogether?

Does anyone know a workaround for this?

Thanks!

---

### Post by vasa1 on 2014-03-25
Hi, have you run **openbox --reconfigure** to ensure your changes take immediate effect? Otherwise, a log out/ log in would be needed.

*If you log into the Lubuntu session*, Lubuntu, (including Lubuntu 13.10 (Saucy) uses **~/.config/openbox/lubuntu-rc.xml** 

If you login to the Openbox session, you'll need **~/.config/openbox/rc.xml**.

---

### Post by Matthew_Bird on 2014-03-25
Hey vasa, thanks for your reply!
I have ran** openbox --reconfigure. **Sorry, I should have mentioned that from the onset.

---

### Post by vasa1 on 2014-03-25
I notice from your image that you're on a netbook. Do you use the "Lubuntu Netbook" option at login time? I don't know how that works.

BTW, instead of 10000000000000%,  have you tried something below 100%? Does that also not make any difference?

If nothing you do in lubuntu-rc.xml makes any difference, it's possible that some other file is being read. I haven't come across any documentation or support for the Lubuntu Netbook session that may clarify matters.

I use a laptop and lubuntu-rc.xml works for me when I log into "Lubuntu session" in 13.10.

---

### Post by Matthew_Bird on 2014-03-25
Thanks for another reply, vasa! 

Unlike other linux distros I've seen, Lubuntu doesn't seem to give me any options at login. In any case, the xml file is in some sense affecting things, as the key bindings I've set up are doing *something *at least! But it must not be reading the file any more... Is there any chance it's reading a new file that has been affected by the xml I'm editing but can no longer be effected by it? It's a real mystery!

---

### Post by Matthew_Bird on 2014-03-25
OK, rather bizarre finding: if I delete the xml file (and reconfigure openbox), I lose all keybindings and the windows restore to default. But if I merely delete the section of the xml file that manages the window tiling key-bindings, they still work as they currently do... What...?

Further update: If I hold the maximise-right buttons down (so the command keeps processing), the area of the screen where the window should be moving flashes white in exactly the place where the xml file wants it to be, but the window moves to the crappy location I noted at the beginning. **It seems that something is *overruling *the openbox command, which is otherwise working.**

---

### Post by Rex Bouwense on 2014-03-25
> **Matthew_Bird said:**
>  Unlike other linux distros I've seen, Lubuntu doesn't seem to give me any options at login.
This really hasn't got anything to do with your main problem but Lubuntu does give you options at Log-in.  Next time you log go to the upper right hand corner of your log-in page and click the drop-down menu and you will find that you can log-in to Lubuntu, Lubuntu Notebook, OpenBox, and another one I think.  It has been a while.

---

### Post by Matthew_Bird on 2014-03-25
> **Rex Bouwense said:**
> This really hasn't got anything to do with your main problem but Lubuntu does give you options at Log-in.

You're absolutely right, I'm sorry!

---

### Post by vasa1 on 2014-03-25
> **Rex Bouwense said:**
> ...  It has been a while.
Hi Rex!
The list of options (plus some duds) is here: /usr/share/xsessions

```
$ ll
...
-rw-r--r--   1 root root   385 Apr 27  2013 Lubuntu.desktop
-rw-r--r--   1 root root   238 May  1  2013 Lubuntu-Netbook.desktop
-rw-r--r--   1 root root   175 May  1  2013 lubuntu-nexus7.desktop
-rw-r--r--   1 root root   210 May  1  2013 lxgames.desktop
-rw-r--r--   1 root root   198 Oct  9 02:53 openbox.desktop
-rw-r--r--   1 root root   202 Oct  9 02:53 openbox-gnome.desktop
-rw-r--r--   1 root root   189 Oct  9 02:53 openbox-kde.desktop
-rw-r--r--   1 root root   153 May  1  2013 qlubuntu.desktop
...
$ 

```

---

### Post by vasa1 on 2014-03-25
Hi, this may take us a while to figure but to start with, please 

[LIST]
[*]run **ls -l ~/.config/openbox** and post the contents here
[*]make a small change to _only_ **~/.config/openbox/lubuntu-rc.xml** that will produce a visible effect and tell us what exactly you've done
[*]once you're sure that **~/.config/openbox/lubuntu-rc.xml** is indeed the file that Openbox obeys, you may upload the file to pastebin (after installing pastebinit if necessary) so that people can take a look at it
[/LIST]

---

### Post by Matthew_Bird on 2014-03-26
Hey there! Thanks for your patience, vasa. 

> **vasa1 said:**
> 
run **ls -l ~/.config/openbox** and post the contents here
```
-rw-r--r-- 1 matt matt 30812 Mar 26 02:17 lubuntu-rc.xml
-rw-r--r-- 1 matt matt 30852 Mar 25 23:53 lubuntu-rc.xml~
```

> 
make a small change to _only_ **~/.config/openbox/lubuntu-rc.xml** that will produce a visible effect and tell us what exactly you've done


I deleted the keybinding for F11 which makes the window fullscreen, and it worked. To do this, I removed the following from **lubuntu-rc.xml**:

```
    <keybind key="F11">
      <action name="ToggleFullscreen"/>
    </keybind>
```

...and then ran openbox --reconfigure in the terminal. Pressing F11 after the reconfigure of openbox had no effect. Adding the above code back into the .xml file and reconfiguring openbox returned the F11 fullscreen functionality. 

As above, I should add that changing the parameters for the right-maximise stuff **does **have an effect: when I press the keyboard shortcut for right-maximise, a white square flashes on the screen at exactly the place the .xml file had configured the window to be, but then the window still moves to the wrong location. Editing the parameters in the .xml file **does **change the location and size of that white square. 

> upload the file to pastebin (after installing pastebinit if necessary) so that people can take a look at it



[Here's the pastebin link.]("http://pastebin.com/kYQiYrfu")

Thanks!

---

### Post by Rex Bouwense on 2014-03-26
Hey guys, does the information here help?
[http://openbox.org/wiki/Help:Actions](http://openbox.org/wiki/Help:Actions)

---

### Post by Matthew_Bird on 2014-03-26
> **Rex Bouwense said:**
> Hey guys, does the information here help?
[http://openbox.org/wiki/Help:Actions](http://openbox.org/wiki/Help:Actions)

Thanks for the link, Rex! I read the section on the command I'm using, and I'm pretty sure I'm using it correctly. 

Given that the area I want the window to move to flashes white when I press the keys, I think it must be something interfering with openbox, rather than a fault in openbox itself. Any thoughts?

---

### Post by Rex Bouwense on 2014-03-26
None at the present time.  I know how to install it and to make it do certain actions.  However, if it's broke or doesn't do what it is supposed to do then I have to bow to those with more geeky experience.  Sorry.

---

### Post by vasa1 on 2014-03-26
> **Matthew_Bird said:**
> ...
[Here's the pastebin link.]("http://pastebin.com/kYQiYrfu")

I've downloaded it and will go over it to see if I can spot any thing "different" but for now, I just saw this:

```
    <keybind key="W-Right">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>1/2</x>
        <y>0</y>
        <width>50%</width>
        <height>97%</height>
      </action>
    </keybind>
```
I don't know what **<x>1/2</x>** does. Could you clarify or check that?

[B]Edit: I just came across another keybind using the same keys ...
[/B]
    <keybind key="W-Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>-0</x><y>0</y><height>110%</height><width>50%</width></action>
    </keybind>
This is earlier on ... ~ lines 333-336.

I should mention that lubuntu-rc.xml at some point did **not** have the "tiling" keybinds but then they appeared. So do go over your code and remove  or comment out what is possibly interfering or just redundant. It's quite possible that the "parser" used by *openbox --reconfigure* does not pick up such things.

Also, please stay with conventional values, mostly integers and keep within 0-100%. Who knows how Openbox reacts to 110%, etc.

---

### Post by vasa1 on 2014-03-27
I think you can look at the original file which should be here: /usr/share/lubuntu/openbox/rc.xml.

Rename your existing ~/.config/openbox/lubuntu-rc.xml to something else temporarily and then copy over /usr/share/lubuntu/openbox/rc.xml and rename that from rc.xml to lubuntu-rc.xml. If your troubles go away, you have a starting point to sort things out. 

All the best!

---

### Post by vasa1 on 2014-03-27
> **vasa1 said:**
> ...
I should mention that lubuntu-rc.xml **at some point** did not have the "tiling" keybinds but then they appeared. ...

The tiling keybinds were first included in 13.04.

---

### Post by Matthew_Bird on 2014-03-27
> **vasa1 said:**
> 
[B]Edit: I just came across another keybind using the same keys ...
[/B]

[FONT=garamond][B]That's it!
[/B]I removed the first set of keybindings (the ones later in the file; see below code) and now my original keybindings work again! (Well, they don't work perfectly: setting the screen height to 100% doesn't make it fill the screen vertically, so it needs some adjustment).

The problem seems to have been caused by Lubuntu 13.10, which has apparently added the below code into the XML file. I wrote the *second *code that you found (the one earlier in the file), and did not write the following:
[/FONT]
```
[COLOR=#000000][FONT=Ubuntu Mono]    <keybind key="W-Right">[/FONT][/COLOR]      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>1/2</x>
        <y>0</y>
        <width>50%</width>
        <height>97%</height>
      </action> [COLOR=#000000][FONT=Ubuntu Mono]    </keybind>[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[SIZE=2][FONT=garamond]It must have been added when Lubuntu updated? It seems that the binding clash was causing my problem. 

Anyway, the problem is fixed now and my keybindings are working perfectly. Thanks for all your help, Vasa1 and Rex![/FONT][/SIZE][/FONT][/COLOR]

---

