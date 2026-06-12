---
title: "Kickoff's Application menu is empty"
date: 2011-12-22
forum: Desktop Environments
---

### Post by manolomanolo on 2011-12-22
Hi to all.

The Application menu in Kickoff (KDE's application launcer) suddenly turned empty.
I see I've even lost the file association. For example, double clicking on a PDF or a text document no more opens the default program (respectively, Evince and LibreOffice Writer) but it opens the typical "open with" window asking me to choose a program to associate to the specific file type.

I've been googling but the proposed solutions are not clear to me.
Also, I've been trying reinstalling kubuntu-desktop metapackage but it didn't solved the problem.

Any suggestion, please?
Thanks

---

### Post by samigina on 2011-12-22
Did you make any change in the system previous to the problem?

---

### Post by manolomanolo on 2011-12-22
I made no changes. Maybe just regular requires system updates.

---

### Post by inobe on 2011-12-22
back up your stuff, also you may lose your settings "if that matters" but you can reset your desktop by renaming or deleting .kde folder in hidden files via dolphin.

restart system.

if you have an ubuntu session too, i don't know what will happen.

---

### Post by manolomanolo on 2011-12-30
> **inobe said:**
> back up your stuff, also you may lose your settings "if that matters" but you can reset your desktop by renaming or deleting .kde folder in hidden files via dolphin.

restart system.

if you have an ubuntu session too, i don't know what will happen.

**Unfortunately, removing the .kde folder did not solve the problem: the application menu is still empty.**
Actually, I did not remove the .kde folder. I just renamed it into _kde_backup and restarted the machine. After restarting, the .kde folder obviously reappeared, even if I recognized no effective changes into my desktop environment, especially into the application menu list which is stil emply.

**Any other suggestion, please?**
Thanks

---

### Post by samigina on 2011-12-30
Try running **kbuildsycoca4 -noincremental** (like your user, not sudo)

---

### Post by inobe on 2011-12-30
> **manolomanolo said:**
> **Unfortunately, removing the .kde folder did not solve the problem: the application menu is still empty.**
Actually, I did not remove the .kde folder. I just renamed it into _kde_backup and restarted the machine. After restarting, the .kde folder obviously reappeared, even if I recognized no effective changes into my desktop environment, especially into the application menu list which is stil emply.

**Any other suggestion, please?**
Thanks

that is odd, i have totally borked my desk several times and this has never failed me, nor anyone else but you?

---

### Post by manolomanolo on 2012-01-02
> **samigina said:**
> Try running **kbuildsycoca4 -noincremental** (like your user, not sudo)

imma@imma-AcerPower-F6:~$ kbuildsycoca4 -noincremental
kbuildsycoca4 running...
kbuildsycoca4(6292): "applications.menu"  not found in  ("/home/imma/.config/menus/", "/etc/xdg/menus/") 

kbuildsycoca4(6292) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/file in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6292) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/trash in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon).

---

### Post by samigina on 2012-01-02
We have found the problem ```
kbuildsycoca4(6292): "applications.menu" not found in ("/home/imma/.config/menus/", "/etc/xdg/menus/") 
```

It seems you have a missing file "applications.menu" you can try copying this file from a live cd and running **kbuildsycoca4 -noincremental** again.

Loading a safe session gives you the same problem?

---

### Post by manolomanolo on 2012-01-08
> **samigina said:**
> We have found the problem ```
kbuildsycoca4(6292): "applications.menu" not found in ("/home/imma/.config/menus/", "/etc/xdg/menus/") 
```

It seems you have a missing file "applications.menu" you can try copying this file from a live cd and running **kbuildsycoca4 -noincremental** again.

Loading a safe session gives you the same problem?

Where should I copy that applications.menu file?
The error message says it has not be found neither into /home/imma/.config/menus/" nor into "/etc/xdg/menus/"
Should I copy it into both or just one of them?
Thanks

PD: meanwhile, I found the following file **/usr/share/app-install/desktop/applications.menu** on my kubuntu installation. Could the problem be there?
```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Applications</Name>
  <Directory>X-GNOME-Menu-Applications.directory</Directory>

  <AppDir>.</AppDir>

  <!-- we disable those here, otherwise we see e.g. wine menus -->
  <!-- Read standard .directory and .desktop file locations -->
  <!-- <DefaultAppDirs/> -->
  <!-- Read in overrides and child menus from applications-merged/ -->
  <!-- <DefaultMergeDirs/> -->

  <DefaultDirectoryDirs/>

  <!-- Accessories submenu -->
  <Menu>
    <Name>Accessories</Name>
    <Directory>Utility.directory</Directory>
    <Include>
      <And>
        <Category>Utility</Category>
        <!-- Accessibility spec must have either the Utility or Settings
             category, and we display an accessibility submenu already for
             the ones that do not have Settings, so don't display accessibility
             applications here -->
        <Not><Category>Accessibility</Category></Not>
        <Not><Category>System</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Accessories -->

  <!-- Accessibility submenu -->
  <Menu>
    <Name>Universal Access</Name>
    <Directory>Utility-Accessibility.directory</Directory>
    <Include>
      <And>
        <Category>Accessibility</Category>
        <Not><Category>Settings</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Accessibility -->

  <!-- Development Tools -->
  <Menu>
    <Name>Development</Name>
    <Directory>Development.directory</Directory>
    <Include>
      <And>
        <Category>Development</Category>
      </And>
      <Filename>emacs.desktop</Filename>
    </Include>
  </Menu> <!-- End Development Tools -->

  <!-- Education -->
  <Menu>
    <Name>Education</Name>
    <Directory>Education.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
        <Not><Category>Science</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Education -->

  <!-- Science -->
  <Menu>
    <Name>Science</Name>
    <Directory>GnomeScience.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
        <Category>Science</Category>
      </And>
    </Include>
  </Menu> <!-- End Science -->

  <!-- Games -->
  <Menu>
    <Name>Games</Name>
    <Directory>Game.directory</Directory>
    <Include>
      <And>
        <Category>Game</Category>
      </And>
    </Include>
    <!-- Sub-categories for the games -->
    <Menu>
      <Name>Action</Name>
      <Directory>ActionGames.directory</Directory>
      <Include>
        <Category>ActionGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Adventure</Name>
      <Directory>AdventureGames.directory</Directory>
      <Include>
        <Category>AdventureGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Arcade</Name>
      <Directory>ArcadeGames.directory</Directory>
      <Include>
        <Category>ArcadeGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Board</Name>
      <Directory>BoardGames.directory</Directory>
      <Include>
        <Category>BoardGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Blocks</Name>
      <Directory>BlocksGames.directory</Directory>
      <Include>
        <Category>BlocksGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Cards</Name>
      <Directory>CardGames.directory</Directory>
      <Include>
        <Category>CardGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Kids</Name>
      <Directory>KidsGames.directory</Directory>
      <Include>
        <Category>KidsGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Logic</Name>
      <Directory>LogicGames.directory</Directory>
      <Include>
        <Category>LogicGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Role Playing</Name>
      <Directory>RolePlayingGames.directory</Directory>
      <Include>
        <Category>RolePlaying</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Simulation</Name>
      <Directory>SimulationGames.directory</Directory>
      <Include>
        <Category>Simulation</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Sports</Name>
      <Directory>SportsGames.directory</Directory>
      <Include>
        <Category>SportsGame</Category>
      </Include>
    </Menu>
    <Menu>
      <Name>Strategy</Name>
      <Directory>StrategyGames.directory</Directory>
      <Include>
        <Category>StrategyGame</Category>
      </Include>
    </Menu>

  </Menu> <!-- End Games -->

  <!-- Graphics -->
  <Menu>
    <Name>Graphics</Name>
    <Directory>Graphics.directory</Directory>
    <Include>
      <And>
        <Category>Graphics</Category>
      </And>
    </Include>
  </Menu> <!-- End Graphics -->

  <!-- Internet -->
  <Menu>
    <Name>Internet</Name>
    <Directory>Network.directory</Directory>
    <Include>
      <And>
        <Category>Network</Category>
      </And>
    </Include>
  </Menu>   <!-- End Internet -->

  <!-- Multimedia -->
  <Menu>
    <Name>Multimedia</Name>
    <Directory>AudioVideo.directory</Directory>
    <Include>
      <And>
        <Category>AudioVideo</Category>
      </And>
    </Include>
  </Menu>   <!-- End Multimedia -->

  <!-- Office -->
  <Menu>
    <Name>Office</Name>
    <Directory>Office.directory</Directory>
    <Include>
      <And>
        <Category>Office</Category>
      </And>
    </Include>
  </Menu> <!-- End Office -->

  <!-- System Tools-->
  <Menu>
    <Name>System</Name>
    <Directory>System-Tools.directory</Directory>
    <Include>
      <And>
        <Category>System</Category>
<!--        <Not><Category>Settings</Category></Not> -->
<!--        <Not><Category>Game</Category></Not> -->
      </And>
    </Include>
  </Menu>   <!-- End System Tools -->

  <!-- Other -->
  <Menu>
    <Name>Other</Name>
    <Directory>X-GNOME-Other.directory</Directory>
    <OnlyUnallocated/>
    <Include>
      <And>
        <Category>Application</Category>
        <Not><Category>Core</Category></Not>
<!--        <Not><Category>Settings</Category></Not> -->
        <Not><Category>Screensaver</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Other -->


</Menu> <!-- End Applications -->

```

---

### Post by samigina on 2012-01-09
The file you found seems to be for gnome, Im using Kubuntu 11.10 and I have searched for the file and it doest exist in my install, so I take a look at my /etc/xdg/menus/ and found a **kde4-applications.menu** do you have this file?

Im attaching my file, so you can copy it in /etc/xdg/menus/ (like sudo) and test again.

---

### Post by samigina on 2012-01-09
I forgot the attachment :D.

Extract the file and copy in /etc/xdg/menus/

---

### Post by manolomanolo on 2012-01-20
> **samigina said:**
> I forgot the attachment :D.

Extract the file and copy in /etc/xdg/menus/

Unfortunately, it did not work.
What to do now?

---

### Post by manolomanolo on 2012-01-20
> **samigina said:**
> I forgot the attachment :D.

Extract the file and copy in /etc/xdg/menus/

Unfortunately, it did not work.
What to do now?

---

### Post by manolomanolo on 2012-01-20
**NEWS**
It seems it has some good effect.
The Application menu has been populated after a couple of runs of that command.
But, begin from the beginning. The first run produced:
```
 kbuildsycoca4 -noincremental
kbuildsycoca4 running...
kbuildsycoca4(3938): **"applications.menu"**  not found in  ("/home/imma/.config/menus/", "/etc/xdg/menus/") 

kbuildsycoca4(3938) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/file in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(3938) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/trash in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 
imma@imma-AcerPower-F6:~$ sudo cp /etc/xdg/menus/kde
kde4-applications.menu  kde-information.menu    
imma@imma-AcerPower-F6:~$ sudo cp /etc/xdg/menus/kde4-applications.menu /home/imma/.config/menus/
[sudo] password for imma: 
imma@imma-AcerPower-F6:~$ kbuildsycoca4 -noincrementalkbuildsycoca4 running...
kbuildsycoca4(7657): "applications.menu"  not found in  ("/home/imma/.config/menus/", "/etc/xdg/menus/") 

kbuildsycoca4(7657) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/file in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(7657) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/trash in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 

```

As y can see, the kbuildsyscoca4 command needs to find the applications.menu file. So, inspired but that error message marked in BOLD, I had to rename the kde4-applications.menu file and copy it into both "/home/imma/.config/menus/" and "/etc/xdg/menus/" folders. So, the menu populated.

However, this is the last output of running **kbuildsycoca4 -noincremental** showing some error messages anyway
                                                                                    
```
kbuildsycoca4 running...                                                                                                                                                                                   
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/kde4/bluedevil-network-dun.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                                                                                                                                           
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/kde4/bluedevil-network-panu.desktop" is not compliant with XDG standard (missing trailing semicolon).                                                                                                                                                                                                          
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/amaya.desktop" is not compliant with XDG standard (missing trailing semicolon).                       
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/leafpad.desktop" is not compliant with XDG standard (missing trailing semicolon).                     
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/abiword.desktop" is not compliant with XDG standard (missing trailing semicolon).                     
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/im-switch.desktop" is not compliant with XDG standard (missing trailing semicolon).                 
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/lxde-x-www-browser.desktop" is not compliant with XDG standard (missing trailing semicolon).        
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/language-selector.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/jockey-gtk.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/file in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(20991) KConfigGroup::readXdgListEntry: List entry x-scheme-handler/trash in "/home/imma/.local/share/applications/mimeapps.list" is not compliant with XDG standard (missing trailing semicolon). 

```

Should I do something more?

PD: I hoped that operations would also have solved the problem related to the fact that when clicking on the "K" button... the menu window appears in the upper-left corner of the desktop... while the related (and sole) pane is on the bottom of the desktop...

---

### Post by paul cooke on 2012-06-12
***_has this problem been fixed?_*** 

My KDE applications menu has suddenly gone blank as well. I had just made a file association in Dolphin to associate folders with Kaffeine and noticed it had gone empty afterwards. I'd launched dolphin using the applications menu just beforehand

---

### Post by paul cooke on 2012-06-13
Also Dolphin has forgotten all file associations as well except for the new one I'd added to handle directories with kaffeine.

---

### Post by paul cooke on 2012-06-15
B.U.M.P

anyone please?

KDE's applications menu is empty and Dolphin has lost it's file associations

---

### Post by MR2 on 2012-10-19
Get samigina attachment,rename kde4-applications.menu to applications.menu and copy it into "/home/$USER/.config/menus/"
run "**kbuildsycoca4 -noincremental**"

Solved :)

---

