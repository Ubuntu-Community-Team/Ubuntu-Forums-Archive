---
title: "Menu editor in XFCE (4.6 in 9.04)"
date: 2009-04-25
forum: General Help
---

### Post by Ambertone on 2009-04-25
Hi all, I've used XFCE in other distros and have been able to right click the main menu button and edit the contents. Add, delete, move, create new launchers etc. Xubuntu 9.04 with XFCE 4.6 does not seem to have this? (not meaning the text file at /etc/xdg/xubuntu/menu xxx.menu)

Does anyone know where the menu editor is hidden? All help appreciated.

Cheers

Rod

---

### Post by Brandon Williams on 2009-05-08
Unfortunately, the menu editor in xubuntu (Applications->Settings->Main Menu) doesn't appear to work. I haven't been able to figure out how to apply my changes such that they actually have an impact on the menu. In previous versions, the menu editor worked ... in 9.04, it doesn't. The new version of XFCE has moved in the direction of the freedesktop.org menu configuration standard, and this appears to have broken the menu editor.

I've been searching the forums looking for a solution, but I haven't come up with anything that doesn't involve making manual changes to /usr/share/applications. I will post an update here if I come across anything.

---

### Post by dLeon on 2009-05-08
Hello, Ambertone.
The tool you talking about is 'alacarte', it's available in main repos. It's installed by default with Ubuntu. Not sure if it's available in Ubuntu Jaunty now. I also use Xubuntu.
Cheers.

---

### Post by kanikilu on 2009-05-08
> **dLeon said:**
> Hello, Ambertone.
The tool you talking about is 'alacarte', it's available in main repos. It's installed by default with Ubuntu. Not sure if it's available in Ubuntu Jaunty now. I also use Xubuntu.
Cheers.

Are you sure that works in 4.6? From the Xubuntu blog:

> Unfortunately, no menu editor is included and, with menu merging not being supported yet, using an alternative menu editor like Alacarte won’t work either. It’s manually editing the files or making do with the menu as-is, for now.

---

### Post by Brandon Williams on 2009-05-08
Ok ... I figured out how to do it ...

There is still no menu editor that works, as far as I can tell, but here is how I went about creating my customized menu.

Step 1, customize the main menu.
[list]
[*]$ cp /etc/xdg/xubuntu/menus/xfce-applications.menu ~/.config/menus/
[*]edit ~/.config/menus/xfce-applications.menu, adding/removing/editing items as required for the layout you desire
[*]the Layout section describes the high-level menu layout
[*]if you want a new menu, add a Menu section, modeled after one of the others
[*]simply including a category makes it a lot easier to add new items to a menu without having to change other files
[*]for example, I changed the Layout and added a Favorites menu
```
    <Layout>
        <Menuname>Favorites</Menuname>
        <Separator/>
        <Menuname>Settings</Menuname>
        <Separator/>
        <Merge type="all"/>
        <Separator/>
        <Filename>gnome-app-install-xfce.desktop</Filename>
        <Filename>xubuntu-help.desktop</Filename>
        <Filename>xfce4-about-xfce.desktop</Filename>
        <Filename>xfce4-logout.desktop</Filename>
    </Layout>

    <Menu>
        <Name>Favorites</Name>
        <Directory>favorites.directory</Directory>
        <Include>
            <Category>Favorites</Category>
        </Include>
    </Menu>
```
[/list]

Step 2, add necessary menu specifications to ~/.local/share/desktop-directories for any new menus you added that don't have existing menu specifications in /usr/share/desktop-directories/. The menu specification provides the name and icon for your memory. Here's an example:
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Directory
Icon[en_US]=emblem-favorite
Name[en_US]=Favorites
Name=Favorites
Icon=emblem-favorite
```

Step 3, add/change/remove menu items. The easiest way to change or remove an item is to copy the .desktop files from /usr/share/applications/ for items that you want to modify, and then edit your copy of the file. In my example, where I wanted to create a favorites menu, I copied all the .desktop files over for the apps that I want to show up as favorites, and then added the string "Favorites;" to the end of each Categories line, so that the entries stay where they were _and_ show up in my favorities menu. If you want a menu item to disappear, add the line "Hidden=true" to the file. If you want to add a new menu item, copy an existing .desktop file and modify it to meet your needs.


Maybe someone else will point us at an easier method. In the mean time, this information about how to do it the hard way might be helpful to others.

---

### Post by dLeon on 2009-05-09
Glad you figure it out. I also do like you've done. I didn't mention that cause you ask for the tool.
By the way, I read from some threads around here that menu structure + desktop file in Ubuntu become not compliant to freedesktop based. I must check it more though.

---

### Post by Brandon Williams on 2009-05-09
> **dLeon said:**
> Glad you figure it out. I also do like you've done. I didn't mention that cause you ask for the tool.
By the way, I read from some threads around here that menu structure + desktop file in Ubuntu become not compliant to freedesktop based. I must check it more though.

You're right, the OP was looking for a tool ... I posted hoping that he'll be happy with any way at all (like I was).

FWIW ... alacarte and gmenu-simple-editor are both python based, and each has some elements of what is required for a tool for XFCE. gmenu-simple-edit can read any specified menu file and will allow you to enable/disable specific existing menu entries. alacarte actually has the capability to edit the menus, but it won't read an arbitrary menu file, and it won't use anything other than Applications and System as the high-level menu entries ... all new menus have to be submenus of one or the other of those. It shouldn't be too difficult to merge the two sets of functionality together. I may look into it at some point when I run out of other things to do :-)

---

### Post by dLeon on 2009-05-09
I C. Maybe not the first priority. Still it best to tell the noobs about it or it will freak them out to not know how to edit their menu in Xfce. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by psilofski on 2009-06-03
Hi, just installed ms office via wine (don't shoot me, slightly layout changed ".doc" application forms when opened and printed in openoffice will cause beauracracy issues) and it messed up the wine menu (it dissapeared and everything was left in "others")

Following the above examples, managed to understand how things work and restored the menu, but I can't create the "Programs" menu within "wine".

My code is (inside or not "wine" menu, not matter):

            <Menu>
                <Name>Programs</Name>
                <Directory>wine-Programs.directory</Directory>
                <Include>
                    <Category>Programs</Category>
                </Include>
            </Menu>    

Other things I added work fine, so it must be a problem with the file/category I refer above

Any suggestions to fix this? 
also, the initial problem could be a wine's bug or msoffice's fault?

---

### Post by mbuell on 2009-08-04
Regarding the categories - I think that xfce has a restricted set of categories, because of trying to comply with the freedesktop standards. 

See this page for a listing of available categories:
[http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

---

### Post by -wyrd- on 2010-09-25
Hi.

Thanks to this thread I now understand (to some degree) how to edit the applications menu. But instead of adding a new application to it, I'd like to add a new item which would run a small script I made. This was possible and fairly simple in hardy, but since installing lucid recently I can't find a way to do it at all. :(

At least now I know it has something to do with the xfce-applications.menu file, but not sure how exactly to edit this file to make it run the script. Any ideas?

---

### Post by LionelPutz on 2011-05-26
alacarte dependencies are huge - ridiculous for a menu editor.
 
Try LXMenuEditor (lxmed) - download from SourceForge.  Designed for LXDE but works well in other environments - Java based, freedesktop.org compliant and very lightweight. It should be standard in LXDE & XFCE.

---

### Post by DouglasAdams on 2011-06-02
[SIZE=2]is this still the case for xubuntu 11.04 please?

i.e.

a) manually editing the xml file

b) loading four billion libraries to run what should be a tiny app

c) loading a package that's not in the repositories
[/SIZE]

---

### Post by kjuergen on 2011-06-09
unfortunately it is..... Alacarte most likely will ruin other things for you and your menu will never look the way you want it and usually worse than original. Manual editing is a pain as some files are hidden somewhere and LXMenu isn't in the repository so I didn't install it.
Yikes, my KDE desktop in 1998 had a menu editor which worked just fine....... Unfortunately KDE went into the cellphone business and only provides eye-candy at the cost of productivity and resources so we are stuck with either XFCE or LXDE (haven't tried busybox nor Fluxbox yet).

Juergen

Couldn't resist and installed LXMenu Editor. No success either as it wants to redefine the categories. Must be extremely difficult to make an editor for teh menu. It surprises me that the XFCE desktop can generate a menu from the .desktop files and that it's so hard to make an editor for that.

---

### Post by DouglasAdams on 2011-06-10
cheers kjuergen

---

