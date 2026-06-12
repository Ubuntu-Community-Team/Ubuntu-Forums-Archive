---
title: "Obozrenie: simple game server browser for Linux"
date: 2015-09-23
forum: Gaming &amp; Leisure
---

### Post by Mi*6d@# on 2015-09-23
[img]https://cdn.rawgit.com/obozrenie/obozrenie/master/assets/icons/hicolor/scalable/apps/obozrenie.svg[/img]

[HR][/HR]
[size=5]**Simple and easy to use game browser**[/size]

[size=4]**[GitHub](https://github.com/obozrenie/obozrenie)** | **[Chat](https://gitter.im/obozrenie/obozrenie)** | **[Arch Linux AUR](https://aur.archlinux.org/packages/obozrenie-git)**[/size]

[[img]https://img.shields.io/badge/gitter-%23obozrenie%2Fobozrenie-blue.svg[/img]](https://gitter.im/obozrenie/obozrenie?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) [[img]https://img.shields.io/badge/license-GPL-brightgreen.svg[/img]](https://gnu.org/licenses/gpl.html) [[img]https://img.shields.io/travis/obozrenie/obozrenie.svg[/img]](https://travis-ci.org/obozrenie/obozrenie) [[img]https://img.shields.io/codecov/c/github/obozrenie/obozrenie.svg[/img]](https://codecov.io/github/obozrenie/obozrenie)


Hey everyone.

I am developing a new game server browser written in [PyGObject]("https://wiki.gnome.org/action/show/Projects/PyGObject") (GTK+ 3). It provides you with ability to view information about and connect to game servers in a convenient fashion. It is your one stop shop for online multiplayer and replacement for ingame lobbies.

**Available features:**
* Simple, uncluttered one-window interface.
* Support for around **30** titles, primarily id Tech and Source engine games.
* Fast stat engine (QStat is used for the majority of games).
* Comprehensive information about each and every game server, up to player list (when possible).
* Filtering support.
* Connecting to selected server straight from browser window, taking you straight to action.
* Active development and support
* ...much more to come, improvements on a daily basis ;)

Originally, I used to contribute to [XQF Game Server Browser]("https://github.com/XQF/xqf"), however its rotten codebase (30+ k lines of GTK1 (!!!) code) made me start writing my own thing. Obozrenie is less than 1.5k lines of Python total now.

Patches and suggestions are welcome :D

**Screenshot:**
[IMG]https://raw.githubusercontent.com/obozrenie/obozrenie/master/screenshot.png[/IMG]

---

### Post by Mi*6d@# on 2015-09-27
Added server filtering and other cool stuff in a megacommit yesterday:
[https://github.com/obozrenie/obozrenie/commit/20e986ac3fd6168573a4dbd1c81d300769b1f344](https://github.com/obozrenie/obozrenie/commit/20e986ac3fd6168573a4dbd1c81d300769b1f344)

---

### Post by Portaro on 2015-09-27
Amazing Idea.

I have Lubuntu 14.04 but I have problems to launch it ->

~/obozeniebrowser/obozrenie-master$ sh obozrenie-gtk
Traceback (most recent call last):
  File "/usr/lib/python3.4/runpy.py", line 170, in _run_module_as_main
    "__main__", mod_spec)
  File "/usr/lib/python3.4/runpy.py", line 85, in _run_code
    exec(code, run_globals)
  File "/home/joao/obozeniebrowser/obozrenie-master/obozrenie/gtk.py", line 32, in <module>
    import obozrenie.helpers as helpers
  File "/home/joao/obozeniebrowser/obozrenie-master/obozrenie/helpers.py", line 24, in <module>
    import pytoml
ImportError: No module named 'pytoml'


Another curiosity by me - there are servers of warzone2100 on the program?

---

### Post by Mi*6d@# on 2015-09-27
> **Portaro said:**
> 
I have Lubuntu 14.04 but I have problems to launch it ->

~/obozeniebrowser/obozrenie-master$ sh obozrenie-gtk
Traceback (most recent call last):
  File "/usr/lib/python3.4/runpy.py", line 170, in _run_module_as_main
    "__main__", mod_spec)
  File "/usr/lib/python3.4/runpy.py", line 85, in _run_code
    exec(code, run_globals)
  File "/home/joao/obozeniebrowser/obozrenie-master/obozrenie/gtk.py", line 32, in <module>
    import obozrenie.helpers as helpers
  File "/home/joao/obozeniebrowser/obozrenie-master/obozrenie/helpers.py", line 24, in <module>
    import pytoml
ImportError: No module named 'pytoml'


Hi,

You need to get all required dependencies to use Obozrenie. See [here](https://github.com/obozrenie/obozrenie#required)

> **Portaro said:**
> Another curiosity by me - there are servers of warzone2100 on the program?
Not yet but I'll look into it.

---

### Post by Portaro on 2015-09-28
When I clonning to the same path I have some problems-
> joao@P4V88:~/obozeniebrowser/obozrenie-master$ git clone [https://wiki.gnome.org/Projects/PyGObjectCloning](https://wiki.gnome.org/Projects/PyGObjectCloning) into 'PyGObject'...
fatal: unable to access 'https://wiki.gnome.org/Projects/PyGObject/': gnutls_handshake() warning: The server name sent was not recognized
joao@P4V88:~/obozeniebrowser/obozrenie-master$ git clone [http://crummy.com/software/BeautifulSoup](http://crummy.com/software/BeautifulSoup)
Cloning into 'BeautifulSoup'...
fatal: repository 'http://www.crummy.com/software/BeautifulSoup/' not found

When I try to launch I have a gtk fault -
> ** (gtk.py:25485): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-CLXMPDyhII: Ligação recusadaCore/Core: PyGeoIP not found. Disabling geolocation.


(gtk.py:25485): Gtk-WARNING **: Unknown property: GtkGrid.margin-start


(gtk.py:25485): Gtk-WARNING **: Unknown property: GtkGrid.margin-end


(gtk.py:25485): Gtk-WARNING **: Unknown property: GtkEntry.max-width-chars


(gtk.py:25485): Gtk-WARNING **: Unknown property: GtkScrolledWindow.margin-end


(gtk.py:25485): Gtk-WARNING **: Unknown property: GtkGrid.margin-start


(gtk.py:25485): Gtk-WARNING **: Unknown property: GtkGrid.margin-end
-------------------------------------------
UI/GTK+: Obozrenie is starting 
-------------------------------------------
''


(gtk.py:25485): Gtk-CRITICAL **: gtk_application_get_app_menu: assertion 'GTK_IS_APPLICATION (application)' failed


(gtk.py:25485): Gtk-CRITICAL **: gtk_application_get_menubar: assertion 'GTK_IS_APPLICATION (application)' failed
-------------------------------------------
UI/GTK+: Initialization failed. Aborting. 
 -------------------------------------------




Thanks for your efforts I hope that this can help others if want uses the tool.

---

### Post by Mi*6d@# on 2015-09-28
> **Portaro said:**
> When I clonning to the same path

You can't do that.

> **Portaro said:**
> When I try to launch I have a gtk fault

Make sure that your GTK+ version is 3.10 or higher

---

### Post by Mi*6d@# on 2015-10-07
Now with Minetest support too!
[https://github.com/obozrenie/obozrenie/commit/dd0d42a96acb7738670b8fc7ad69f1c602379b1d](https://github.com/obozrenie/obozrenie/commit/dd0d42a96acb7738670b8fc7ad69f1c602379b1d)

---

### Post by Mi*6d@# on 2015-11-14
Posted a new logo. Obozrenie is more or less feature complete; currently working on tests and fixing subtle bugs.

---

