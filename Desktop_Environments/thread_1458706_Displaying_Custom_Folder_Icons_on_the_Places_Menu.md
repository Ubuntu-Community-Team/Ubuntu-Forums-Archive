---
title: "Displaying Custom Folder Icons on the Places Menu"
date: 2010-04-20
forum: Desktop Environments
---

### Post by gypsyjiver on 2010-04-20
Hi everyone,

I have a little issue with the Places menu, and I would appreciate it a lot if anyone here could help me. I'm keeping my documents, music, and videos etc. on a separate partition from my home directory, formatted with encrypted fat32 so that I can access it from both my windows and my ubuntu installation. So I've made the folders, transferred the files, and I selected custom icons (by right-click, properties, click on custom icon, then select the file from /usr/share/icons/Humanity/places/48).

So far so good. The problem is that the custom icons don't appear in the Places sidebar in Nautilus or the main Places menu in gnome. It just comes up as a regular folder.

[See a screenshot of it here.]("http://www.jacksabode.co.uk/pics/PlacesMenuScreenshot.png")

Does anyone have an idea/workaround so that I can use my custom icons in the Places menu as well? I have tried it with scalable icons, with no difference. I've also tried looking for a configuration file which might have the details in, but I haven't found it - I suppose this probably has something to do with how the Places menu is automatically generated.

I'm running Ubuntu 9.10 Karmic Koala with Gnome.

I will be really grateful if anyone can help! [-o<

---

### Post by gypsyjiver on 2010-04-20
Oops, messed up the formatting of the location of the custom icon file. Here it is again:

/usr/share/icons/Humanity/places/48

---

### Post by jivimberg on 2010-04-25
Having the exact same problem here. 
Any help would be appreciated!

---

### Post by gypsyjiver on 2010-04-26
Bump

---

### Post by gypsyjiver on 2010-05-23
Bump

---

### Post by BenJokisch on 2010-06-07
bump.. i'm interested too, and haven't found an answer searching

---

### Post by t.rei on 2010-06-07
I would think that the theme containing the icons does not contain those scaled for the right size in the menu, thus defaulting to the stock folder icon.

[COLOR=Red] Make a backup! [/COLOR]
```

cp -r /usr/share/icons/Humanity HumanityBackup

```I'd suggest: 
copy the folder with the existing custom icons to your home dir, to have a "working copy"
```
cp  -r /usr/share/icons/Humanity/places/48 ./48icons
```now scale all your 48 icons that you are missing to 24 and to 32 sizes. (or even 22 and 16)
you can do that using gimp or a little inkscape and bash marvell:
```

cd 48icons
mkdir [COLOR=DarkRed]32[/COLOR]; for i in *; do inkscape $i -w=[COLOR=DarkRed]32[/COLOR] -h=[COLOR=DarkRed]32[/COLOR] --export-png=`echo [COLOR=DarkRed]32[/COLOR]/$i | sed -e 's/svg$/png/'`; done

```this will create the 32x32 icons as png-images in a folder called 32 within the 48icons folder
*this will also show alot of errors due to the links that exist!*
repeat with all occurances of 32 replaced by 24,22 and 16

Now you got a whole bunch of png images, I am sorry for not being shure if there is a way to easily scale loads of svg images? There most certainly is, but the above will create png files, that can also be used i.e. by kde components.

You will need to copy them into the corresponding folders in /usr/share/icons/Humanity/places using sudo:

```
cd ~
cd 48icons
sudo cp -r ./22 /usr/share/icons/Humanity/places/

```Repeat for all scaled icons.

Reload the theme and see if that helped. ;)

[COLOR=Red]Please note, that this WILL copy files of non-svg-nature to a system folder. If unsure use a copy of the Humanity theme for this.[/COLOR]

---

### Post by gypsyjiver on 2010-06-08
Thanks for the reply - it is much appreciated. I'm afraid it didn't work though. I did exactly as you suggested but it looks exactly the same as my previous screenshot after reboot.

Actually, I found out that there were already resized icons in /usr/share/icons/Humanity/places/24 and /usr/share/icons/Humanity/places/16 that were the same as the ones I used. They were there before I started. Adding .png images for sizes 22 and 32 didn't seem to help much.

Any suggestions for what to do next? Maybe file a bug report? I have no idea if this behaviour still exists in the latest version of Gnome, though.

---

### Post by korolla2987 on 2010-06-08
[U]Here all we are friend......

What do you say?

So i think there is no need of giving thanks....
[/U]

---

### Post by gypsyjiver on 2010-06-10
Well, I don't know t.rei and he tried to help me, so I think it's pretty normal to say thank you (not to mention good manners). Of course, now we are special Ubuntu friends ;)

Anyone have any other suggestions about my problem? If not I will look into filing a bug report.

---

### Post by t.rei on 2010-06-10
Hm, now I am confused about the icons not showing, because those directories I mentioned are exactly the places where they should be. Sry, I'm out of ideas why those should not be loaded.

maybe 'gtk-update-icon-cache' will help? But they SHOULD be picked from those folders, if they exists - the stock folder is just the fallback in those cases.

---

### Post by gypsyjiver on 2010-06-10
I'm afraid gtk-update-icon-cache didn't work. I also tried 16- and 24-sized icons on the folders, but it didn't make any difference. It seems that the icons won't display on the places menu no matter what the size.

Could it have something to do with the fact these folders are on an encrypted disk? Seems unlikely to me, but still.

More likely, do the folder icons only show up on the places menu if they point at folders in your home directory?

I'm off to bed now, so I'll have to wait until tomorrow to experiment further.

---

### Post by t.rei on 2010-06-11
Oh now we're getting somewhere.

You are using 'custom folders' for Documents, Pictures etc... right? And you set this by reght-click -> properties -> 'click image' ...

Not by assigning those places in *~/.config/user-dirs.dirs*
I think that was ist... not entirely certain, since I haven't messed with that in a while.

Anyway, mine looks like this:
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/.templates"
XDG_PUBLICSHARE_DIR="$HOME/Öffentlich"
XDG_DOCUMENTS_DIR="$HOME/Dokumente"
XDG_MUSIC_DIR="$HOME/Musik"
XDG_PICTURES_DIR="$HOME/Bilder"
XDG_VIDEOS_DIR="$HOME/Videos"

```
These are the Folders that show up on the Desktop with a custom icon, if the theme provides it. And also using that icon of another size in the menu's.

I hope we're getting closer.

---

### Post by gypsyjiver on 2010-06-12
Thanks, I got it working! ... sort of. :-?

It works perfectly for folders that are accessible at startup, but I'm running into problems because I access my encrypted partition manually. Let me demonstrate.

I found ~/.config/user-dirs.dirs and it looked like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```I edited it to add my custom folder locations:

```
XDG_DOCUMENTS_DIR="/mnt/encrypteddrive/Documents"
XDG_MUSIC_DIR="/mnt/encrypteddrive/Music"
XDG_PICTURES_DIR="/mnt/encrypteddrive/Pictures"
XDG_VIDEOS_DIR="/mnt/encrypteddrive/Videos"
```Now, if I mount my encrypted partition, log out, and log back in, it works! All the icons show up in the right places.

However, if I reboot, then it doesn't work. My settings are automatically reset by Gnome:

```
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
```This also happens if I log out and log in again with my encrypted drive unmounted. I think this must be because Gnome can't see the encrypted partition on startup and thinks it got moved or deleted.

I did a little testing, and if the folders are on a drive that is accessible at startup, everything works fine. 

```
XDG_DOCUMENTS_DIR="/mnt/normaldrive/Documents"
XDG_MUSIC_DIR="/mnt/normaldrive/Music"
XDG_PICTURES_DIR="/mnt/normaldrive/Pictures"
XDG_VIDEOS_DIR="/mnt/normaldrive/Videos"
```These settings are kept after reboot and work perfectly.

Also, if I point ~/.config/user-dirs.dirs to my encrypted drive, then log out and log in again with my encrypted drive mounted, then it works even if I unmount and mount my encrypted drive again.

An interesting thing happens if I reboot, then point ~/.config/user-dirs.dirs to my encrypted drive, then mount my encrypted drive. In this case, the folder icons work, the nautilus side-bar icons work, but the main places menu icons *don't* work.

Is there a good way to get round this??

---

### Post by gypsyjiver on 2010-06-12
Ok, now I've really got it working!

I had a search round the internet, and I found these two websites which were useful:
[http://www.movingtofreedom.org/2007/10/23/new-dirs-in-gutsy-documents-music-pictures-video/](http://www.movingtofreedom.org/2007/10/23/new-dirs-in-gutsy-documents-music-pictures-video/) (a bit old but still good)
[http://www.freedesktop.org/wiki/Software/xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs) (the freedesktop manual page)

So here's what I did:

[LIST=1]
[*]edited my ~/.config/user-dirs.dirs to point to the directories on my encrypted partition
[*]mounted my encrypted partition
[*]logged off and logged on with my encrypted partition still mounted
[*]checked that everything was showing up as it should
[*]edited my /etc/xdg/user-dirs.conf to "False"
[*]rebooted and checked that all the icons showed up when I mounted my encrypted drive
[/LIST]
Hooray! It all works! As for step number 5, this is what I did. Open a terminal and type:

```
gksudo gedit /etc/xdg/user-dirs.conf &
```The file looks like this:
```
# This controls the behaviour of xdg-user-dirs-update which is run on user login
# You can also have per-user config in ~/.config/user-dirs.conf, or specify
# the XDG_CONFIG_HOME and/or XDG_CONFIG_DIRS to override this
#

enabled=True

# This sets the filename encoding to use. You can specify an explicit
# encoding, or "locale" which means the encoding of the users locale
# will be used
filename_encoding=UTF-8
```I just changed the line in the middle to:

```
enabled=False
```And then saved the file.

This stops xdg-user-dirs-update from being run on login and overwriting your settings in ~/.config/user-dirs.dirs. This isn't a very elegant solution, because if you want to change those settings in the future I assume you'll have to edit the text file again. But it works for me.

Thanks for all your help, t.rei!

---

### Post by t.rei on 2010-06-12
So it took a while but the monster was found and slain! Hooraay! :)

I do somehow think this might be something a smart gnome/ubuntu guy might want to take a look at.

---

### Post by jivimberg on 2010-06-12
Hey I'm on Ludic Lynx and the behaviour is just the same...
any ideas?

---

### Post by gypsyjiver on 2010-06-13
Jivimberg: Did you try doing what I did? The steps should be pretty easy to follow. I don't know Lucid Lynx but I imagine the files and behaviours will be the same. Give it a try, and let us know how it goes. 

T.rei: I agree. It would be best if: a) the ~/.config/user-dirs.dirs file had a nice, shiny GUI interface, and b) there was sensible behaviour for folders not available on startup. I'd be interested in reading the logic behind xdg-user-dirs-update overwriting the user-dirs.dirs file every log-on.

I haven't been able to install lucid - the liveCD doesn't even boot up - but maybe I will try and install it on a virtual machine and experiment a little. I want to see if anything's different. All that's left after that is to learn to code so I can change it :lol:

---

### Post by gypsyjiver on 2010-06-13
By the way, for those not in the know, ~/.config is a hidden folder, so to open it you need to go to your home folder, then on the menu click "View --> Show Hidden Files". After that you can just open the .config folder and open the user-dirs.dirs file as normal.

Or, you could just use a terminal (or press Alt + F2) and open the file directly:
```
gedit ~/.config/user-dirs.dirs
```The information about this is scattered about all over this thread - if people want it I can make a better howto on this topic.

---

### Post by jivimberg on 2010-06-13
gypsyjiver: Well I tried your solution but didn't work for me. 
I'm using links to point to the directories I want, is that ok? 
or how I'm supose to bring the old places folders back?

Thanks in advance

---

### Post by gypsyjiver on 2010-06-13
Jivimberg: Need More Information! Tell us more about your setup. Are your Music and Video folders on an encrypted drive? Do you access that drive manually or automatically? If you access it automatically, are you using /etc/fstab or some other method? Also, please post the contents of your ~/.config/user-dirs.dirs file. Does this file change after reboot? Does it change after logging out and logging in again? What version of Gnome are you running?

When we have this information we can begin to answer your question.

---

### Post by jivimberg on 2010-06-13
Yes sorry about the lack of context :P

So I have created links in ~ pointing the directories Music, Documents, Videos, etc. The targeted directories are in a NTFS partition of the HD (not encrypted as far as I know) which I load manually.

The content of  ~/.config/user-dirs.dirs is this

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
#
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="/media/Datos/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="/media/Datos/Documents"
XDG_MUSIC_DIR="/media/Datos/Music"
XDG_PICTURES_DIR="/media/Datos/Pictures"
XDG_VIDEOS_DIR="/media/Datos/Videos"

```
 
It doesn't change after logout nor reboot (I set the /etc/xdg/user-dirs.conf enable flag to false as you explain in your post).

I'm running Gnome 2.30.0 Ubuntu 10.04

---

### Post by gypsyjiver on 2010-06-14
Ah, I think I see what the problem is.

You need to set your /etc/xdg/user-dirs.conf enable flag to false *after* you get everything working, not before. If you do it before, it will just never update your icons at all.

So, try this:


[LIST=1]
[*]Set your /etc/xdg/user-dirs.conf enable flag to True again and save the file.
[*]Make sure your ~/.config/user-dirs.dirs is pointing to the right place.
[*]Mount your NTFS partition.
[*]Log off and log on again. (NOT reboot)
[*]Check the correct icons are showing up in the folders, the nautilus side-bar and the places menu.
[*]Set your /etc/xdg/user-dirs.conf enable flag to False and save the file.
[*]Reboot.
[*]Mount your NTFS partition again and check if it works.
[/LIST]
The links you created in ~ shouldn't make any difference to the process. The links also won't get a special icon even if you succeed in getting a special icon for the folders on your NTFS partition. If you want custom icons for your links you'll have to do it manually.

If you get to step 5 and still no joy, let me know.

Of course, you could automatically mount your NTFS partition in /etc/fstab and avoid the need to fiddle around with /etc/xdg/user-dirs.conf. That's up to you though. By the way, do you have to enter your user account password when you mount the NTFS partition in Gnome? That happened to me, and I found out you can change it if you edit a text file somewhere. Let me know if you want to and I'll find out where it is again.

---

### Post by jivimberg on 2010-06-14
Thanks for your help gypsyjiver, it worked!!!

About the partition It wasn't asking for password. Anyway I decide to automount it on boot using PySDM (which is a little embarrasing to say) since I didn't want to waste time messing with the fstab.

So now everything is working great, thank you!!!

---

### Post by gypsyjiver on 2010-06-14
Glad to hear it ):P

---

### Post by gypsyjiver on 2010-06-14
By the way, has anyone tried this with ~/.config/user-dirs.dirs pointed to a partition that is mounted automatically when Gnome starts? (as opposed to starting at boot with /etc/fstab)

I'm curious whether the partition would get mounted first or whether xdg-user-dirs-update would run first. It might save some people some headaches who read this and think that Gnome detects their custom folders when really it doesn't...

---

### Post by PaLoBo on 2010-07-02
Hey all,

Sorry for jumping in right and the end and sort of hijacking the thread but I think some more info is warranted.

The reason the custom icons don't appear in the places menu is (correct me if I'm wrong) because it uses the standard:icon attribute. and not the Metadata::Custom Icon (See below)


Normal Folder:
```
gvfs-info ~/Downloads/ | grep icon
  **standard::icon: folder-download, folder**

```

Custom Folder:
```
gvfs-info ~/Dropbox/ | grep icon
  **standard::icon: inode-directory, gnome-mime-inode-directory, inode-x-generic, folder**
  metadata::nautilus-icon-view-auto-layout: true
  metadata::nautilus-icon-view-tighter-layout: false
  **metadata::custom-icon: Downloads/Icons/dropbox.svg**

```

UInfortunately I haven't yet had success using gvfs-set-attribute to change the standard::icon attribute.

This would in theory use your custom icon everywhere (places, sidebar etc.)

If anybody knows better please chime in.

Cheers,
PL

---

### Post by brookie on 2010-09-21
Thanks for this! 

As many folks have suggested, I installed Lucid in it's own partition with separate partitions for /home, and /data which has Documents, Videos, Downloads, etc... folders in it. For the longest time I didn't know why the folder icons were hosed. 

Today, I manually drilled down to fix the icons for these folders (right click icon/Properties/click icon/ and drill down...) in /usr/share/icons/Humanity/places/48. So my home folder icons and my data folder icons were fixed but my Places icons were still hosed. 

With your help I now have the Places icons fixed. I can't believe that more people haven't been bothered by the icons being wrong with this type of install. It's all pretty now! :) Sweet!

Cheers, 
brook

---

### Post by Joshimitsu on 2010-11-17
Hey everyone,

I'm using 10.10 and have Windows 7 running on virtualbox.  I managed to share my Music folder with Windows 7 and everything was working fine.  Now when I go into my Home folder, the Music folder no longer has an icon - it looks like a standard folder.  The little icon has gone from the folder in the Places drop-down menu as well.  

Can anyone tell me what went wrong?  And how I can restore the Music folder icon?

Thanks

---

### Post by Paanini on 2010-11-29
@[gypsyjiver]("http://ubuntuforums.org/member.php?u=1054451") - Thanks a lot for your guide - it was really very lucid (pun intended :P) and nifty; something I'd been wanting to change for long !
:)

---

