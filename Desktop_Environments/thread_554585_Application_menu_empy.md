---
title: "Application menu empy"
date: 2007-09-19
forum: Desktop Environments
---

### Post by motscousus on 2007-09-19
hello, 

i am running gusty (with ubuntustudio and kde) and since 2 or weeks i think my applications menu in gnome is empty. i am trying to find a way to rebuild it or check  what could have done wrong with. 

where to start ?

cheers !

---

### Post by NoDough on 2007-09-21
Same problem.:confused:

I have a Dell E1505 that came with Feisty pre-installed, and as of two or three days ago my applications menu became empty as well.

Been googling for a fix, but no luck.

Anyone have a solution for this?

---

### Post by reset3x on 2007-09-22
Try ```
sudo update-desktop-database
```

Hope this helps!!!

---

### Post by Wolki on 2007-09-22
What happens if you right-click on the menu and select "edit menus"?

---

### Post by NoDough on 2007-09-22
sudo update-desktop-database ran successfully, but generated no output.  Did not fix up the menu.

If I right-click on the Applications menu and select "Edit menus", then a window opens and closes in a flash.  But that's all I get.

Thanks for the suggestions.  Any other ideas?

---

### Post by Wolki on 2007-09-22
If you create a new user and login as that user, is the applications menu empty there, too?

If no, your local .menu file is corrupt, if yes there is some system-wide problem.

If it works for another user, please post the conent of your "~/.config/menus/applications.menu" file.

Another possibility would be a corrupt .desktop file. try moving all things in "~/.local/share/applications" into a backup folder.

---

### Post by NoDough on 2007-09-22
Just ran "sudo update-desktop-database --verbose", and every entry says "lacks MimeType key".

Anyone know what that means?  Could it be the cause?

---

### Post by Wolki on 2007-09-22
> **NoDough said:**
> Just ran "sudo update-desktop-database --verbose", and every entry says "lacks MimeType key".

Anyone know what that means?  Could it be the cause?

I have the same here. It's unlikely to be the cause.

What it means is that .desktop files have a section where you can specify which filetypes this program can handle (so that the filemanager knows how to open them, for example). Some programs don't operate on files though, or that key isn't set for another reason. It should not cause errors.

---

### Post by NoDough on 2007-09-22
> **Wolki said:**
> If you create a new user and login as that user, is the applications menu empty there, too?

If no, your local .menu file is corrupt, if yes there is some system-wide problem.

If it works for another user, please post the conent of your "~/.config/menus/applications.menu" file.

Another possibility would be a corrupt .desktop file. try moving all things in "~/.local/share/applications" into a backup folder.

The new user has a normal, populated applications menu.

Here's the "~/.config/menus/applications.menu" file...

> <!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<DirectoryDir>/home/ashley/.local/share/desktop-directories</DirectoryDir>
	</Menu>
</Menu>

---

### Post by Wolki on 2007-09-22
> **NoDough said:**
> The new user has a normal, populated applications menu.

Here's the "~/.config/menus/applications.menu" file...

Wonderful, this means it's an error in your settings and not a system error. These should be much easier to fix.

Looking at the file you posted, I see a space character in the closing </MergeFile> tag. (between the e and the r). If I put a space there on my system, I lose my applications menu as well, so try to remove that space ("gedit ~/.config/menus/applications.menu", delete the superfluous character, and save) and see whether you get your applications menu back.

---

### Post by NoDough on 2007-09-22
Oddly, when I opened the file for editing, the was no extraneous space.  I retyped MergeFile anyway, saved the file, logged out and back in.  Still no luck.

Thanks for the help, BTW.

Any ideas for the next move?

---

### Post by Wolki on 2007-09-22
> **NoDough said:**
> Oddly, when I opened the file for editing, the was no extraneous space.  I retyped MergeFile anyway, saved the file, logged out and back in.  Still no luck.

Thanks for the help, BTW.

Any ideas for the next move?

Hmm.... can you repost the file in code tags instead of quote tags? maybe the forum software is messing up the file. Or just attach the file (if you're allowed to, I don't know)

Or, what you could try, is simply deleting the file - it should get regenerated (and this time, hopefully without errors)

---

### Post by NoDough on 2007-09-22
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<DirectoryDir>/home/ashley/.local/share/desktop-directories</DirectoryDir>
	</Menu>
</Menu>
```

Also, copy of the file is attached.

---

### Post by NoDough on 2007-09-22
Ba da bing, ba da boom.

Renaming the applications.menu file and allowing it to be recreated solved the problem.

Thanks so much for your help.

ADDED:  Oddly, the file was not recreated.  It no longer exists, but the applications menu works fine now.

---

### Post by Wolki on 2007-09-22
> **NoDough said:**
> Ba da bing, ba da boom.

Renaming the applications.menu file and allowing it to be recreated solved the problem.

Thanks so much for your help.

ADDED:  Oddly, the file was not recreated.  It no longer exists, but the applications menu works fine now.

Glad that it works now.

Though I still wonder what caused this, looking at the file it seems to be ok. And especially why this happened, seems like some other users have the same problem.

> ADDED: Oddly, the file was not recreated. It no longer exists, but the applications menu works fine now.

Yeah, it's only for modifications to the system default menu; the freedesktop menu spec says programs handling such menus must look in various places, then merge the contents in a special way.

Maybe there are problems in ~/.local/share/desktop-directories? hmmm... If you edit your menus now, does the problem reappear?

---

### Post by NoDough on 2007-09-22
Nope.  Able to edit to my heart's content.

What's more, I diff'd the new and old applications.menu files and the only differences were the edits I made.

Strange.

---

### Post by Esther on 2007-09-23
I am really new to Ubuntu, I mean REALLY new....and I got an empty applications menu as well...would like to see if another user also has an empty menu, but I cannot get into the user/groups part. It says I cannot enter it, being the root....I would like to go back not being the root and just user Esther, but I have no idea how, as I cannot get into my applications menu, i don't know how to get into terminal and then how to change it....Any help would be appreciated!

---

### Post by Esther on 2007-09-23
When I try to enter user/groups, I get this message:  Failed to run users-admin as user root.

---

### Post by NoDough on 2007-09-23
Esther,

1) Boot up your computer.
2) Press Cntrl+Alt+F1 (your screen should change to a black, text login screen)
3) Logon as your default user.
4) Type "cd .config/menus"
5) Type "mv applications.menu applications.menu.old"
6) Press Cntrl+Alt+F7 (your screen will change back to the graphical login)
7) Logon and test to see if your applications menu has reappeared.

Hope this helps.

---

### Post by stooge4ever on 2007-09-30
Hey everyone, I'm having a similar empty menu problem in gutsy that seems to be going around. i tried renaming applications.menu, but instead of resetting my menu, it simply blanked it (i have some things come up, but not everything - only games, graphics and system, and even those have numerous things missing).

here's my applications.menu. let me know if there's anything i can fix

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Games</Name>
		<Include>
			<Filename>Pingus.desktop</Filename>
		</Include>
		<Include>
			<Filename>Mupen64-1.desktop</Filename>
		</Include>
		<Include>
			<Filename>Mupen64-2.desktop</Filename>
		</Include>
		<Include>
			<Filename>FlightGear.desktop</Filename>
		</Include>
		<Layout>
			<Merge type="menus"/>
			<Filename>sol.desktop</Filename>
			<Filename>armagetron.desktop</Filename>
			<Filename>gataxx.desktop</Filename>
			<Filename>blackjack.desktop</Filename>
			<Filename>glines.desktop</Filename>
			<Filename>FlightGear.desktop</Filename>
			<Filename>gnect.desktop</Filename>
			<Filename>freecell.desktop</Filename>
			<Filename>freeciv.desktop</Filename>
			<Filename>gnometris.desktop</Filename>
			<Filename>gnudoku.desktop</Filename>
			<Filename>gtkboard.desktop</Filename>
			<Filename>iagno.desktop</Filename>
			<Filename>gnotski.desktop</Filename>
			<Filename>lincity.desktop</Filename>
			<Filename>lincity-ng.desktop</Filename>
			<Filename>mahjongg.desktop</Filename>
			<Filename>gnomine.desktop</Filename>
			<Filename>Mupen64-2.desktop</Filename>
			<Filename>nexuiz.desktop</Filename>
			<Filename>gnibbles.desktop</Filename>
			<Filename>Pingus.desktop</Filename>
			<Filename>gnobots2.desktop</Filename>
			<Filename>same-gnome.desktop</Filename>
			<Filename>slune.desktop</Filename>
			<Filename>gtali.desktop</Filename>
			<Filename>gnotravex.desktop</Filename>
			<Merge type="files"/>
		</Layout>
		<AppDir>/home/adam/.local/share/applications</AppDir>
		<Exclude>
			<Filename>gfceu.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>pcsx.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>vbaexpress.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>Wolfenstein: Enemy Territory.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>Frets on Fire.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Office</Name>
		<Include>
			<Filename>TilEm.desktop</Filename>
		</Include>
		<Include>
			<Filename>Celtx.desktop</Filename>
		</Include>
	</Menu>
	<Include>
		<Filename>Mupen64.desktop</Filename>
	</Include>
	<Layout>
		<Merge type="menus"/>
		<Menuname>Accessibility</Menuname>
		<Menuname>Accessories</Menuname>
		<Menuname>Debian</Menuname>
		<Menuname>Education</Menuname>
		<Menuname>Games</Menuname>
		<Menuname>Graphics</Menuname>
		<Menuname>Internet</Menuname>
		<Menuname>Office</Menuname>
		<Menuname>Other</Menuname>
		<Menuname>Development</Menuname>
		<Menuname>Multimedia</Menuname>
		<Filename>Mupen64.desktop</Filename>
		<Menuname>System</Menuname>
		<Menuname>wine-wine</Menuname>
		<Separator/>
		<Filename>gnome-app-install.desktop</Filename>
		<Merge type="files"/>
	</Layout>
	<Menu>
		<Name>Education</Name>
		<AppDir>/home/adam/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Internet</Name>
		<Exclude>
			<Filename>galeon.desktop</Filename>
		</Exclude>
		<AppDir>/home/adam/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Graphics</Name>
		<AppDir>/home/adam/.local/share/applications</AppDir>
		<Include>
			<Filename>ooo-draw.desktop</Filename>
		</Include>
		<Include>
			<Filename>alacarte-made.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/adam/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Debian</Name>
		<DirectoryDir>/home/adam/.local/share/desktop-directories</DirectoryDir>
	</Menu>
</Menu>

```

---

### Post by Brandel Valico on 2007-10-01
Just had this happen to me. My Applications menu stopped working. To fix it I went Copied the information from the Applications menu found at  /etc/xdg/applications.menu

To the one found in the Home Folder/.config/Menus/applications.menu

It completely restored my application menu to working order and so it shows all my installed applications as well. 

Hope this helps those still having issues with this

---

### Post by digby280 on 2007-10-01
> **Brandel Valico said:**
> Just had this happen to me. My Applications menu stopped working. To fix it I went Copied the information from the Applications menu found at  /etc/xdg/applications.menu

To the one found in the Home Folder/.config/Menus/applications.menu

It completely restored my application menu to working order and so it shows all my installed applications as well. 

Hope this helps those still having issues with this

This solution worked for me.  One question though won't this mean that I have to do this every time I install/uninstall a program to keep the menu up to date because it is no longer merging with /etc/xdg/menus/applications.menu?

---

### Post by stooge4ever on 2007-10-01
So problem with that.

I don't HAVE a /etc/xdg/applications.menu. i'm looking, but it's just not there...

what now?

---

### Post by digby280 on 2007-10-01
> **stooge4ever said:**
> So problem with that.

I don't HAVE a /etc/xdg/applications.menu. i'm looking, but it's just not there...

what now?

I think that was a typo and it's ment to be: /etc/xdg/menus/applications.menu

Hope that helps.

---

### Post by stooge4ever on 2007-10-01
regardless, i have it not. i have...
debian-menu.menu, enlightenment-applications.menu, gnome-screensavers.menu, gnomecc.menu, kde-applications.menu, kde-information.menu, kde-screensavers.menu, kde-settings.menu, preferences.menu, settings.menu, system-settings.menu.

no applications.menu

---

### Post by Wolki on 2007-10-01
> **stooge4ever said:**
> 
no applications.menu

That's the root of your problem, I think. Try reinstalling gnome-menus via synaptic.

---

### Post by stooge4ever on 2007-10-01
i just tried that. no dice. i still have the same 3 folders "games" "graphics" "system" wiht few things in them. i tried going through the menu editor, but it gives me no options of programs to put it. i'm at my wit's end!

---

### Post by Brandel Valico on 2007-10-03
Stooge4ever try creating a new applications.menu in .config/Menus

using the following 

> <!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Applications</Name>
  <Directory>Applications.directory</Directory>

  <!-- Scan legacy dirs first, as later items take priority -->
  <LegacyDir>/etc/X11/applnk</LegacyDir>
  <LegacyDir>/usr/share/gnome/apps</LegacyDir>
  <LegacyDir>/usr/share/control-center-2.0/capplets</LegacyDir>

  <!-- Read standard .directory and .desktop file locations -->
  <DefaultAppDirs/>
  <DefaultDirectoryDirs/>

  <!-- Read in overrides and child menus from applications-merged/ -->
  <DefaultMergeDirs/>

  <!-- Accessories submenu -->
  <Menu>
    <Name>Accessories</Name>
    <Directory>Accessories.directory</Directory>
    <Include>
      <And>
        <Category>Utility</Category>
        <Not>
          <Category>System</Category>
        </Not>
      </And>
    </Include>
  </Menu> <!-- End Accessories -->

  <!-- Accessibility submenu -->
  <Menu>
    <Name>Accessibility</Name>
    <Directory>Accessibility.directory</Directory>
    <Include>
      <And>
        <Category>Accessibility</Category>
        <Not>
          <Category>Settings</Category>
        </Not>
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
      </And>
    </Include>
  </Menu> <!-- End Education -->

  <!-- Games -->
  <Menu>
    <Name>Games</Name>
    <Directory>Games.directory</Directory>
    <Include>
      <And>
        <Category>Game</Category>
      </And>
    </Include>
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
    <Directory>Internet.directory</Directory>
    <Include>
      <And>
        <Category>Network</Category>
      </And>
    </Include>
  </Menu>   <!-- End Internet -->

  <!-- Multimedia -->
  <Menu>
    <Name>Multimedia</Name>
    <Directory>Multimedia.directory</Directory>
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
        <Not><Category>Settings</Category></Not>
      </And>
    </Include>
  </Menu>   <!-- End System Tools -->

  <!-- Other -->
  <Menu>
    <Name>Other</Name>
    <Directory>Other.directory</Directory>
    <OnlyUnallocated/>
    <Include>
      <And>
        <Category>Application</Category>
        <Not><Category>Core</Category></Not>
        <Not><Category>Settings</Category></Not>
      </And>
    </Include>
  </Menu> <!-- End Other -->

  <!-- The Debian menu -->
  <Menu>
    <Name>Debian</Name>
    <MergeFile>debian-menu.menu</MergeFile>
    <Directory>Debian.directory</Directory>
  </Menu>

<Include>
  <Filename>gnome-app-install.desktop</Filename>
</Include>

<!-- Separator between menus and gnome-app-install -->
<Layout>
  <Merge type="menus"/>
  <Merge type="files"/>
  <Separator/>
  <Filename>gnome-app-install.desktop</Filename>
</Layout>

</Menu> <!-- End Applications -->

digby280 Thanks for correcting the path and showing the right one. Sorry about that guys.
I have tried installing several programs now after having done this and my list updates each time.

---

### Post by stooge4ever on 2007-10-07
it's alive! thank you so much for that script! you rock

---

### Post by Brandel Valico on 2007-10-10
I'm glad it worked. 

Thanks for giving me the chance to return the favor so many people in this community have given me. By helping others with problems when your able to do so.

It's what makes this one of the best user communities around.

---

### Post by pmorton on 2007-10-17
> **NoDough said:**
> Esther,

1) Boot up your computer.
2) Press Cntrl+Alt+F1 (your screen should change to a black, text login screen)
3) Logon as your default user.
4) Type "cd .config/menus"
5) Type "mv applications.menu applications.menu.old"
6) Press Cntrl+Alt+F7 (your screen will change back to the graphical login)
7) Logon and test to see if your applications menu has reappeared.

Hope this helps.

My Applications pull-down menu and 'Edit Menus' right-click  stopped functioning after a disk-full crash.   NoDough's instructions (above) fixed  it.

---

### Post by LeslieL on 2007-11-06
Thank you! I had exactly this problem when I changed from Gutsy Kubuntu to Ubuntu - no applications menu. Brandel Valico's fix gave me something to start with. Still no idea what happened to my menus, tho.

---

### Post by csmth on 2007-11-15
I have the same experience. So this is my example and the result I solved that.

After some set up my files becomes:
```
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">

<Menu>
  <Name>Applications</Name>
  <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
  <Menu>
    <Name>Universal Access</Name>
    <Exclude>
      <Filename>onboard.desktop</Filename>
      <Filename>onboard-settings.desktop</Filename>
    </Exclude>
  </Menu>
  <Menu>
    <Name>Other</Name>
    <Exclude>
      <Filename>wine-Programs-Icewind Dale II-Icewind Dale II.desktop</Filename>
      <Filename>wine-Programs-Black Isle-Icewind Dale II-Icewind Dale II Configuration.desktop</Filename>
      <Filename>wine-Programs-Black Isle-Icewind Dale II-Icewind Dale II - Readme.desktop</Filename>
      <Filename>wine-Programs-Black Isle-Icewind Dale II-Icewind Dale II Setup & Uninstall.desktop</Filename>
    </Exclude>
  </Menu>
  <Menu>
    <Name>System</Name>
    <Exclude>
      <Filename>gdebi.desktop</Filename>
      <Filename>gdmflexiserver-xnest.desktop</Filename>
    </Exclude>
  </Menu>
</Menu>
```

Because my last action is to excluding some "Icewind Dale" items, I realized the excluded part of "Icewind Dale" is wrong. I don't know why the syntax is wrong, I even do not know the syntax, but after deleting the exclude, it works.

---

### Post by tCarls on 2007-11-23
Thanks so much to everyone in this thread! I've been trying to figure this out for days. Copying /etc/xdg/menus/applications.menu got most of my menu back. However, I'm using KDE and I'm still missing K System Settings and KControl (and probably more that I don't realize right now.) How do I get those back? I would add them manually with kmenuedit but the applications I add don't show up in the menu. Maybe this is a separate problem.

---

### Post by Brandel Valico on 2007-12-14
Having never ran KDE I'm sadly not going to be much help to you. But I'll at least bump this back up. Hopefully someone who has ran KDE will be able to help you out.

---

### Post by gdmix on 2008-01-01
Renaming “~/.config/menus/applications.menu” worked for me, thanks!

Mine broke after including some Wine menus.

---

### Post by christopher.newell on 2008-01-01
Thanks so much for this post!  I didn't actually fix mine using your method, but it is what got me looking in the right spot.  I went to /home/username/.config/menus and I saw all the applications.menu.undo-## files, and when I organized them by date, I noticed that somehow the current one was for today, even though I hadn't made any changes, so I renamed that one and took our the "undo..." for the last one, and bango! I got my menu back as soon as the rename was complete.  I wouldn't have found that if it weren't for your post, so thanks.  I've been googling for hours to no avail.

---

