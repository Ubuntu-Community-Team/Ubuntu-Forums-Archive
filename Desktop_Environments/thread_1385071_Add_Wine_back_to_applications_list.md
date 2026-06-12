---
title: "Add Wine back to applications list"
date: 2010-01-19
forum: Desktop Environments
---

### Post by mister_playboy on 2010-01-19
My list of programs under Application > Wine had become messed up, with some entries for programs that had been uninstalled in Wine.  I was unable to remove these from the menu for some reason, so I removed the entire Wine category.  It was not re-added upon reinstalling Wine... do I have to add it all back manually, or is there some way to have it appear as it did when originally installed?

---

### Post by andrea000 on 2010-01-19
Wine doesn't delete anything, menu editors on Linux simply
mark's these menus as Deleted.You can undo this by opening 
the /home/<user name>/.config/menu/applications.menu
file with a text editor and finding the Wine section. Remove
the <Deleted/> flag from everything you want back and the
programs menu should come back.Example the deleted is in red
remove that and save then your menu will come back

        > <Menu>
                <Name>wine-wine</Name>
                [COLOR="Red"]<Deleted/>[/COLOR]
        </Menu>

or perhaps this:

        <Menu>
                <Name>wine-wine</Name>
                <Menu>
                        <Name>wine-Programs</Name>
                        <Menu>
                                <Name>wine-Programs-AutoHotkey</Name>
                                <DirectoryDir>/home/user/.local/share/desktop-directories</DirectoryDir>
                        </Menu>
                </Menu>
                [COLOR="Red"]<Deleted/>[/COLOR]
        </Menu>


---

### Post by mister_playboy on 2010-01-20
Ah, excellent.  Thank you.

---

### Post by linux_dream on 2010-11-06
I've done exactly the same procedure as mister_playboy, however I can't get wine back into the applications menu.
In my "/home/isaac/.config/menus" I have more than 1 text file.  I've checked them all, and there's not a single place where there's a [COLOR=Red]<Deleted/> [COLOR=Black]line[/COLOR].
[COLOR=Black]I'm all ears to suggestions.  I want to recover wine in the Applications menu.  And yes, I did reinstalled it.  [/COLOR]
[COLOR=Black]Here's a screenshot of what I see in the .config folder.  [/COLOR]
[/COLOR]

---

### Post by hitman2k9 on 2011-05-20
worked good for me too thanks :) .

---

### Post by losthawken on 2011-10-31
Me 3 :D

---

