---
title: "Menu editing in Xfce"
date: 2006-06-09
forum: Desktop Environments
---

### Post by DevilInPgh on 2006-06-09
How do I edit the menu in Xfce so I can put apps in the folders that I want them in?  I saw that I can add programs to the menu via the GNOME menu editor, but this places apps in the "Other" folder.  And when I use the Xfce menu editor, it just has a space that represents the whole system, which I can't edit.

---

### Post by easy_target on 2006-06-23
I wanna do the same thing. Anyone out there can help us?

---

### Post by aysiu on 2006-06-23
Edit the menu the way you want and then save it as /home/username/.custommenu.xml

In XFCE menu properties, select **use custom menu file** and then navigate to your custom menu.

---

### Post by jonathantneal on 2006-06-23
If you want to edit the main menu, you have to load the default .xml

If you want to edit 99% of that menu; the part that exists above the first seperator and beneath the second (settings, accessories, games, graphics, multimedia, network, office, other, system - you know, just those...) then I haven't a clue, and I hope we find out soon! :)

EDIT: someone else posted the solution while I was writing my comment.  UNDO, CTRL+Z, BACKSPACE, CTRL+ALT+DELETE MYPOST.

---

### Post by ardchoille on 2006-07-06
[QUOTE=aysiu]Edit the menu the way you want and then save it as /home/username/.custommenu.xml

In XFCE menu properties, select **use custom menu file** and then navigate to your custom menu.[/QUOTE]
The problem is you **can't** edit most of the xfce4 menu with the menu editor. Even many of the xfce community agree that the menu editor is almost useless. 

I have, however, found a way to change things in the system menu. Create new .desktop files in ~/.local/share/applications and those new meu items will show up in the xfce4 menu immediately.. at least they did for me.

---

### Post by ezphilosophy on 2006-08-20
> **aysiu said:**
> Edit the menu the way you want and then save it as /home/username/.custommenu.xml

In XFCE menu properties, select **use custom menu file** and then navigate to your custom menu.

Aysiu,

How do you edit the menu in the way of accessories, games, utilites, etc.?  I just installed xfce from Kubuntu and I have loads of applications that I really don't want in the menu.  For some reason, with the install, xfce decided to put a bunch of screensavers in the "system" menu.

You mentioned editing a menu, that just seems to be for the other menu components e.g., settings, terminal, run program, etc.

Any ideas?  Anyone?

---

### Post by lionel47 on 2006-08-21
The screensavers in the system menu is a great annoyance to me, too.  I hope someone finds the answer.:confused:

---

### Post by DirtDawg on 2006-08-22
All the menu files can be found in /usr/share/applications in the form of ".desktop" files. The easiest thing to do is edit those (make a backup first). For example, Cream was under applications, but I wanted it in Development. 

Here is the original "/usr/share/applications/cream.desktop" file:
```

[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Name=Cream
Comment=Edit text files
Comment[de]=Textdateien editieren
TryExec=cream
Exec=cream %F
MimeType=text/plain
Categories=Application;Utility;TextEditor;
Icon=/usr/share/pixmaps/cream.xpm

```

I changed the "Categories" line to include "Development" rather than "Applications", so now it shows up in the "Development" catergory:
```
Categories=Development;Utility;TextEditor;
```

To remove something from the menu, add the following line to a ".desktop" file at the bottom:```
NoDisplay=true
``` 

I found this trick and a few others [here]("http://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/").

Hope this helps

---

### Post by oyvindaa on 2006-11-29
Thanks, DirtDawg. That's a very useful trick.

---

### Post by fresonrebelde on 2007-01-02
in addition: not all .desktop files are under /usr/share/applications.

do ** locate *.desktop ** to find them all

i wanted to edit some &#8220;Root Shell&#8221; icon, and it was found in /home/rob/.kde/share/apps/konsole/su.desktop :)

---

### Post by nyinge on 2007-01-22
Thanks, DirtDawg.  Working beautifully now.  :)

Just one question...  Those MIME Types ...  If I put some types in there for an app, will they make those files default to be opened by that particular application?

---

### Post by brunobelo on 2007-05-10
Is there a way to edit the SYSTEM menu?

---

### Post by TravMan63 on 2007-06-23
I'm using Xubuntu 7.04 - and the file isn't there - did the search with no luck either.

My main issue is the 'other menu' - lots of 'wine' apps in there (I think instaled with 'sidewine'?)
many 'wine' files are in home/username/.config/menus/applications-merged/

 directory - but editing has no effect...

Seems to be a problem reported on the XFCE site as well...

TM

---

### Post by OunSu on 2007-07-20
Try this link [http://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/](http://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/)  and see the comments.

---

### Post by hellork on 2007-12-16
I thought Xfce uses the gnome menus, at least it used to. But now it doesn't seem to work. Strange.

---

### Post by nutts4life on 2007-12-20
Hi there,

Just thought i'd add in a note and a request. I decided to create my own menu completely as i wanted such a simple menu structure that to go to every .desktop file would be a real hassle.

Basically i used the menu editor to create a new mymenu.xml and added a system submenu, an accessories submenu and a games submenu. 

The rest of my programs i put as i icons on the panel.

BUT, the system submenu is huge and would be a real hassle to add every launcher one by one.

Has anybody done this already and can send me the xml?

All i need is the xml for creating all the launchers found under the current default 'system' menu, which launch the standard xfce4 system applicaitons.

It would be great to see some of your menus!

Thanks,

nutts4life

---

### Post by usacomputertec on 2008-02-11
Ok here is what I need to do. I'm making Ultumix 0.0.1.3 Light XFCE and I want to put all of the items above the first bracket and below the second one under an "all applications menu" or "All Programs" to make it easier for Windows Users. Is there any way I can do this? I will put my current code for my current file below and you can tell me what to do.

Something that may help you all. [http://standards.freedesktop.org/menu-spec/latest/]("http://standards.freedesktop.org/menu-spec/latest/")

<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<title name="Ultumix Lite Menu" icon="connect_creating"/>
	<separator/>
	<app name="Run Program" cmd="xfrun4" icon="xfce-system"/>
	<separator/>
	<app name="Xfce 4 mintConfig" cmd="xfce4-mintConfig" icon="gnome-control-center"/>
	<app name="Terminal" cmd="xfterm4" icon="terminal"/>
	<app name="Home" cmd="thunar" icon="gtk-home"/>
	<app name="Firefox web browser" cmd="firefox" icon="firefox"/>
	<separator/>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
	</menu>
	<separator/>
	<include type="system" style="multilevel" unique="true"/>
	<separator/>
	<app name="Help" cmd="xfhelp4" icon="stock_dialog-question"/>
	<app name="About Xfce" cmd="xfce4-about"/>
	<builtin name="Quit" cmd="quit" icon="xfce-system-exit"/>
</xfdesktop-menu>

Don't know if this does you any good but more power to you. Thanks.

And incase I don't get an e-mail giving me a reply my e-mail is [email]admin@mindblowingidea.com[/email] thanks.

---

### Post by usacomputertec on 2008-02-12
I put this in my menu.xml file but it didn't work.

	<separator/>
	<menu name="All Programs">
		<include type="system" style="simple" unique="true" legacy="true"/>
	</menu>
	<separator/>

It kept replacing the file for some reason so I changed the permissions to read only and it hasn't been changed but still it won't work.

Ok I talked to <kelnos|laptop> in the #XFCE IRC channel. He told me XFCE does not change it's menu.xml file back by itself so it's a mint script doing it in my OS.

---

### Post by mixmaster on 2008-02-13
Ugh, this system is truely dire.

I've recently tried to move to xfce.  Generally I like it, but the menu system stinks.  I managed to hide the system menu with the menu editor then couldn't get it back until I found out what the menu editor app was called so I could edit it from the desktop.  Then I managed to make the entire applications menu disappear playing with custom menu files and had to re-establish it using add-panel.

Anyway, one tip.

If you add the line 
<include type="file" src="menu2.xml"/>
to your ~/config/xfce4/desktop/menu.xml file then the contents of menu2.xml will be embedded in your menu.  I copied the original menu.xml to menu2.xml and started by editing that.  However, if you change menu2.xml the changes will not be reflected in the application menu unless you also update menu.xml (touch is sufficient).

Oh, yes, get used to editing the .xml files by hand if you use the default location because as far as I can see there is no way to persuade the "open file" option in the menu editor to traverse into a directory whose name begins in a "."

I've just noticed that the menu editor has disappeared from the autogenerated menu tree for reasons that I cannot fathom.

---

### Post by erginemr on 2008-02-15
I am a Gnome user. Tried KDE, but it wasn't cut for me. I like Gnome's feel and distributed system to handling the desktop very much, but also was reading favorable reviews of Xfce and thinking to give a try to Xubuntu or Xfce-desktop for that matter, because of its subtle balance between performance and user-friendliness.

I have attempted several times to use Xfce and like the overall performance and the familiar GTK+ look very much, but... The "so-called" menu editor did not show most of the items (later on I realized to my surprise that all boiled down to a single line "system menu" or something). I first thought that perhaps the Xfce version I installed was buggy, because I was expecting to have something similar to the Gnome alacarte menu, where you could manipulate the placement and appearance of all menu items.

To me, this "menu editing" issue is a real show-stopper. To customize the menu by editing a myriad of "*.desktop" files is a nightmare. I believe Xfce developers should concentrate on this issue and develop a decent menu editor for this really amazing desktop environment, which gets better and better at each release.

---

### Post by doorknob60 on 2008-02-19
> **erginemr said:**
> To me, this "menu editing" issue is a real show-stopper. To customize the menu by editing a myriad of "*.desktop" files is a nightmare. I believe Xfce developers should concentrate on this issue and develop a decent menu editor for this really amazing desktop environment, which gets better and better at each release.

I agree! My brothers computer uses Xfce because he only has 256 MB RAM, and it rocks because even with Compiz and Emerald and stuff it's a lot faster than Gnome and even a clean Windows 2000 install. But, when I try to do stuff with the menus, I just don't bother because there's no effeciant way to do it :( Lets hope that the next version of Xfce (I don't know the release schedule for Xfce, but I'm assuming that it will make it into Hardy?) has a menu editor that's not totally pointless. That's the only annoyance I have with Xfce right now, because everything else about it is great :D

---

### Post by Jouke74 on 2008-02-19
The trick I often use is to make a launcher at the Desktop using "appfinder". 

1. Open Appfinder.
2. Find the program you want to use, and "left-click and hold" this app.
3. Drag the application to the Desktop.
        It will now show an Icon on the desktop for that application.
4. Open a Terminal and issue the following commands:
> cd Desktop
> sudo mv <name of application>.desktop /usr/share/applications/

I don't know how to get rid of the "Other" but at least all apps are present in the menu.
If the menu fails to show the application, first reboot. It needs to make a new cache file in your home directory.

---

### Post by DAC1138 on 2008-02-23
I have a menu in ~/.config/xfce/menu.xml (not the actual directory, but its similar, since I don't want to type it all our for future reference)

The gnome/kde/xfce STANDARDS APP MENU (they agreed to this standard) is in /usr/share/applications and it's several .desktop files that gets put there when you install a program via apt-get. My copy of XFCE is reading from ~/.config/xfce/menu.xml

I've been googling for 3 hours now to figure out how to get it to reference the .desktop files in /usr/share/applications. Does anyone have a clue on how to do this?

#xfce on freenode wasn't too helpful. I'm in australia, so if they're in America or France I can understand why it was dead. It would be late night there on Friday.

---EDIT---

Okay then. Not thirty seconds after I posted this, my friend over IRC told me, "when in doubt, erase the config file." I didn't want to do it because I was affraid of having no menu or even a menu bar. So I renamed the config file, the one that is placed in ~/.config/xfce/menu. The menu now reads from /usr/share/applications.

So for future reference, if anyone wants to fix the problem that I was experiencing, delete or rename or move the "menu.xml" file located in ~/.config/xfce4/desktop

---

### Post by cardinals_fan on 2008-02-27
Just follow the tips on the Xfce wiki, paraphrased below:

> How to edit the auto generated menu with the menu editor?

cp ~/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml
cd ~/.config/xfce4/desktop/
cat menu.xml > menu3.xml
cat menu2.xml >> menu3.xml
mv menu.xml menu.orig.xml
mv menu3.xml menu.xml

Now, you already have a menu with all the categories in the main tree with some duplicates, but you must first edit menu.xml with your favorite editor and remove the 4 following lines in the middle of the file, otherwise the menu editor will complain about a wrong format:

</xfdesktop-menu>
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xfdesktop-menu>

<xfdesktop-menu>

That's all. Now you can run the menu editor, remove the few duplicates and edit all as you like.

Settings > Desktop > Menu > Menu Editor

Notes: by removing the “system” line, you will remove all the duplicates menu entries from the auto generated file. So, if it is changed in this auto generated file, they don't appear anymore, but you will get rid of most of the duplicates.

To restore the original menu, just do in a terminal:

mv menu.xml menu3.xml; mv menu.orig.xml menu.xml



In my experience, this duplicates the entire menu.  However, you can now remove the duplicates and add new items (even subfolders!) graphically.

---

### Post by DAC1138 on 2008-02-27
> **cardinals_fan said:**
> Just follow the tips on the Xfce wiki, paraphrased below:



In my experience, this duplicates the entire menu.  However, you can now remove the duplicates and add new items (even subfolders!) graphically.

It's a lot easier to just remove the menu config xml in the home directory. Just "rm -fr ~/.path-to-config-xml" and it will cause XFCE to resort to using the .desktop files in /usr/share/applications. Then, whatever you install/remove in synaptic it will automatically add/remove the item from the menu. And you still have the option of adding new items, simply by adding a new .desktop item to that directory.

---

### Post by cardinals_fan on 2008-02-28
> **DAC1138 said:**
> It's a lot easier to just remove the menu config xml in the home directory. Just "rm -fr ~/.path-to-config-xml" and it will cause XFCE to resort to using the .desktop files in /usr/share/applications. Then, whatever you install/remove in synaptic it will automatically add/remove the item from the menu. And you still have the option of adding new items, simply by adding a new .desktop item to that directory.

Yes, but this way doesn't let you create/edit submenus on the menu, and it also doesn't allow you to edit the categories.  That is well worth 5 minutes of my time.

---

### Post by SneakyWho_am_i on 2008-03-28
Interesting. Aysiu's screenshot shows two Windows. I have the first, and the second, but the second has much different content in my version of XFCE. I'm not taking a screenshot but basically the only "editable" item in that is the link to the settings thing. It's also the only collapsible category.

I'm not complaining, I can edit it by hand and I'm using Hardy proposed updates and backports and such ;) - it's just curious that everything after the second divider is just represented by
"--- include ---                                        system"
ESP tells me it's an "External" entry.

> **aysiu said:**
> Edit the menu the way you want and then save it as /home/username/.custommenu.xml

In XFCE menu properties, select **use custom menu file** and then navigate to your custom menu.

---

### Post by SnakeHips on 2008-04-21
> **cardinals_fan said:**
> Just follow the tips on the Xfce wiki, paraphrased below:
To restore the original menu, just do in a terminal:

mv menu.xml menu3.xml; mv menu.orig.xml menu.xml

.


I found that by doing a restore in this way i was left with some "junk entries". I deleted menu2.xml and menu3.xml to put the menu back in its original condition. Its left me wondering why the entries from menu2.xml and/or menu3.xml were still being read ? Does it "chain" the entries together in xml?

I'm new to xubuntu but to be honest i could do without having to re-work this just to get my menu customised - it's crying out for an easier solution.

---

### Post by SnakeHips on 2008-04-21
> **TravMan63 said:**
> I'm using Xubuntu 7.04 - and the file isn't there - did the search with no luck either.

My main issue is the 'other menu' - lots of 'wine' apps in there (I think instaled with 'sidewine'?)
many 'wine' files are in home/username/.config/menus/applications-merged/

 directory - but editing has no effect...

Seems to be a problem reported on the XFCE site as well...

TM

This worked for me...

[http://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/](http://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/)

"as OunSu im also using xubuntu, and ive found some shortcuts that shows in the category “Other” (that wine is using) in this directory:"

~/.local/share/applications/wine/

---

### Post by BeachBum on 2008-06-19
It seems you guys are doing it the hard way...

It looks like there are few things that need to be cleared up: in XFCE, you can edit the desktop files, which will also edit GNOME entries (AFAIK), or you can edit the XFCE menu itself.  

Editing the XFCE menu itself is probably the easiest, and again there are two ways to do this: 1. edit xml files, or 2. use XFCE's menu editor.  ( Run xfce4-settings-manager and click on Menu Editor).  This menu editor seems really barren, but it works very similarly to GNOME's menu editor.  You add/ remove entries using the plus/minus buttons, and you can hide the Include system entry so it doesn't show the default GNOME menu.  That way you can keep the GNOME menu the way it is and not worry about it, and create your own custom menu.  

See my screenshot for what I'm talking about.

Now if I can only figure out how to remove the icon space so the menu looks like fluxbox...

---

