---
title: "How to edit/change main menu in Ubuntu 9.10?"
date: 2010-04-01
forum: Desktop Environments
---

### Post by vickoxy on 2010-04-01
Hi, i am trying to remove two folders/submenus from my main menu (Orte and System). But i can not do it with gui menu editor. Anyone knows where can i find menu config file to remove those places/submenus?

Thanks

---

### Post by vickoxy on 2010-04-01
Bump

---

### Post by oldos2er on 2010-04-01
Right-click on the menu icon, Edit Menus; or ```
alacarte
```

---

### Post by vickoxy on 2010-04-02
> **oldos2er said:**
> Right-click on the menu icon, Edit Menus; or ```
alacarte
```

I wish it was so simple. These items i want  to remove (orte/system) are not listed in alacarte:

---

### Post by vickoxy on 2010-04-02
Bump

---

### Post by Gömböc on 2010-04-02
The config for your menus should live at

/home/[username]/.config/menus

Replace [username] with your user name.

If you don't see the .config folder in Nautilus, press Control + H to show hidden files/folders.

---

### Post by vickoxy on 2010-04-02
> **Gömböc said:**
> The config for your menus should live at

/home/[username]/.config/menus

Replace [username] with your user name.

If you don't see the .config folder in Nautilus, press Control + H to show hidden files/folders.

I have there lot of app menus. The first one is applications.menu, but i am not sure what to delete to remove orte (places)/system entries:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<AppDir>/home/mini/.local/share/applications</AppDir>
	<DefaultLayout inline="false"/>
	<Menu>
		<Name>alacarte-made-2</Name>
		<Directory>alacarte-made-2.directory</Directory>
		<Include>
			<Filename>Aktualisierungsverwaltung.desktop</Filename>
		</Include>
		<Include>
			<Filename>Anmeldebildschirm.desktop</Filename>
		</Include>
		<Include>
			<Filename>Benutzer und Gruppen.desktop</Filename>
		</Include>
		<Include>
			<Filename>Datum und Uhrzeit.desktop</Filename>
		</Include>
		<Include>
			<Filename>Drucken.desktop</Filename>
		</Include>
		<Include>
			<Filename>Hardware-Treiber.desktop</Filename>
		</Include>
		<Include>
			<Filename>Laufwerksverwaltung.desktop</Filename>
		</Include>
		<Include>
			<Filename>Multiple Screens.desktop</Filename>
		</Include>
		<Include>
			<Filename>Netzwerkdiagnose.desktop</Filename>
		</Include>
		<Include>
			<Filename>Rechner-Hausmeister.desktop</Filename>
		</Include>
		<Include>
			<Filename>Software-Paketquellen.desktop</Filename>
		</Include>
		<Include>
			<Filename>Sprachunterstützung.desktop</Filename>
		</Include>
		<Include>
			<Filename>Synaptic-Paketverwaltung.desktop</Filename>
		</Include>
		<Include>
			<Filename>Systemprotokollbetrachter-1.desktop</Filename>
		</Include>
		<Include>
			<Filename>Systemtest.desktop</Filename>
		</Include>
		<Include>
			<Filename>Systemüberwachung.desktop</Filename>
		</Include>
		<Include>
			<Filename>USB-Startmedien-Ersteller.desktop</Filename>
		</Include>
		<Include>
			<Filename>Software-Center.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<Include>
			<Filename>Systemprotokollbetrachter.desktop</Filename>
		</Include>
		<Include>
			<Filename>CompizConfig Einstellungs-Manager.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Graphics</Name>
		<AppDir>/home/mini/.local/share/applications</AppDir>
		<Exclude>
			<Filename>evince.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<Include>
			<Filename>Dokumentenbetrachter.desktop</Filename>
		</Include>
	</Menu>
	<Exclude>
		<Filename>ubuntu-software-center.desktop</Filename>
	</Exclude>
	<Layout>
		<Merge type="menus"/>
		<Menuname>Universal Access</Menuname>
		<Menuname>Education</Menuname>
		<Menuname>Office</Menuname>
		<Menuname>Debian</Menuname>
		<Menuname>Development</Menuname>
		<Menuname>Graphics</Menuname>
		<Menuname>Internet</Menuname>
		<Menuname>Games</Menuname>
		<Menuname>Multimedia</Menuname>
		<Menuname>Science</Menuname>
		<Menuname>Accessories</Menuname>
		<Separator/>
		<Menuname>System</Menuname>
		<Menuname>Other</Menuname>
		<Menuname>alacarte-made-2</Menuname>
		<Filename>ubuntu-software-center.desktop</Filename>
		<Separator/>
		<Merge type="files"/>
	</Layout>
</Menu>
```

Thanks

---

### Post by Gömböc on 2010-04-02
Ah! I didn't realise that Orte = Places. To remove items from Places, open a Nautilus window, then select Bookmarks > Edit Bookmarks. Select the appropriate entry from the list on the left, then click Remove.

As for your System entries -- what exactly do you want to remove from the System menu?

---

### Post by vickoxy on 2010-04-03
Thanks for answer. Well in System i have only three entries (see pict) that i really do not need...

Thanks

---

### Post by Gömböc on 2010-04-03
I've learnt something new. You'll need to do this as super-user, so open up a terminal window, then type "gksu nautilus" and enter your root password.

Then go to /usr/share/applications. There you should see the three items that you want to delete (amongst many others). On my system they are called "About GNOME", "About Ubuntu" and "Help". Just right-click on each one and select "Move to the Deleted Items folder". They will instantly be deleted from your System menu: there's no need to reboot.

If you change your mind and want the items back, you'll find them in /root/.local/share/Trash/files.

---

### Post by vickoxy on 2010-04-03
Thanks for answer-well, that way i am to delete these programs-so, there is no way just to remove them from menu? Not to delete?

---

### Post by Gömböc on 2010-04-03
These files are not the programs themselves: they are just text configuration files. You can see the contents if you drag them into a gedit/Text Editor window:

gnome-about.desktop
==============
[Desktop Entry]
Name=About GNOME
Comment=Learn more about GNOME
Exec=gnome-about
Icon=gnome-logo-icon-transparent
Terminal=false
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-desktop
X-GNOME-Bugzilla-Component=gnome-about
X-GNOME-Bugzilla-Version=2.28.1
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-desktop-2.0

ubuntu-abount.desktop
===============
[Desktop Entry]
Encoding=UTF-8
Name=About Ubuntu
Comment=Learn more about Ubuntu
Exec=yelp ghelp:about-ubuntu
Icon=distributor-logo
Terminal=false
Type=Application
Categories=GNOME;Application;Core;
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-panel-2.0

yelp.desktop
========
[Desktop Entry]
Name=Help
Comment=Get help with Ubuntu
OnlyShowIn=GNOME;
Exec=yelp
Icon=help-browser
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;GTK;Core;Documentation;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=Yelp
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.28.0
X-Ubuntu-Gettext-Domain=yelp


Note that there is nothing in these files that defines that they should each appear in the System menu. So I suppose there must be some other file or menu structure that defines that they should go in System: I just don't know where that is.

Does anyone else know? If not, there's no need to delete the files: you could just move them to some other folder.

---

### Post by oldos2er on 2010-04-03
> **Gömböc said:**
> I've learnt something new. You'll need to do this as super-user, so open up a terminal window, then type "sudo nautilus" and enter your root password.


 Should be **gksu nautilus**

 You'd think there'd be a way to do this with gconf-editor (maybe there is, I don't know), but this is one thing I don't like in Gnome; pockets of unconfigurability.

---

### Post by Gömböc on 2010-04-03
> **oldos2er said:**
> Should be **gksu nautilus**

 You'd think there'd be a way to do this with gconf-editor (maybe there is, I don't know), but this is one thing I don't like in Gnome; pockets of unconfigurability.

Thanks Ann. I've amended the original post to use gksu. For all I know, this could be done with gconf-editor (which I have little experience of using). I don't claim to be an expert in Gnome configuration -- just thought I'd have a stab at helping.

---

### Post by oldos2er on 2010-04-03
I need an 'Idiot's Guide to gconf-editor'.  :)

---

