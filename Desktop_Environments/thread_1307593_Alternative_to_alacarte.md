---
title: "Alternative to alacarte?"
date: 2009-10-31
forum: Desktop Environments
---

### Post by 0xABC123 on 2009-10-31
Alacarte is laggy/slow and it doesn't have an option to choose the icon path for menu entries. Terminal looks ugly and password is needed. Are there any GUI gnome menu editors that aren't slow or limited?

---

### Post by zzarko on 2009-11-11
I'm searching for the same thing, nothing so far... alacarte is OK if you want to change an entry or two, but if you need to rearrange more than 4-5 entries, it's painfully unfriendly. You cannot move entry from one menu to another, you need to make a copy, and the delete the original. Also, making a copy automatically takes you to menu where you copied the entry. If you need to move more than one entry, you'll need to go back to first menu every time (there is no multi-selection). I have a lot of programs in Accessories submenu, and I wanted to sort them by functionality, but it's frustrating.

EDIT: both bugs are already reported in launchpad, for Jaunty alpha release, and still not fixed.

---

### Post by dummiebeginner on 2009-11-16
I am also goig crazy trying to arrange my menu. It is absurd that Ubuntu is so flexible but has some middle-age things. I need my own menu arranged to my needs not those huge lists of administration, preferences, accesories and system tools spread in four places for instance.

Is it impossible to change the menu to your taste making your own folders and dragging and dropping the elements easily as in Windows?

---

### Post by The Joe on 2009-11-29
I'm just bumping this, because I totally agree. I have hated Alacarte from the offset.

---

### Post by quequotion on 2010-02-15
I'd like to join in on this alacarte-hating if I may.

I once spent three hours editing every .desktop file  I could find (they are stored in at least three locations) in gedit in order to set up a menu in logical order with out any duplicates (or triplicates, or quadruples etc) of menu items and without any items mysteriously vanishing.  This painstakingly well made menu was erradicated by an upgrade to Jaunty.

Try this: copy a menu item to another directory and delete the original, or find a mysterious, unaccountable duplicate, and delete it or the original **and miraculously lose both forever**.....

Why did I even bother in the first place? Because alacarte doesn't effect only your programs menu. OH no.. it also specifies the applications for your "Open with..." dialog and affects several other parts of gnome's interface.  I had to change every .desktop file on my system so I could find useful programs to open files with and not triplicate entries for "winhlp32.exe" (installed by wine and completely useless). 

I don't like .desktop files much either. In order to get a menu item into a particular place, one must put it into a string of several categories. Sometimes a rather long string is required to get an item into a specific folder, sometimes only one; it is also possible for one .desktop file to represent multiple menu items just in case it wasn't confounding enough. Heaven forbid you want to put an item into your own custom menu folder, **because that can only be done by alacarte**.


rage.

---

### Post by mirak63 on 2010-04-11
I agree, alacarte sucks

---

### Post by simon_w on 2010-06-07
I totally agree with this.  Alacarte really sucks. It is far and away my least favourite thing about Gnome (and, therefore, about Ubuntu). It has pretty much the worst usability of any Gnome program I’ve ever used, frequently fails to work properly, and makes the most awful mess of crap in the configuration files (which I have to go and hand-edit when it screws something up).

Part of the problem is Alacarte itself, and part of the problem is the freedesktop.org menu specifications and standards. But it adds up to a real p.i.t.a.

@quequotion - it *is* possible to edit the menu files by hand and make something that makes some kind of sense...  but then opening alacarte, or sometimes, just installing a new program which adds itself to the menu, will cause it all to go to hell in a handcart. :(

---

### Post by Barafu Albino Cheetah on 2010-06-07
You can edit menu config files by hand. They are tough, butdo it a few times and you will see no problem. Just like compiling kernel. 
Ask Google for instructions, cause I did it years ago last time. 
Alakarte is in a shame state. You people shoul all write to main gnome project to make them assign a man to fix it, if current team can't.

---

### Post by simon_w on 2010-06-07
> **Barafu Albino Cheetah said:**
> You can edit menu config files by hand. They are tough, butdo it a few times and you will see no problem. Just like compiling kernel. 
Ask Google for instructions, cause I did it years ago last time. 
Alakarte is in a shame state. You people shoul all write to main gnome project to make them assign a man to fix it, if current team can't.

You *can* edit the menu specs. by hand, but I can't agree that there are no problems.  Once you've got your head around the over-rides and how the submenus work, you have to deal with the default folders nonsense too.

I started meddling with this less because I was dissatisfied with Alacarte (though I was), and more because I have some fairly complicated custom menus that I wanted to back-up.  I'm no slouch with this kind of stuff, but after an hour I just gave up.  It's too much of a mess.  As I indicated in my last post, though, this is not entirely the fault of Alacarte - much of the problem (in my eyes, at least) lies with the freedesktop.org standards.

I hesitate to suggest this, but what's wrong with a simple folder structure with launchers?  Perhaps a single XML to associate paths in this structure with a little metadata, including icons for folders?  Y'know, like on (whisper it) Windows?  I've been reading the stuff on freedesktop.org, but I'm still at a loss as to what need this proliferation of horrendously complicated nonsense is seeking to address....

---

### Post by afrodeity on 2010-06-22
This is definitely on my TO DO list. Desperately seeking a faster, lighter, better menu editor than Alacarte.

---

### Post by pastalavista on 2010-06-22
I create my own custom menu in a drawer on the panel but that solves nothing. You might like the [Mint Menu]("http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html")

---

### Post by afrodeity on 2010-06-23
Both mint menu and gnomenu were designed to be on the bottom panel. I like cardapio because it is close the original ubuntu menu. What I am looking for is a better editor. Alacarte is damn slow and old. 2007. It hasn't been updated since it came out, and Ubuntu really needs a better editor.

PS you are getting confused with the two parts of the main menu system. The undercarriage is edited by alacarte not cardapio.

---

### Post by dummiebeginner on 2010-06-23
Me too. It's ridiculous that you can customize everything in Ubuntu but not the Start Menu. I need to arrange it to my needs not to those fixed sections.

---

### Post by Maineac54 on 2011-04-23
I can't believe this thread has been around for a year and a half and has no answer.  I haven't found anything else either.  I checked SourceForge and don't see anyone working on a solution.  This is one project that the community really needs.  I generally just live with the menu on my other Linux machines, but I wanted to set up this machine to be used by several users.  There is no way to make changes to the system menu in Alacarte.

I have searched around for accurate, complete instructions to the FreedomDesktop but those are hard to find as well.  The best I've found is this: [http://manpages.ubuntu.com/manpages/hardy/man1/xdg-desktop-menu.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/xdg-desktop-menu.1.html) which, I believe is an html version of the man page.  Some of the comments here seem to explain some of the behavior I've seen.  Particularly updates/upgrades undoing the changes I've made.

Although FreedomDesktop does have some flaws.  Overall I like the idea of using configuration files to launch applications.  Has anyone tried uninstalling Alacarte?  Trying to use the Synaptic Manager to do it wants to uninstall the Ubuntu Desktop!  Not what I had in mind.

---

### Post by SnoFox on 2011-05-24
I decided it was about time to recover my Ubuntu forums password specifically so I could bump this thread. Why on earth hasn't ala-cart been updated? It is god-awful slow, not flexible, and overall unfriendly. Although, I highly doubt it's going to get a makeover by Canonical now that Unity and GNOME 3 are out in the wild... I guess this gives me a reason to try KDE, XFCE, and various other DEs I've been ignoring while I was happily using my GNOME 2 interface.

---

### Post by LionelPutz on 2011-05-26
alacarte dependencies are huge - ridiculous for a menu editor.
 
Try LXMenuEditor (lxmed) - download from SourceForge.  Designed for LXDE but works well in other environments - Java based, freedesktop.org compliant and very lightweight.

---

### Post by linfidel on 2012-01-22
Guess everyone has given up by now?  I've been playing with menus some, and yes, alacarte is bad, but I find it to mainly be one thing that makes it unusable: every time you move (well, copy) an entry to a new menu, it closes the old menu, and opens the new one, so you need to navigate back.  

I've been trying to make major changes, so I moved (menus get moved, items get copied!) all the original menus to one menu, called "original", and started copying from there to various new top-level menus of my own choosing.  It works, but it's slow due to the above behavior.

By the way, I've discovered a trick if you want to add new menus to the the panel.  I'm doing this in 11.10 gnome classic desktop, but it may work in gnome 2.

First, create a new custom menu using alacarte, with possibly at least one item; or you can skip this and add a whole existing menu, if desired.  If you will want a custom icon for the menu on the panel, pick an icon now by clicking on the icon.

Then, from the "add to panel" menu, choose "Application Launcher", then the Forward button; now, choose the menu you want to add, and press the "add" button.  The new menu should show up on the panel, and you can edit it using alacarte.  This menu can be hierarchical, if so desired.

---

