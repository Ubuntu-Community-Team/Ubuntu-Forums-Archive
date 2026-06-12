---
title: "Applications Menu Editor is going nuts"
date: 2006-01-09
forum: Desktop Environments
---

### Post by ruudiculus on 2006-01-09
Hi,

I've got a strange thing going on with my Gnome menu editor. I installed KDevelop (maybe Gnome doesn't like kde things in its menu: it worked for K3b though) and  program entries were made in the submenu of programming, which is obvious off course.

Here it comes: I wanted all of the KDevelop entries in one KDevelop submenu in the Programming menu instead of having seven separate KDevelop entries between Anjuta (Gnome likes Anjuta) and Bluefish. While creating a new entry I didn't realize that the Programming menu was not selected, so a new entry was placed in the main menu. Since then things I don't remember everything I did very well: I deleted the new entry, tried to get KDevelop  entries in one submenu under Programming and shuffled with some entries under the Programming menu, but the result was this:

The main menu OFFICE now can only be placed in a submenu, not in the main menu anymore (so now I have it under Debian: a main menu entry I normally don't use, but I need OpenOffice some way).  I can't get KDevelop entries in a submenu and I can't get my Office menu back in the main menulist.

I figured that there must be some kind of configuration file so I searched my system for a bit and I found this rather complicated looking file /home/ruud/.config/menus with the following content:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<AppDir>/home/ruud/.local/share/applications</AppDir>
	<Menu>
		<Name>Development</Name>
		<Include>
			<Filename>kde-kdevelop_scripting.desktop</Filename>
		</Include>
		<AppDir>/home/ruud/.local/share/applications</AppDir>
		<DirectoryDir>/home/ruud/.local/share/desktop-directories</DirectoryDir>
		<Include>
			<Filename>kde-kdevelop_ruby.desktop</Filename>
		</Include>
		<Layout>
			<Filename>anjuta.desktop</Filename>
			<Filename>bluefish.desktop</Filename>
			<Filename>devhelp.desktop</Filename>
			<Filename>glade-2.desktop</Filename>
			<Filename>kde-kdevassistant.desktop</Filename>
			<Filename>kde-kdevelop_c_cpp.desktop</Filename>
			<Filename>kde-kdevdesigner.desktop</Filename>
			<Filename>kde-kdevelop_kde_cpp.desktop</Filename>
			<Filename>Development-kdevelop3.desktop</Filename>
			<Filename>scite.desktop</Filename>
			<Filename>kde-kdevelop_scripting.desktop</Filename>
			<Filename>kde-kdevelop_ruby.desktop</Filename>
			<Menuname>KDevelop</Menuname>
			<Merge type="menus"/>
			<Merge type="files"/>
		</Layout>
	</Menu>
	<Menu>
		<Name>Internet</Name>
		<AppDir>/home/ruud/.local/share/applications</AppDir>
		<Include>
			<Filename>Airsnort.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<AppDir>/home/ruud/.local/share/applications</AppDir>
		<DirectoryDir>/home/ruud/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>System</Name>
		<AppDir>/home/ruud/.local/share/applications</AppDir>
	</Menu>
	<Move>
		<Old>Office</Old>
		<New>Development/Office</New>
	</Move>
	<Move>
		<Old>Development/Office</Old>
		<New>Office</New>
	</Move>
	<Menu>
		<Name>Graphics</Name>
	</Menu>
	<Move>
		<Old>Office</Old>
		<New>Graphics/Office</New>
	</Move>
	<Move>
		<Old>Graphics/Office</Old>
		<New>Office</New>
	</Move>
	<Menu>
		<Name>Debian</Name>
		<DirectoryDir>/home/ruud/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Move>
		<Old>Office</Old>
		<New>Debian/Office</New>
	</Move>
	<Move>
		<Old>Debian/Office</Old>
		<New>Office</New>
	</Move>
	<Move>
		<Old>Office</Old>
		<New>Debian/Office</New>
	</Move>
	<Move>
		<Old>Debian/Office</Old>
		<New>Office</New>
	</Move>
	<Move>
		<Old>Office</Old>
		<New>Debian/Office</New>
	</Move>
	<Move>
		<Old>Debian/Office</Old>
		<New>Office</New>
	</Move>
	<Move>
		<Old>Office</Old>
		<New>Debian/Office</New>
	</Move>
</Menu>

```

It looks to me as if this file only takes care of the non-default applications menu entries, but I have no idea of how to configure it so that my office is in the main menu list again.

On a second search in /home/ruud/.local/share I found some desktop configuration files which were also present in a seemingly incomplete list looking like this:
```
ruud@HP:~/.local/share$ ls -R
.:
applications  desktop-directories

./applications:
Airsnort.desktop  ethereal.desktop       fireglcontrol.desktop  gfloppy.desktop  mimeinfo.cache            xchat.desktop
amsn.desktop      evolution-2.4.desktop  gaim.desktop           kde              scite-usercustom.desktop

./applications/kde:
kdevelop_ruby.desktop

./desktop-directories:
Debian.directory  Development.directory  Office.directory

```

Seems to me that linux has configuration files for EVERYTHING, so I probably have bad luck trying to find the right (and easy) one for the applications menu.

Have you got any idea? Please help me out!

---

### Post by ruudiculus on 2006-01-11
I always like to reply to myself, because I know better than I do :???: 

Anyways I managed to create a KDevelop submenu entry now in Programming. I found out that drag 'n dropping the seven separate KDevelop entries from the programming menu (which has its contents presented ont he right if you select it) to the new KDevelop submenu can only be done by dragging from left-to-right, while the new submenu is also present among the seven Kdevelop entries.

Can you still follow me? I can't...

And if I remembered well the only way to enable the KDevelop submenu is to stand on it (in the list on the left) and add a new program entry. After that the Kdevelop menu is enabled and other existing entries can be drag 'n dropped the way I described above.

So, one problem solved: I've got the KDevelop submenu in Programming as I wanted, with the seven entries in it.

Second problem still present: my Office menu entry still can't be dragged and dropped. But hey...I'm thinking...I said the only way to drag 'n drop is from right-to-left...right? Let's try that!

Nope, doesn't work! Well I now have the Office main menu in a submenu of a new Main menu, and the entries are copied from the original Office main menu entry to this new one. Since the original Office entry can't be deleted it stays fixed (yet unselected) in the application menu editor (where ever you put it).

Strange that a programmer has enabled drag 'n dropping in such a way that it can only be used partly.

So only one question for this thread (which it seems like I'll answer myself someday) rests: is there another configuration file for editing the Gnome applications menu non-graphically???

Thanks in advance!

---

