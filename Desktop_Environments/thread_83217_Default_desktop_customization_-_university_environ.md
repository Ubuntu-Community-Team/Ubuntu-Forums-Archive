---
title: "Default desktop customization - university environment"
date: 2005-10-28
forum: Desktop Environments
---

### Post by grendel on 2005-10-28
Hey folks,
  First of all, I have read the thread at [http://ubuntuforums.org/showthread.php?t=67831](http://ubuntuforums.org/showthread.php?t=67831) and I'm aware of the Sabayon existence but, alas, what I need to do goes a bit beyond what Saybaon can do for me (as far as I can see). Also, feel free to redirect me to the correct forum for this kind of question if I missed to post it in the correct one.
  Some background information is in order, I guess. The project I'm going to work on is deploying at least 75 Ubuntu desktops in a University environment, for both the students (labs, library) and the administration. Bypassing the details not related to my question, the student-accessible desktops need to meet some requirements. First of all, the students will be authenticated from an ActiveDirectory Windows server, so no user accounts will be local to the desktop machines. Second of all, there will be a Debian-based fileserver using Samba to export individual shares for each student. Third of all, there will be a Windows Terminal server accessible to the students, so that they can work with some Microsoft Windows-based applications which are not supported by Crossover Office. 
Ubuntu, of course, contains all the components to implement that and this is not the problem or question I'm writing here about. My question is about the possibility to customize the default GNOME desktop after the user logs in for the first time (PAM will take care of creating the user home directory on the first login, which will set up most of the stuff I need) - namely, I need to put a volume icon pointing to the user's individual share on the Samba server on their desktop. The icon/volume link needs to be set up in the way that the user just clicks it and gets prompted just for the share password (it would be ideal if Nautilus could reuse the password the user logged in with, but I don't think it's possible). The other icon I need to put on the desktop (or in the panel) is one to launch the Terminal Server Client with the appropriate configuration, also customized for the user, but I guess that one is easier, since I can just drop in a .desktop file in the Desktop directory of the user's home dir and generate the Terminal Server Client's config on the first login.
Phew, after this long intro, finally the question - is there a way to programmatically create a Nautilus volume icon for the purpose described above? I googled for information about it for a while, but found no help there. Any pointers/hints will be greately appreciated (I'm a coder, so API documentation/samples are perfectly fine and sufficient)

---

### Post by kamstrup on 2005-11-01
Can't you just create a .desktop file with some script and put it in ~/Desktop? If PAM is already running setup scripts for the user, this should just amount to making PAM execute a sed-script or something... 

```
[Desktop Entry]
Name=Home
Encoding=UTF-8
Type=Link
Icon=stock_directory_server
URL=ftp://skimdk@ftp.skim.dk/httpdocs/
``` 
Save as ~/Desktop/foobar.desktop. Well, for some reason the icon isn't working for me, but hey!

Or have I missed something?

---

### Post by grendel on 2005-11-01
[QUOTE=kamstrup]Can't you just create a .desktop file with some script and put it in ~/Desktop? If PAM is already running setup scripts for the user, this should just amount to making PAM execute a sed-script or something... 

```
[Desktop Entry]
Name=Home
Encoding=UTF-8
Type=Link
Icon=stock_directory_server
URL=ftp://skimdk@ftp.skim.dk/httpdocs/
``` 
Save as ~/Desktop/foobar.desktop. Well, for some reason the icon isn't working for me, but hey!

Or have I missed something?[/QUOTE]
Yes, the solution you present is fine - it works, but I would like to do the same what Nautilus does for remote filesystems. To see what I mean, go Places->Connect To Server; then choose any connection type (e.g. Public FTP) and configure appropriately. An icon will appear on the desktop - right-click on it and note it has the 'Unmount Volume' option. Clicking on it initiates the connection to the shared folder within Nautilus. Further note that there is no .desktop file in ~/Desktop for the connection. Then visit ~/.nautilus/metafiles/ - you'll find an x-nautilus-desktop:%2F%2F%2F.xml file there which will contain a reference to "yourconnection.volume", like this
```

<?xml version="1.0"?>
<directory><file name="Test%20Windows%20Share.volume" timesta
mp="1130884122" icon_position="64,222"/></directory>

```
There will be a separate instance of the <file/> tag for each icon on the desktop.
*[10 minutes later]*
Hehe, while typing this response I have found where the configuration files are, although it seems that I'm still missing a piece of the puzzle:

Nautilus stores the mounted (connected) volumes information for gnome-fs locations in the gconf database. The entries are numbered starting from 1 and  can be found in ~/.gconf/desktop/connected_servers/X/%gconf.xml, where X is the connection number. The contents of %gconf.xml is as follows (for an SMB) share:
```

<?xml version="1.0"?>
<gconf>
        <entry name="uri" mtime="1130884122" type="string">
                <stringvalue>smb://testdomain;testuser@testserver/test</stringvalue>
        </entry>
        <entry name="display_name" mtime="1130884122" type="string">
                <stringvalue>Test Windows Share</stringvalue>
        </entry>
        <entry name="icon" mtime="1130884122" type="string">
                <stringvalue>gnome-fs-smb</stringvalue>
        </entry>
</gconf>

```
So, in theory it would be enough to add the entries and nautilus should create the icon on the desktop. Alas, when I did just that - created the files/directories described above for a user - I can't see the icon after logging in. There must be something else that needs to be done in order for Nautilus to notice the "mounted" volume.

---

### Post by kamstrup on 2005-11-02
> right-click on it and note it has the 'Unmount Volume' option. Is this really a desireable behavior? Actually I think I would use a .desktop file and make it read-only, to make sure users does not cut them self off from the world.

> So, in theory it would be enough to add the entries and nautilus should create the icon on the desktop. Alas, when I did just that - created the files/directories described above for a user
How are you installing that in gconf? Just copying the file to an appropriate place or are you setting gconf keys with some script?

If you create a <favorite script language>-script (Python recommended) that creates the keys by talking to gconf in a correct way, it still does not work? This is probably the correct way...

A more hackish but somewhat more direct is to use gnomevfs to write .volume files in network://...Unfortunatly the gnomevfs module for Python is vastly undocumented. I don't know if network:/// is writable though

Here's a sample Python session... If you dig Python?

```
>>> import gnomevfs
>>> d = gnomevfs.open_directory ("network://")
>>> for f in d:
...     dir (f)
...     break
... 
['__class__', '__delattr__', '__doc__', '__getattribute__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', 
'__repr__', '__setattr__', '__str__', 'atime', 'block_count', 'ctime', 'device', 'flags', 'gid', 'inode', 'io_block_size', 'li
nk_count', 'mime_type', 'mtime', 'name', 'permissions', 'size', 'symlink_name', 'type', 'uid', 'valid_fields']
>>> d = gnomevfs.open_directory ("network://")
>>> for f in d:
...     print f.name, type
... 
smblink-root <type 'type'>
volume-vfsmail <type 'type'>
volume-public_html <type 'type'>
volume-gtunnel <type 'type'>
volume-ftp.skim.dk <type 'type'>
>>> print gnomevfs.read_entire_file ("network:///volume-vfsmail")
[Desktop Entry]
Encoding=UTF-8
Name=vfsmail
Type=FSDevice
Icon=gnome-fs-ssh
URL=sftp://kamstrup@shell.sourceforge.net/home/groups/v/vf/vfsmail/htdocs
X-Gnome-Volume=15

>>> 
```

A completely different approach that should work to is simply to dig into the Nautilus code and try to copy the Nautilus way of doing it...

Well good luck anyway ;-P

---

### Post by kamstrup on 2005-11-03
Just thinking maybe gconftool-2 is the tool you are looking for. It's a command line tool to set keys in gconf... Or maybe you are already using it?

Cheers

---

### Post by grendel on 2005-11-03
[QUOTE=kamstrup]Is this really a desireable behavior? Actually I think I would use a .desktop file and make it read-only, to make sure users does not cut them self off from the world.
[/QUOTE]
My impression is that the .desktop files are easier to delete - they do physically exist in the ~/Desktop folder - any user with some level of *nix experience can change the permissions or and delete the file (unless I chown both the ~Desktop and the file to a different user, of course - but that's rather not desirable. I guess I could also use the ext3/reiserfs/xfs special flags to make the file readonly, though)

> 
How are you installing that in gconf? Just copying the file to an appropriate place or are you setting gconf keys with some script?

The theory is that I would do it from within the PAM module that sets up the user environment on the first login, so the only option for me is to use direct filesystem write, since I cannot count on gconf running by the time user is being authenticated. Also, my impression was that gconf monitors the ~/.gconf directory for changes? Even if it wouldn't be monitoring the directory it should read the ~/.gconf contents, I guess. Perhaps the problem is that the connected_servers key contents is not defined in any schema since it's dynamic, so it must be done through gconfd as you say...

> 
If you create a <favorite script language>-script (Python recommended) that creates the keys by talking to gconf in a correct way, it still does not work? This is probably the correct way...

You're definitely right, but see above :)

> 
A more hackish but somewhat more direct is to use gnomevfs to write .volume files in network://...Unfortunatly the gnomevfs module for Python is vastly undocumented. I don't know if network:/// is writable though

Here's a sample Python session... If you dig Python?

Yep, I do know Python. Using gnomevfs sounds like a good idea, but the question is - will it work from within the PAM module (I'm guessing not, will have to test it at some point)

> 
A completely different approach that should work to is simply to dig into the Nautilus code and try to copy the Nautilus way of doing it...

Yeah, been there already - all I could find is a call to gnome_vfs_connect_to_server API in nautilus-connect-server-dialog.c/connect_to_server(), but I haven't investigated it further yet... :)

> 
Well good luck anyway ;-P
Thanks :), luckily I have some time to dig that... :)

---

### Post by grendel on 2005-11-03
[QUOTE=kamstrup]Just thinking maybe gconftool-2 is the tool you are looking for. It's a command line tool to set keys in gconf... Or maybe you are already using it?
[/QUOTE]
I don't think I will be able to use it - it requires the gconfd to be running, and my code would have to run from within a PAM module - that is before the user is fully authenticated/authorized.

---

### Post by kamstrup on 2005-11-03
Ok, my last idea... I see your point(s) regarding the previous.

Is it possible to to make gnome-session run some script upon login -- without a gconf registry? If so a simple ~/.first_gnome_session script that removes itself would prolly cut it. If the script is prioritized as the very last to be run on login, it should have gconfd available no?

But I don't know how to install such a script... The brute force way would be to write a .xinitrc yourself, that way you could manually start gconfd before you do your magic...

Well. Just a thought.
Cheers

---

### Post by grendel on 2005-11-04
[QUOTE=kamstrup]Ok, my last idea... I see your point(s) regarding the previous.

Is it possible to to make gnome-session run some script upon login -- without a gconf registry? If so a simple ~/.first_gnome_session script that removes itself would prolly cut it. If the script is prioritized as the very last to be run on login, it should have gconfd available no?
[/QUOTE]
Yep, gnome-session runs ~/.gnomerc if it's present. It would be possible to add a one-time code to do the setup there. It would be ideal if gnome had a global equivalent to ~/.gnomerc (with the knowledge of the user logging in), will have to investigate that. I also thought about adding a program to the default gnome-session, that would either a) run once, add the necessary stuff and then remove itself from the session, or b) run every time the user logs in to make sure the necessary stuff is always recreated should it have been deleted.
Thanks for your input :) - as always, when talking to somebody about a problem, many ideas appear, thanks a million :)

---

### Post by kamstrup on 2005-11-04
You're welcome. If you find a good solution be sure to post back so that others may benefit from you experiences.

Cheers!

---

