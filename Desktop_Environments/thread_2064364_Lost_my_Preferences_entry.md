---
title: "Lost my Preferences entry"
date: 2012-09-29
forum: Desktop Environments
---

### Post by GeForce 9500GT on 2012-09-29
Hi everyone,

This morning is started my computer finding out that my Preferences entry is gone in the Menu. How can i get the Preferences entry back?

---

### Post by GeForce 9500GT on 2012-09-30
*bump*

---

### Post by Guilden_NL on 2012-09-30
There are a couple of ways to get it back: manual entries in *.desktop files, see here for examples: [http://wiki.lxde.org/en/Main_Menu]("http://wiki.lxde.org/en/Main_Menu")

Or.....I install LXMenu Editor on all of my systems as I run Lubuntu on everything.  Once installed, you can tweak your menus via GUI.  Note that it is written in Java, so if you have a really old system with low memory, it might be a problem, though I've never run into one.
  [http://lxmed.sourceforge.net]("http://lxmed.sourceforge.net")

---

### Post by GeForce 9500GT on 2012-10-01
> There are a couple of ways to get it back: manual entries in *.desktop files, see here for examples: [http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)
I'll try that after reading the wiki.

>  Or.....I install LXMenu Editor on all of my systems as I run Lubuntu on everything.  Once installed, you can tweak your menus via GUI.  Note that it is written in Java, so if you have a really old system with low memory, it might be a problem, though I've never run into one.
  [http://lxmed.sourceforge.net](http://lxmed.sourceforge.net)
With LXMED i can;t get the whole entry back. It is not that just 1 item is missing or what, but the compleet entry.

---

### Post by vasa1 on 2012-10-01
> **Guilden_NL said:**
> ...
Or.....I install LXMenu Editor on all of my systems as I run Lubuntu on everything.  Once installed, you can tweak your menus via GUI.  Note that it is written in Java, ...
Hi!
What about [MenuLibre]("http://www.smdavis.us/projects/menulibre/")? Would that be similar to LxMenu Editor? It's installable using Synaptic or the Ubuntu Software Center. It's not yet in the Lubuntu Software Center.)

---

### Post by GeForce 9500GT on 2012-10-01
Hee vasa1, i never knew that this tool existed. I'll try that out, see if i can get my Preferences entry back. I'm still in a trail-and-error mode with Lubuntu, testing one or two things. And sometimes **** happens :biggrin:

---

### Post by vasa1 on 2012-10-01
> **GeForce 9500GT said:**
> Hee vasa1, i never knew that this tool existed. I'll try that out, see if i can get my Preferences entry back. I'm still in a trail-and-error mode with Lubuntu, testing one or two things. And sometimes **** happens :biggrin:
But can't you remember what you were doing, even approximately, that could have caused it to disappear?

MenuLibre scored quite high in the recent apps showdown. I've installed it instead of alacarte.

Could you put up an image of what you see? (Like the one I posted in another of your threads.)

---

### Post by vasa1 on 2012-10-01
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=2064171](http://ubuntuforums.org/showthread.php?t=2064171)
especially [http://ubuntuforums.org/showpost.php?p=12271063&postcount=3](http://ubuntuforums.org/showpost.php?p=12271063&postcount=3)

---

### Post by GeForce 9500GT on 2012-10-01
> But can't you remember what you were doing, even approximately, that could have caused it to disappear?
No, i just noticed it this week that the whole Preferences entry was gone. Can't recall what i was doing and how this happend.
 
> MenuLibre scored quite high in the recent apps showdown. I've installed it instead of alacarte.
I have the experience that alacarte doesn't work properly with LXDE/Lubuntu. So i try MenuLibre then. Thanks for the hint!
 
> Could you put up an image of what you see? (Like the one I posted in another of your threads.)
Yup, only i can do it this evening. I'm at work right now.

---

### Post by vasa1 on 2012-10-01
I'm pasting the contents of my "lxde-applications.menu" below. You may compare it with yours if you think it could give you a hint.
```

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://standards.freedesktop.org/menu-spec/1.0/menu.dtd">

<Menu>
    <Name>Applications</Name>
    
    <DefaultAppDirs/>
    <DefaultDirectoryDirs/>
    <DefaultMergeDirs/>

<!-- Applications Menu -->
    <Menu>
        <Name>Accessories</Name>
        <Directory>lxde-utility.directory</Directory>
        <Include>
            <And>
                <Category>Utility</Category>
                <Not><Category>Accessibility</Category></Not>
                <Not><Category>System</Category></Not>
		<Not><Category>AudioVideo</Category></Not>
		<Not><Category>Audio</Category></Not>
		<Not><Category>Video</Category></Not>
            </And>
                <Or>
                    <Category>Core</Category>
                    <Category>Legacy</Category>
                </Or>
        </Include>
    </Menu>

    <Menu>
        <Name>Universal Access</Name>
        <Directory>lxde-utility-accessibility.directory</Directory>
        <Include>
            <And>
                <Category>Accessibility</Category>
                <Not><Category>Settings</Category></Not>
            </And>
        </Include>
    </Menu>

    <Menu>
        <Name>Development</Name>
        <Directory>lxde-development.directory</Directory>
        <Include>
            <And>
                <Category>Development</Category>
            </And>
            <Filename>emacs.desktop</Filename>
        </Include>
    </Menu>

    <Menu>
        <Name>Education</Name>
        <Directory>lxde-education.directory</Directory>
        <Include>
            <Or>
                <Category>Education</Category>
            </Or>
            <And>
                <Category>Science</Category>
                <Not><Category>Office</Category></Not>
            </And>
        </Include>
    </Menu> 

    <Menu>
        <Name>Games</Name>
        <Directory>lxde-game.directory</Directory>
        <Include>
            <Category>Game</Category>
        </Include>
    </Menu>

    <Menu>
        <Name>Graphics</Name>
        <Directory>lxde-graphics.directory</Directory>
        <Include>
            <And>
                <Category>Graphics</Category>
                <Not><Category>Utility</Category></Not>
            </And>
        </Include>
    </Menu>

    <Menu>
        <Name>Internet</Name>
        <Directory>lxde-network.directory</Directory>
        <Include>
            <Category>Network</Category>
        </Include>
    </Menu>

    <Menu>
        <Name>Multimedia</Name>
        <Directory>lxde-audio-video.directory</Directory>
        <Include>
            <Category>Audio</Category>
            <Category>Video</Category>
            <Category>AudioVideo</Category>
        </Include>
    </Menu>

    <Menu>
        <Name>Office</Name>
        <Directory>lxde-office.directory</Directory>
        <Include>
            <Category>Office</Category>
        </Include>
    </Menu>

    <Menu>
        <Name>Other</Name>
        <Directory>lxde-other.directory</Directory>
        <OnlyUnallocated/>
        <Include>
            <And/>
        </Include>
    </Menu>

<!-- Administration Menu, to include in Layout section -->
    <Menu>
        <Name>Administration</Name>
        <Directory>lxde-system-tools.directory</Directory>
        <Include>
            <And>
                <Category>Settings</Category>
                <Category>System</Category>
            </And>
            <Or>
                <Category>System</Category>
            </Or>
        </Include>
    </Menu>

<!-- Preferences Menu, to include in Layout section -->
    <Menu>
        <Name>DesktopSettings</Name>
        <Directory>lxde-settings.directory</Directory>
        <Include>
            <And>
                <Category>Settings</Category>
                <Not>
                    <Or>
                        <Category>System</Category>
                    </Or>
                </Not>
            </And>
        </Include>
    </Menu>

<!-- General layout of the whole menu -->
    <Layout>
        <Menuname>Settings</Menuname>
        <Separator/>
        <Merge type="all"/>
        <Separator/>
        <Menuname>Administration</Menuname>
        <Menuname>DesktopSettings</Menuname>
    </Layout>

</Menu>

```

---

### Post by GeForce 9500GT on 2012-10-02
I found the troublestarter! It was K3B which i installed. After removing K3B the entry came back but it also messed up my whole system in such way that i had to re-install Lubuntu...

---

