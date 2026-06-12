---
title: "HELP! Places &gt; Any Folder, Launches Disk Analyzer 14.04"
date: 2015-07-22
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-07-22
HELP!

Places > Any Folder, Launches Disk Usage Analyzer 14.04 from the Main Menu in Ubuntu Classic GNOME.  Has Nautilus lost its mind???

When I select Places > Computer, nautilus displays the correct folder view.

Also, nautilus run from the terminal runs correctly and there is no terminal output.

How do I recover from this? Reinstalled baobab didn't help.

Thanks, Hannibal

---

### Post by CantankRus on 2015-07-22
run 
```
gedit ~/.local/share/applications/mimeapps.list
```

search for ```
inode/directory
```

What does that line show?

---

### Post by coljohnhannibalsmith on 2015-07-23
There is no such line.  Below are the contents of the entire file:

[Added Associations]
application/x-shellscript=nautilus-autorun-software.desktop;

---

### Post by CantankRus on 2015-07-23
What does this command give you?
```
xdg-mime query default inode/directory
```

---

### Post by coljohnhannibalsmith on 2015-07-23
Just this:

sophie@sophie-Inspiron-1545:~$ xdg-mime query default inode/directory
nautilus-folder-handler.desktop
sophie@sophie-Inspiron-1545:~$

This problem started after I added some new software to the Main Menu.  I think it's possible that the menu editor clobbered the config file.

---

### Post by mc4man on 2015-07-25
To make clear - what session are you using? " Classic GNOME" would imply the gnome-shell extension that adds a 'Classic' session option.
Otherwise there is gnome-flashback which offers 2 session options - compiz or metacity

I'll guess you are using flashback, if so then try renaming ~/.config/menus/gnome-flashback-applications.menu to a .bak, log out/in & see if improved.
If so then read thru that file in a text editor & see what is wrong.. or just delete it & edit menus more carefully

---

### Post by coljohnhannibalsmith on 2015-07-25
Yes,

Thank you.  I am using Gnome Flashback Compiz.  I followed your advice, and I assumed as I'm sure you did that the system would create a new config file; however, this didn't happen.  I even tried rebooting and this didn't help.

BTW, here are the contents of the config file. It doesn't look complete:

```
<?xml version="1.0" ?>
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
    <Name>Applications</Name>
    <MergeFile type="parent">/etc/xdg/menus/gnome-flashback-applications.menu</MergeFile>
    <Menu>
        <Name>Accessories</Name>
        <Include>
            <Filename>gksu.desktop</Filename>
        </Include>
        <AppDir>/home/sophie/.local/share/applications</AppDir>
        <Include>
            <Filename>alacarte-made-2.desktop</Filename>
        </Include>
        <Layout>
            <Merge type="menus"/>
            <Filename>file-roller.desktop</Filename>
            <Filename>unity-deja-dup-panel.desktop</Filename>
            <Filename>bluetooth-sendto.desktop</Filename>
            <Filename>gcalctool.desktop</Filename>
            <Filename>gucharmap.desktop</Filename>
            <Filename>gnome-contacts.desktop</Filename>
            <Filename>gnome-disks.desktop</Filename>
            <Filename>nautilus.desktop</Filename>
            <Filename>gnome-font-viewer.desktop</Filename>
            <Filename>yelp.desktop</Filename>
            <Filename>alacarte.desktop</Filename>
            <Filename>apport-gtk.desktop</Filename>
            <Filename>gksu.desktop</Filename>
            <Filename>gnome-screenshot.desktop</Filename>
            <Filename>gnome-terminal.desktop</Filename>
            <Filename>gedit.desktop</Filename>
            <Filename>unity-datetime-panel.desktop</Filename>
            <Merge type="files"/>
        </Layout>
    </Menu>
    <Menu>
        <Name>Electronics</Name>
        <Include>
            <Filename>alacarte-made-1.desktop</Filename>
        </Include>
        <Layout>
            <Merge type="menus"/>
            <Filename>gerbv.desktop</Filename>
            <Merge type="files"/>
        </Layout>
    </Menu>
    <Menu>
        <Name>Other</Name>
        <Exclude>
            <Filename>alacarte-made.desktop</Filename>
        </Exclude>
        <AppDir>/home/sophie/.local/share/applications</AppDir>
    </Menu>
</Menu>
```

Here's something else I discovered.  I also tried checking an unchecked item in the main menu and when I opened it up again, it would still be unchecked.
To me this means that the menu editor itself is not writing to the config file.  Perhaps, this app is corrupt and needs to be reinstalled after renaming the 
original config file to .bak as I did in the first attempt.

Do you know what the correct name of this app is, so I can try to find it in Synaptic?

Hannibal

---

### Post by mc4man on 2015-07-25
It's called alacarte.
A new user 'gnome-flashback-applications.menu' would only be created after making some edit's, otherwise you'd be using the default <whatever>.menu file.
Is there anything else in that folder/ (~/.config/menus/
&
what's in ~/.local/share/applications folder
(as in 
ls ~/.local/share/applications
&
ls ~/.config/menus

---

### Post by coljohnhannibalsmith on 2015-07-25
sophie@sophie-Inspiron-1545:~$ ls ~/.local/share/applications
alacarte-made-1.desktop  kde4-amarok_containers.desktop
alacarte-made-2.desktop  mimeapps.list
alacarte-made.desktop    nautilus-folder-handler.desktop
deja-dup.desktop         rhythmbox-device.desktop
gksu.desktop
sophie@sophie-Inspiron-1545:~$

sophie@sophie-Inspiron-1545:~$ ls ~/.config/menus 
gnome-flashback-applications.menu
sophie@sophie-Inspiron-1545:~$ 

Thanks, Hannibal

---

### Post by mc4man on 2015-07-26
Well I'd try any of the below - 
Create a folder somewhere else like in Documents, move all those .desktops from .local/share/applications there, log out/in & see
or 
open all those .desktops in gedit & look for a suspect Exec= line, may need to arrow over in gedit to view some.. - 
```
gedit .local/share/applications/*.desktop
```
or  
```
cd .local/share/applications && grep -R baobab
```

---

### Post by coljohnhannibalsmith on 2015-07-26
No.  This is it:

sophie@sophie-Inspiron-1545:~$ ls ~/.config/menus
gnome-flashback-applications.menu
sophie@sophie-Inspiron-1545:~$ 

Thanks, Hannibal

The first method revealed only the menu entries I made; and there were no suspicious "Exec=" lines.

The second method yielded only:

sophie@sophie-Inspiron-1545:~$ cd .local/share/applications && grep -R baobab
alacarte-made-2.desktop~:Exec=baobab
alacarte-made-2.desktop:Exec=baobab
[EMAIL="sophie@sophie-Inspiron-1545:~/.local"]sophie@sophie-Inspiron-1545:~/.local[/EMAIL]/share/applications$

This is just the menu option I made to put baobab back in the accessories menu.  This was after I
discovered the problem with Disk Usage Analyzer being launched instead of Nautilus.  BTW, I did
reinstall alacarte during this iteration; however without complete removal the config files are left behind.
I could also completely remove alacarte in Synaptic which would remove the main menu and the config files,
wherever they may be hiding;  and then lauch Synaptic from a terminal and reinstall alacarte.  This would
be an extreme measure and could hose my OS if it doesn't work the first time.

BTW, It seems problematic that I can edit Applications in the main menu; but I can't edit Places.  There must be
a config file somewhere just for that menu.

Thanks, Hannibal

---

### Post by mc4man on 2015-07-26
2 things - 
if you created a new user account & logged into that account in a gnome session does Places work correctly?

If not then what is in  - 
```
gedit  /usr/share/applications/mimeinfo.cache
```
on the line inode/directory=

If a new user works then try removing nautilus-folder-handler.desktop from your .local/applications folder

---

### Post by coljohnhannibalsmith on 2015-07-26
> **mc4man said:**
> 2 things - 
if you created a new user account & logged into that account in a gnome session does Places work correctly?

If not then what is in  - 
```
gedit  /usr/share/applications/mimeinfo.cache
```
on the line inode/directory=

If a new user works then try removing nautilus-folder-handler.desktop from your .local/applications folder

1. Yup, Places works correctly in another user account.

2. inode/directory=baobab.desktop;nautilus.desktop;nautilus-folder-handler.desktop;

3. Yup, I placed it on the desktop and now Places works like a charm.

Can I get rid of this file now; or do I need to put it somewhere else?

Thanks for sticking it out!

Hannibal

---

### Post by mc4man on 2015-07-26
> **coljohnhannibalsmith said:**
> 1. Yup, Places works correctly in another user account.

2. inode/directory=baobab.desktop;nautilus.desktop;nautilus-folder-handler.desktop;

3. Yup, I placed it on the desktop and now Places works like a charm.

Can I get rid of this file now; or do I need to put it somewhere else.

Thanks for sticking it out!

Hannibal
Just delete it

---

### Post by oldefoxx on 2016-01-13
> **coljohnhannibalsmith said:**
> HELP!

Places > Any Folder, Launches Disk Usage Analyzer 14.04 from the Main Menu in Ubuntu Classic GNOME.  Has Nautilus lost its mind???

When I select Places > Computer, nautilus displays the correct folder view.

Also, nautilus run from the terminal runs correctly and there is no terminal output.

How do I recover from this? Reinstalled baobab didn't help.

Thanks, Hannibal

The problem was first detected in Ubuntu 13.04, as I discovered in a google search.  It is easily corrected, and this thread explains how:

[http://ubuntuforums.org/showthread.php?t=2308978]("http://ubuntuforums.org/showthread.php?t=2308978")

Searches here are only for this site's drives.  The problem and solution were on askubuntu.com.  Major search engines look at thousands of sites on an ongoing bases, so can be more effective in finding data sometimes.

---

