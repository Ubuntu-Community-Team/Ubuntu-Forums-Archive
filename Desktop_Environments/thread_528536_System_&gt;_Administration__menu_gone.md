---
title: "System &gt; Administration  menu gone"
date: 2007-08-18
forum: Desktop Environments
---

### Post by DiFFeReNT on 2007-08-18
In the process of editing my menus via 'System > Preferences > Main Menu',  I think I accidentally dragged the entire 'System > Administration' folder outside the window, which apparently deleted it altogether.

How can I recover my 'System > Administration' folder with all the contents it contained before accidentally obliterated it?

Thanks,
DiFFeReNT

---

### Post by DiFFeReNT on 2007-08-18
Oh yeah, and this might be related - but probably not:

In my "system tray" (top right), my volume icon somehow got moved to the right side of the "logoff" button, and is usually to the left of the date/time.

In addition, my "trash" icon (bottom right) somehow got moved to the left of my two workspace squares.

I'm running Feisty.

Thanks again,
DiFFeReNT

---

### Post by neaeo on 2007-08-18
The per-user menu layout is stored in your HOME folder under .config/menus

so, to undo all your changes, open a terminal and enter:
cd && rm .config/menus/*

(This will remove ALL the changes you made however)

---

### Post by DiFFeReNT on 2007-08-18
Thanks for your reply.

Well, since I'd rather not remove ALL changes (which I assume includes short cuts for things like nVidia, WINE, and other important things), there must be a workaround.

In .config/menus/ the .menu docs are in XML or similar, and my settings.menu has this in it:

> <Menu>
	<Move>
		<Old>Administration</Old>
		<New>Administration/Administration</New>
	</Move>
	<Name>Desktop</Name>
	<MergeFile type="parent">/etc/xdg/menus/settings.menu</MergeFile>

Inside  /etc/xdg/menus/settings.menu  is:

>   <!-- System Settings -->
  <Menu>
    <Name>Administration</Name>
    <Directory>System-Settings.directory</Directory>
    <Include>
      <And>
        <Category>Settings</Category>
        <Category>System</Category>
      </And>
    </Include>
  </Menu>     <!-- End System Settings -->

  <Layout>
    <Menuname>Preferences</Menuname>
    <Menuname>Administration</Menuname>
  </Layout>

It looks like it should at least still be showing the Administration "folder"...
Anyways I'm lost....
Did it actually **completely** destroy all that information?

---

### Post by neaeo on 2007-08-18
This XML structure is a bit difficult to understand and it's nor so easy to edit it directly...
The information is defenitely not lost.
Did you make many changes to your settings menu? If not, I would suggest to just remove
the ~/.config/settings.menu

---

### Post by freeflyer57 on 2007-08-18
Sometimes when  I log into my account my icons move around. Sometimes they go back the next time I log in. But most of the times, they stay right where **THEY** really wanted to be. :-D

---

### Post by DiFFeReNT on 2007-08-18
I did not edit it. However, if anything I installed created shortcuts in the Settings/Preferences/Administration menus, will they disappear?

---

### Post by DiFFeReNT on 2007-08-18
> **freeflyer57 said:**
> Sometimes when  I log into my account my icons move around. Sometimes they go back the next time I log in. But most of the times, they stay right where **THEY** really wanted to be. :-D

Haha! Thanks for lightening the mood.
(This issue damaged the "perfect" experience with Ubuntu I've been having - this kind of stuff happens daily in Windows, so I felt spoiled, like I was on a winning streak - especially after I've finally almost finished configuring Ubuntu to become my new workstation)

---

### Post by neaeo on 2007-08-19
As long as you do not login as the super user (with sudo), you will never destroy
any system settings on a linux machine.

I tried to reproduce what you did: you probably dragged the Administration folder from the right onto the Administration folder on the left.
Here's what it gives in my ~/.config/menu/settings.menu:
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
        <Move>
                <Old>Administration</Old>
                <New>Administration/Administration</New>
        </Move>
        <Name>Desktop</Name>
        <MergeFile type="parent">/etc/xdg/menus/settings.menu</MergeFile>
        <Menu>
                <Name>Administration</Name>
                <DirectoryDir>/home/nea/.local/share/desktop-directories</DirectoryDir>
        </Menu>
</Menu>

I then just deleted the following part in ~/.config/menu/settings.menu, and the admin menu came back:

       <Move>
                <Old>Administration</Old>
                <New>Administration/Administration</New>
        </Move>

---

### Post by DiFFeReNT on 2007-08-19
Ah hah! I know <Move> looked suspicious!
Thanks a lot! :)

There should be something that prevents that from happening in the first place... anyways...
Thanks again

---

### Post by neaeo on 2007-08-20
You're welcome!

Yes, you're right: beeing able to drag a folder onto itself should not be allowed, since the result is not consistent. Perhaps you could file a bug in launchpad.

---

### Post by DiFFeReNT on 2007-08-20
> **neaeo said:**
> 
I tried to reproduce what you did: you probably dragged the Administration folder from the right onto the Administration folder on the left.


I'm filing the bug report now, but I forgot to respond directly to this.
I just reproduced what I did before, and here's all I did:

On the left column (Menus), at bottom under System:
- Click and hold Administration
- Move it just a little, like if you were going to drag it somewhere, but only a few pixels and still within the left column, and then let go of it.

Even if you move it back to where it was, it still disappears from that list and from the menu bar at the top of the screen.

---

### Post by neaeo on 2007-08-20
..that really looks like a bug.

---

