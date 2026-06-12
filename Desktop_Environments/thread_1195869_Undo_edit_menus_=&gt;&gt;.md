---
title: "Undo edit menus =&gt;&gt;?"
date: 2009-06-24
forum: Desktop Environments
---

### Post by laeg_ on 2009-06-24
I mistakenly went into Applications =>> Edit Menus =>> and clicked on revert. Now every entry but Accessories in Applications =>> Wine ==>> Programs is prefixed with wine-Programs- and uninstalling and re-installing wine didn't fix the problem.

How can I?

---

### Post by gettinoriginal on 2009-06-24
Edit Menus > Wine > Programs then highlight the program and "Properties" on Right then edit name.  :P

---

### Post by laeg_ on 2009-06-24
> **gettinoriginal said:**
> Edit Menus > Wine > Programs then highlight the program and "Properties" on Right then edit name.  :P

They're not programs, they're directories and nothing happens when I right click them :(

---

### Post by gettinoriginal on 2009-06-24
You should be able to highlight the directory and the properties, then rename. At least it works here.

---

### Post by laeg_ on 2009-06-24
> **gettinoriginal said:**
> You should be able to highlight the directory and the properties, then rename. At least it works here.

I can't and selecting the directory in Edit Menus and then properties doesn't do anything either :(

Having a gnome problem with print screen since 9.04 also, it works except when I have the applications, places or system menus open but that's another matter.

---

### Post by laeg_ on 2009-06-24
Maybe I should re-install gnome?

---

### Post by gettinoriginal on 2009-06-24
Before you do that, reboot and when you get to the log in screen, select options, then session, and choose gnome, the resume log in.

---

### Post by laeg_ on 2009-06-24
> **gettinoriginal said:**
> Before you do that, reboot and when you get to the log in screen, select options, then session, and choose gnome, the resume log in.

I selected gnome and clicked on change session after which I was prompted "Do you want to make gnome your default or just use for this session because you have it set to run an XPerl script" - I clicked on just for this session because I wasn't sure.

There was no change to the menus, so should I now uninstall and re-install gnome and if so is it safe to do it through synaptic because if I removed my desktop I may not have anyway to re-install it through the GUI - perhaps I have to do it through terminal and if so what are the commands please?

Thanks.

---

### Post by laeg_ on 2009-06-24
c

---

### Post by laeg_ on 2009-06-24
```
#
laeg@skyrocket:~$ cd ~/.config/menus/applications-merged
#
laeg@skyrocket:~/.config/menus/applications-merged$ ls
#
wine.menu
#
wine-Programs-Accessories-Media Center-Media Center Programs.menu
#
wine-Programs-Cain.menu
#
wine-Programs-Curse-changelog.menu
#
wine-Programs-Curse-Curse Client.menu
#
wine-Programs-Curse-EULA.menu
#
wine-Programs-Curse-Uninstall.menu
#
wine-Programs-DivX-DivX Codec-Links.menu
#
wine-Programs-DivX-DivX Codec.menu
#
wine-Programs-DivX-DivX Converter-Links.menu
#
wine-Programs-DivX-DivX Converter.menu
#
wine-Programs-DivX-DivX Player-Links.menu
#
wine-Programs-DivX-DivX Player.menu
#
wine-Programs-DivX-DivX Web Player-Links.menu
#
wine-Programs-DivX-DivX Web Player.menu
#
wine-Programs-DivX-Helpful Links.menu
#
wine-Programs-DivX.menu
#
wine-Programs-Electronic Arts-Crysis.menu
#
wine-Programs-Electronic Arts-Crysis-Support Files Czech.menu
#
wine-Programs-Electronic Arts-Crysis-Support Files English UK.menu
#
wine-Programs-Electronic Arts-Crysis-Support Files French.menu
#
wine-Programs-Electronic Arts-Crysis-Support Files Hungarian.menu
#
wine-Programs-Electronic Arts-Crysis-Support Files Polish.menu
#
wine-Programs-Full Tilt Poker-Full Tilt Poker.menu
#
wine-Programs-Full Tilt Poker-Uninstall Full Tilt Poker.menu
#
wine-Programs-Gadu-Gadu.menu
#
wine-Programs-K-Lite Codec Pack-Configuration.menu
#
wine-Programs-K-Lite Codec Pack-Help.menu
#
wine-Programs-K-Lite Codec Pack.menu
#
wine-Programs-K-Lite Codec Pack-Tools.menu
#
wine-Programs-K-Lite Codec Pack-Uninstall.menu
#
wine-Programs-MagicISO.menu
#
wine-Programs-PacSteam.menu
#
wine-Programs-Paddy Power  Poker-Paddy Power  Poker.menu
#
wine-Programs-Paddy Power Poker-Paddy Power  Poker.menu
#
wine-Programs-Paddy Power  Poker-Uninstall Paddy Power  Poker.menu
#
wine-Programs-SmartDCT4Calc v1.17.menu
#
wine-Programs-Steam.menu
#
wine-Programs-VALVe-Counter-Strike Source.menu
#
wine-Programs-VALVe-Half-Life 2.menu
#
wine-Programs-Valve-Half-Life.menu
#
wine-Programs-Valve-Half-Life-MODs.menu
#
wine-Programs-Warcraft III.menu
#
wine-Programs-WinDirStat-Help (ENG).menu
#
wine-Programs-WinDirStat-Uninstall WinDirStat.menu
#
wine-Programs-WinDirStat-WinDirStat.menu
#
wine-Programs-WinPcap.menu
#
wine-Programs-WinRAR-Console RAR manual.menu
#
wine-Programs-WinRAR-WinRAR help.menu
#
wine-Programs-WinRAR-WinRAR.menu
#
wine-Programs-World of Warcraft-Account Billing.menu
#
wine-Programs-World of Warcraft-Blizzard Technical Support.menu
#
wine-Programs-World of Warcraft.menu
#
wine-Programs-World of Warcraft-World of Warcraft.menu
#
wine-Programs-World of Warcraft-World of Warcraft Read Me.menu
#
wine-Programs-World of Warcraft-World of Warcraft - Repair.menu
#
wine-Programs-World of Warcraft-World of Warcraft - Uninstall.menu
#
wine-Programs-World of Warcraft-Wrath of the Lich King - Manual.menu
#
 
#
 
#
laeg@skyrocket:~/.config/menus/applications-merged$ cd ..
#
laeg@skyrocket:~/.config/menus$ sudo nano applications.menu
#
 
#
 
#
 
#
 GNU nano 2.0.9                                     File: applications.menu                                                                                
#
 
#
<!DOCTYPE Menu
#
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
#
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
#
<Menu>
#
        <Name>Applications</Name>
#
        <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
#
        <Menu>
#
                <Name>Internet</Name>
#
                <Include>
#
                        <Filename>alacarte-made.desktop</Filename>
#
                </Include>
#
                <Include>
#
                        <Filename>alacarte-made-4.desktop</Filename>
#
                </Include>
#
                <Include>
#
                        <Filename>alacarte-made-5.desktop</Filename>
#
                </Include>
#
        </Menu>
#
        <Menu>
#
                <Name>wine-wine</Name>
#
                <Menu>
#
                        <Name>wine-Programs</Name>
#
                        <Menu>
#
                                <Name>wine-Programs-Electronic Arts</Name>
#
                                <DirectoryDir>/home/laeg/.local/share/desktop-directories</DirectoryDir>
#
                        </Menu>
#
                        <Menu>
#
                                <Name>wine-Programs-VALVe</Name>
#
                                <DefaultLayout inline="false"/>
#
                                <Menu>
#
                                        <Name>alacarte-made</Name>
#
                                        <Directory>alacarte-made.directory</Directory>
#
                                        <Include>
#
                                                <Filename>alacarte-made-2.desktop</Filename>
#
                                        </Include>
#
                                </Menu>
#
                                <Menu>
#
                                        <Name>wine-Programs-VALVe-Counter-Strike Source</Name>
#
                                        <Include>
#
                                                <Filename>alacarte-made-3.desktop</Filename>
#
                                        </Include>
#
                                </Menu>
#
                        </Menu>
#
                </Menu>
#
        </Menu>
#
        <Menu>
#
                <Name>Games</Name>
#
                <Include>
#
                        <Filename>alacarte-made-1.desktop</Filename>
```

---

