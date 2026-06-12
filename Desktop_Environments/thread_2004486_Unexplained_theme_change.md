---
title: "Unexplained theme change"
date: 2012-06-15
forum: Desktop Environments
---

### Post by hwychld on 2012-06-15
I recently installed 12.04.  This was a fresh install and replaced the previous OS which was Ubuntu 10.04.  I keep my home directory on a separate partition, so I was able to keep all of my data even though I performed a clean install.  This included the data in the .config directory.

The last time I logged in my theme changed from the default 12.04 (which I like) to something really ugly.  My terminal windows suddenly had a menu displayed in the local window along with the same menu in the global menu.  The window buttons for maximize, minimize, and close were all moved to the right hand side of the windows, plus there was a little white dot that acted the same as right clicking to get a drop down list.  The keyboard shortcut CTRL+ALT+L no longer locks my screen.  The icons used in my applications (like when firefox pops up a window to warn about closing multiple tabs) look awful.  

I have been able to restore the ambiance theme, and using the gconf-editor fix the position of the window max, min, and close buttons.  I was also able to get rid of the extra menu for my terminal windows.  However I have had no luck getting my keyboard shortcut for locking the screen working, or fixing the stupid looking application icons.  The system settings selection for keyboard has the correct shortcut for locking the screen (plus I tried changing it) and I still can't get the shortcut to work.  

Can somebody please help me restore my desktop to the default 12.04 settings - I greatly prefer those to whatever has recently popped up (and I suspect this weirdness happened due to the 10.04 settings in the .config folder.

Thanks

---

### Post by hwychld on 2012-06-16
I just created a new user and that account is showing the same problems, so I have no idea what caused this issue.  But I sure would like to get it back to the way it was (especially the keyboard shortcut to lock the screen).

---

### Post by hwychld on 2012-06-18
Nobody has any thoughts on this?  Anybody else have this problem recently?

---

### Post by Frogs Hair on 2012-06-18
When you are logging be sure you have selected Ubuntu from the gear Icon in the login screen. The gnome environments in 12.04 do have the program menu in the applications as you have describe. Lucid had buttons on the left so it doesn't seem as though it is a residual configuration problem. Posting a screen shot may be helpful also.

---

### Post by hwychld on 2012-06-18
Thanks for the reply FrogsHair.  I have not installed any other desktop environments so I should definitely be using Ubuntu (Unity 3d).  I will check Ubuntu 2D just for kicks when I get home tonight to see if it is the same.

I took some screenshots this morning but didn't have time to upload them to Flikr before I had to go to work.  I also took some screen shots from a clean install in VirtualBox for comparison purposes.  I will try to get them posted tonight.

---

### Post by hwychld on 2012-06-18
Here is how it used to look (as seen in a virtual machine)

[[IMG]http://farm8.staticflickr.com/7234/7398771276_48be8da51a.jpg[/IMG]]("http://www.flickr.com/photos/31742906@N08/7398771276/")
[correct]("http://www.flickr.com/photos/31742906@N08/7398771276/") by [hwychld]("http://www.flickr.com/people/31742906@N08/"), on Flickr

Here is what it inexplicably changed into:

[[IMG]http://farm8.staticflickr.com/7096/7398770012_55f2bd1222.jpg[/IMG]]("http://www.flickr.com/photos/31742906@N08/7398770012/")
[foobar]("http://www.flickr.com/photos/31742906@N08/7398770012/") by [hwychld]("http://www.flickr.com/people/31742906@N08/"), on Flickr

---

### Post by hwychld on 2012-06-18
You will note in the foobar version:

The terminal window has a local menu (as well as the global menu).  
The min, max, and close buttons are on the right, and really plain looking.
The Appearances dialog shows Ambiance as the theme, but clearly that is not what is being used - note the blue bar at the top of the active window instead of ambiances dark grey.
I am not sure what that blue box on the appearance dialog is doing there - but it may explain the blue bar at the top of the active window.
Note the really stupid looking icons in the firefox dialog box.

I really want to restore the 'factory defaults'.  I did not attempt to change them so I don't know why they suddenly got whacky.  And I really want ctrl+alt+L to lock the computer again.

Thanks for the help.

---

### Post by Frogs Hair on 2012-06-19
This may be a configuration carry over. If all the hidden configuration folders were saved on your home partition they may be affecting the new installation which is Gnome 3 and those configurations are Gnome 2 from lucid.

I move files via cloud from clean installation to clean installation. I move mainly documents and photos though.When I tried a full home backup with Deja Dup the hidden folders from the previous installation caused major problems. I don't know if this is related related for sure.       

I have seen this problem reported before and a solution , but I will take some digging.

---

### Post by kansasnoob on 2012-06-19
> **hwychld said:**
> I just created a new user and that account is showing the same problems, so I have no idea what caused this issue.  But I sure would like to get it back to the way it was (especially the keyboard shortcut to lock the screen).

What about a guest session?

If that also has a problem then I'd look in /var/log/apt for package changes.

---

### Post by hwychld on 2012-06-19
> **kansasnoob said:**
> What about a guest session?

If that also has a problem then I'd look in /var/log/apt for package changes.

Haven't tried the guest session.  I am not sure how the new user I created would have been screwed up by the old config files though.  I will check the /var/log/apt log but there have been a ton of updates recently so trying to figure out which one it is might be hard.

I am not even sure when the change happened although I think it coincides with an (unsuccessful) attempt to install openvas.  The worst part is I made a clone of the disk right after this, but the clone has all of the same issues.  Too bad I didn't make the clone before the system went beserk.

---

### Post by hwychld on 2012-06-20
This just gets stranger and stranger.  The guest session exhibits the same problem.  I decided to just start fresh, reinstall.  I backed up my home directory stuff, and reinstalled, formatting both the / and /home partitions.  Then I started building my system back up, installing the software that I use such as nmap (compiled from source), virtual box, tomboy, and a few other minor ones.  I restored my Documents and stuff like that from my backup and restored my .bash_aliases file.  

At this point I was pretty happy with the way things were going so I decided to use clonezilla to make a backup image.  I used an older version (based on Maverick).  When I rebooted into Precise it was screwed up again.  Aha I figured, it was clonezilla doing the damage - makes no sense but that is what it seemed like.  So I did some testing in virtual box and was unable to duplicate the problem.

So I decide the fresh install again (maybe it was the reboot and not clonezilla).  Did the same thing, formatted / and /home.  This time the fresh install was screwed up.  I am getting really frustrated.  Oddly, the shutdown dialog box comes up as the correct theme but firefox, truecrypt and the like seem to be using there own.

Can anybody tell me what config files are used to control the keyboard shortcuts and also the config file for the theme used by applications - it seems like some applications are using their own theme while others are still using the Ubuntu default.

Thanks

---

### Post by kansasnoob on 2012-06-21
Look at the top section of this post:

[http://ubuntuforums.org/showpost.php?p=11993655&postcount=70](http://ubuntuforums.org/showpost.php?p=11993655&postcount=70)

I was fiddling with themes for a reason that's totally unrelated to what you're doing but I decided to check the defaults on a fresh install of Precise and I was surprised at what I found. 

In that top section you'll see what I found the defaults to be, what I think they should be, and a list of commands to see what they are.

---

### Post by hwychld on 2012-06-21
Thanks for the great info Kansasnoob, that is exactly the kind of stuff I needed.  It is a shame I hadn't read your tips and tweaks thread before.  Since I am running Unity I didn't look at the thread since it was for classic.  

Oddly enough, when I run the commands (am not actually at my machine but have ssh'd in - don't think that should make a difference but maybe it does since I don't actually have a desktop) I get the exact results of your preferred settings:


user@precise:~$ gconftool-2 -g /apps/metacity/general/theme
Ambiance

user@precise:~$ gsettings get org.gnome.desktop.interface gtk-theme
'Ambiance'

user@precise:~$ gsettings get org.gnome.desktop.interface icon-theme
'ubuntu-mono-dark'

user@precise:~$ gsettings get org.gnome.desktop.interface cursor-theme
'DMZ-White'

But obviously, it is still squirelly.  When I get home tonight I will run the commands when I am logged into the desktop.  

It does seem odd to me though that when I create a new user I get the same screwed up theme.  

I think I may try the classic desktop as well and see how that reacts (and it is more like I am used to, but I have to say Unity was nearly as bad as I had heard).

Where did you find the information on how to use gconf-2 and gsettings from the command line?

---

### Post by hwychld on 2012-06-21
OK, so thanks to KansasNoob I have learned quite a bit over the last couple of hours and I can answer a couple of my own questions, which I will share for anybody else who stumbles across this thread.  First learning about gsettings - gsettings works on schemas, and schemas have keys associated with them. So with this piece of code:

```

gsettings get org.gnome.desktop.interface buttons-have-icons

``` 

retrieves the value from the key 'buttons-have-icons' from the schema "org.gnome.desktop.interface".

To get a list of all the available schema:

```

gsettings list-schemas | less 

```

Then to check out the keys of a particular schema and the values of the keys:

```

gsettings list-recursively org.gnome.desktop.interface

```

And you will see:
```

user@precise:~$ gsettings list-recursively org.gnome.desktop.interface
org.gnome.desktop.interface automatic-mnemonics true
org.gnome.desktop.interface buttons-have-icons false
org.gnome.desktop.interface can-change-accels false
org.gnome.desktop.interface clock-format '24h'
org.gnome.desktop.interface clock-show-date false
org.gnome.desktop.interface clock-show-seconds false
org.gnome.desktop.interface cursor-blink true
org.gnome.desktop.interface cursor-blink-time 1200
org.gnome.desktop.interface cursor-blink-timeout 10
org.gnome.desktop.interface cursor-size 18
org.gnome.desktop.interface cursor-theme 'DMZ-White'
org.gnome.desktop.interface document-font-name 'Sans 11'
org.gnome.desktop.interface enable-animations true
org.gnome.desktop.interface font-name 'Ubuntu 11'
org.gnome.desktop.interface gtk-color-palette 'black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90'
org.gnome.desktop.interface gtk-color-scheme ''
org.gnome.desktop.interface gtk-im-module ''
org.gnome.desktop.interface gtk-im-preedit-style 'callback'
org.gnome.desktop.interface gtk-im-status-style 'callback'
org.gnome.desktop.interface gtk-key-theme 'Default'
org.gnome.desktop.interface gtk-theme 'Ambiance'
org.gnome.desktop.interface gtk-timeout-initial 200
org.gnome.desktop.interface gtk-timeout-repeat 20
org.gnome.desktop.interface icon-theme 'ubuntu-mono-dark'
org.gnome.desktop.interface menubar-accel 'F10'
org.gnome.desktop.interface menubar-detachable false
org.gnome.desktop.interface menus-have-icons false
org.gnome.desktop.interface menus-have-tearoff false
org.gnome.desktop.interface monospace-font-name 'Ubuntu Mono 13'
org.gnome.desktop.interface show-input-method-menu true
org.gnome.desktop.interface show-unicode-menu true
org.gnome.desktop.interface text-scaling-factor 1.0
org.gnome.desktop.interface toolbar-detachable false
org.gnome.desktop.interface toolbar-icons-size 'large'
org.gnome.desktop.interface toolbar-style 'both-horiz'
org.gnome.desktop.interface toolkit-accessibility false
org.gnome.desktop.interface ubuntu-overlay-scrollbars true
user@precise:~$

```

You can use 'get' and 'set' to retrieve or modify individual keys.

Thanks KansasNoob for giving me something to sink my teeth into.

---

### Post by hwychld on 2012-06-21
I am beginning to suspect the gnome-settings-daemon as the cause of my trouble.  I have this in my .xsession-errors file:
```

(gnome-settings-daemon:8953): Gdk-WARNING **: The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 557 error_code 8 request_code 141 minor_code 22)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

gnome-session[8870]: WARNING: App 'gnome-settings-daemon.desktop' respawning too quickly
gnome-session[8870]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Initializing unityshell options...done

```

And I have found out that the hotkey stuff (such as my broken ctrl-alt-L to lock screen) can be traced to this daemon.

This ring any bells for anybody?

---

