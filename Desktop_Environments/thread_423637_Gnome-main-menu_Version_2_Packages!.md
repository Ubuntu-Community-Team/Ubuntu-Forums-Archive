---
title: "Gnome-main-menu Version 2 Packages!"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Kevin on 2007-04-26
As many of you may have seen in screenshots of Novell's SLED 10 SP1, there are new updated version's of the "slab" gnome main menu that are much improved over the ones currently in the repos.

I made some packages of the new menu before feisty was released, and as such, that thread got closed.  So here they are once again :)

**Installation**
To install these packages, simply download the two .deb files attached to this post, and double-click to install both of them.  You'll need to install libslab0 first as it won't work without it.

Then right click on your panel, click "Add to panel" and add the "Slab Main Menu"

*Note:  If you have an earlier version of gnome-maine-menu installed, I strongly recommend you remove it first using the "Completely Remove" option in Synaptic.  This removes the configuration files from the earlier version which can mess some things up.  You could also do a ```
sudo apt-get remove --purge gnome-main-menu
```

**Customization**
You can add and remove applications from the favourites section by simply right clicking on the in either the menu or the Applications Browser.

The new version is not configured through gconf as in the earlier versions, but rather through *.xbel files stored in either /usr/share/gnome-main-menu of ~/.config/gnome-main-menu

If you want to change the items in the system menu, you can copy the files into your home directory and change everything to your liking.  Run ```
cp /usr/share/gnome-mein-menu/*.xbel ~/.config/gnome-main-menu
``` and then browse to that directory and edit the files in gedit.  The syntax isn't that difficult to get around.

**Search functionality**
To use the search box, you'll need to have either beagle or tracker installed.  Simply installing beagle will get you the search box, to use tracker you'll have to make a small change in gconf.

Fire up gconf by Alt-F2, and running gconf-editor.  Navigate to /desktop/gnome/applications/main-menu and change the key entitled "search_command" to read "tracker-search-tool SEARCH_STRING"

**Building packages from source**
I only built packages for i386, so if you're on another architecture, I've included the patches I made to the source so you can make your own package. (and post it to this thread so others can use it!)

Download the debian.tar.gz file I included, and paste it in a new folder called slab in your home directory.  Then just run the following in a terminal!```
cd slab
svn co http://svn.gnome.org/svn/gnome-main-menu/trunk
mv trunk slab-0.9.8
tar -xvf debian.tar.gz
mv debian slab-0.9.8/
cd slab-0.9.8
sudo apt-get install build-essential
sudo apt-get build-dep gnome-main-menu
./autogen.sh --prefix=/usr
dpkg-buildpackage -rfakeroot

```
And you'll have shining new packages waiting for you!

*Note: this doesn't include building the updated libslab0 binary.  I'll write up that soon, its more complicated.

**Known Issues**
On some desktops, the Ubuntu logo is clipped off.  I don't know why, my laptop doesn't do it, but my computer does.  I'll look into it.
The "Add to favourites" menu option in nautilus doesn't work yet. Looking through the code it doesn't seem to be implemented yet, or else I'm missing something.
The "Recently Used Apps" section is missing from these debs.  This is due to it not being implemented in gnome.  I updated patches and applied them to the gnome-panel and gnome-desktop packages but it didn't work, so I'll look more into it when I have time.


So here are the debs and a screenshot!  Let me know how it goes!  Only install libslab0-dev if you need it.

---

### Post by neutron on 2007-04-28
Hi! 

Thanks for the debs. It looks good, but I've two little problems:

1) I don't get the search bar in the SLAB menu. Any ideas?

2) I don't have my home folder anymore like I had in the previous gnome menu version. I'm not very good in editing text file so perhaps you can give me some hints?

there's a small error in your howto btw. "cp /usr/share/gnome-mein-menu/*.xbel ~/.config/gnome-main-menu" has to be "cp /usr/share/gnome-main-menu/*.xbel ~/.config/gnome-main-menu".

Thanks again!

/edit
btw, I've installed libtrackerclient0, tracker and tracker-search-tool.

/etit2
forget 2). It's under places now I see ;)

---

### Post by dentaku65 on 2007-04-28
> **Kevin said:**
> 
**Known Issues**
On some desktops, the Ubuntu logo is clipped off.  I don't know why, my laptop doesn't do it, but my computer does.  I'll look into it.


I think it depends by the default Ubuntu Theme, if you change to another one (eg. Industrial Tango) the logo (in this case a pc icon) will be showed correctly :-)

---

### Post by Kevin on 2007-04-28
> **neutron said:**
> 1) I don't get the search bar in the SLAB menu. Any ideas? Yeah, if you're using tracker, you need to set it up in gconf.  Go to gconf-editor, navigate to /desktop/gnome/apps/gnome-main-menu and there's a search-command key.  Change it to tracker-search-tool.
> forget 2). It's under places now I see ;)Yes, you can also get to it by clicking on your hard drive device though, its quicker.

> **dentaku65 said:**
> I think it depends by the default Ubuntu Theme, if you change to another one (eg. Industrial Tango) the logo (in this case a pc icon) will be showed correctly :-)
Ah, makes sense.  Although its using the distributor logo, you'd think that wouldn't change.

---

### Post by neutron on 2007-04-28
> **Kevin said:**
> Yeah, if you're using tracker, you need to set it up in gconf.  Go to gconf-editor, navigate to /desktop/gnome/apps/gnome-main-menu and there's a search-command key.  Change it to tracker-search-tool.

Sorry, forgot to mention it but I already did this..

---

### Post by el_itur on 2007-04-28
Looking at gconf I found a lot of yast2 calls specially on main-menu>cc_action_list.

Look at that a little

---

### Post by el_itur on 2007-04-28
In fact there is a lot of suse's configuration going on around here. Any of you know something about this? how to tweak this to call debian/ubuntu commands instead of suse's

---

### Post by Kevin on 2007-04-28
They're likely old keys from an old version of gnome-main-menu.  This version doesn't use gconf for any of the items on the menu.  Gconf is only there for some configuration options, not the contents of the menu.  I've customized all of the menu items in this package to be ubuntu specific.

---

### Post by Kevin on 2007-04-28
> **neutron said:**
> Sorry, forgot to mention it but I already did this..

Hmm, that's strange.  I'd first try a sudo apt-get remove --purge gnome-main-menu, the reinstall it, then change the search key and see if that fixes things.

You can also try changing the /desktop/gnome/applications/main-menu/lock_down/search_area_visible key to true.

---

### Post by neutron on 2007-04-29
> **Kevin said:**
> Hmm, that's strange.  I'd first try a sudo apt-get remove --purge gnome-main-menu, the reinstall it, then change the search key and see if that fixes things.

You can also try changing the /desktop/gnome/applications/main-menu/lock_down/search_area_visible key to true.

My fault. I checked it again and although I changed it from beagle to tracker it still listed the beagle command. I must have made an error.. Anyway, search is working now. 

Unfortunately I don't have the nice search icon as shown in your screenshot. Instead, I have a red cross (apparently it can't find an icon). Also, any idea how to change the ubuntu icon in the standard pc icon? (without installing a whole new theme?) 

Thanks!

---

### Post by Kevin on 2007-04-29
The search icon should be a part of tango, does it show up if you switch to tango icons?

And changing the pc icon to the ubuntu logo was a patch in my package.  You could download the source and disable the patch and build it if you really want to :)  The icon used there is hard-coded in.  Although you could also replace the distributor-logo icon with the pc icon.  It should be in /usr/share/icons somewhere.

---

### Post by VFiend on 2007-05-04
I compiled this on amd64 but the application browser and such isn't visible, presumably because I haven't compiled the newer libslab. Would be nice to see where you got it from/what any patches you applied to it are. And thanks for this.

---

### Post by Kevin on 2007-05-06
Ah yes, sorry about that, forgot to update.  I'll write it up in detail tomorrow, but in general, I got the source for control-centre ```
apt-get source control-centre
```

Then I copied the libslab folder from the gnome-main-menu svn source, and pasted it in the control-centre folder.  I then updated the debian/changelog so it wouldn't be overridden by the package manager, and rebuilt it ```
dpkg-buildpackage -rfakeroot
```

---

### Post by LordMau on 2007-05-11
Hullo.

where can i adjust the command to log-out? im not on gnome right now, using xfce. i was able to adjust the logut command in previous versions of gnome main menu as well as usp but it doesnt seem apparent here. i already went thru the *.xbel file youy suggested in the first post to no avail.

thanks!

---

### Post by jackmc on 2007-06-19
I really like this. Easy to use, looks good. One issue:

Recent documents.

I have documents everywhere that I want to be included in there, but only the ones in my "Documents" directory are showing up. Even if I could get it to do subdirectories within "documents" I'd be set. I'm a bit of an organisation freak...

---

### Post by mariner09 on 2007-07-13
What's the proper wording for the places.xbel file to add additional folders to that pane?

Is there a reference file somewhere that just knows the href entry for DOCUMENTS means ~/Documents?

---

### Post by LuisC-SM on 2007-08-21
To the Original Author.

First Off, Thanks a lot for this great tool. 

Could you be a litte bit more specific on how we can configurate the xbel files?.

Thanks a lot again

Luis.

PS. If you could post an example of what we can change and do, should be very usefull for future reference and new users.

---

### Post by nimajiman on 2007-09-24
Hi there,

I just downloaded the two debs from the original post (libslab and gnome-main-menu) and installed them. When I go to "add to panel...", I can find the slab menu item there, but I get this error when adding to panel
> 
The panel encountered a problem while loading "OAFIID:GNOME_MainMenu" 
Delete / Don't Delete  

Any ideas on whats going wrong?

---

