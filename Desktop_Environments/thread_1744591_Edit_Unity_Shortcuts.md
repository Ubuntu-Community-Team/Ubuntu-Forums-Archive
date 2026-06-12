---
title: "Edit Unity Shortcuts"
date: 2011-04-30
forum: Desktop Environments
---

### Post by burpootus on 2011-04-30
When you click the ubuntu button in unity, the Global Search dash comes up and under the search it has a list of shortcuts. The bottom row of shortcuts seems to point to what has been set in preferred applications. One shortcut does not fall into this category, view photos. It automatically takes you to shotwell. I don't use shotwell, I use picasa. Since there is not a setting for a photo viewing application in preferred applications, how can this shortcut be edited?

---

### Post by mc4man on 2011-04-30
There doesn't appear to be a straightforward way which there should be, so -
if you're not using shotwell than possibly try removing it and see if picasa takes it's place

(don't have picasa, but did remove shotwell and install fspot which is now showing in the dash

---

### Post by burpootus on 2011-04-30
> **mc4man said:**
> There doesn't appear to be a straightforward way which there should be, so -
if you're not using shotwell than possibly try removing it and see if picasa takes it's place

(don't have picasa, but did remove shotwell and install fspot which is now showing in the dash

I removed shotwell, but now eye of gnome seems to be the default. If I remove eye of gnome, then I also remove ubuntu-desktop so that's not an option.

The more I poke around the more I think unity is the wrong direction to go for desktop users. Maybe fine for other applications but I wish ubuntu would offer a more robust experience for desktop users. I guess I'll be going back to classic and see what 11.10 brings. If they decide to go unity only and not have a full fledged desktop environment then I'll move to another distro.

---

### Post by cmcanulty on 2011-04-30
I love Ubuntu but I won't upgrade to a more resource intensive, less functional Natty. If this trend continues I too will be gone. Very sad. Yes I did try Natty and allowed extra time for learning but it is simply more eye candy and less function and slower unless we resort to the old Windows deal of buying a new computer to keep up with fancy effects.

---

### Post by bigsmitty64 on 2011-04-30
> **cmcanulty said:**
> I love Ubuntu but I won't upgrade to a more resource intensive, less functional Natty. If this trend continues I too will be gone. Very sad. Yes I did try Natty and allowed extra time for learning but it is simply more eye candy and less function and slower unless we resort to the old Windows deal of buying a new computer to keep up with fancy effects.

I just wish they could have made the Dash Icons a little bigger :P Can't hardly see them. 
[/sarcasm]

---

### Post by mc4man on 2011-05-01
More of a curiousity than anything else, it's possible to get picasa to show in the dash
(even though it's wine app, installs to /opt and really isn't packaged/installed remotely like a  normal, proper .deb 

It may be possible to do thru gconf, didn't bother because I was building a new unity so just added it to a list
(could use a little higher quality icon, not unexpected there

---

### Post by burpootus on 2011-05-01
> **mc4man said:**
> More of a curiousity than anything else, it's possible to get picasa to show in the dash
(even though it's wine app, installs to /opt and really isn't packaged/installed remotely like a  normal, proper .deb 

It may be possible to do thru gconf, didn't bother because I was building a new unity so just added it to a list
(could use a little higher quality icon, not unexpected there

Where there's a will...

---

### Post by cybergalvez on 2011-05-14
> **mc4man said:**
> More of a curiousity than anything else, it's possible to get picasa to show in the dash
(even though it's wine app, installs to /opt and really isn't packaged/installed remotely like a  normal, proper .deb 

It may be possible to do thru gconf, didn't bother because I was building a new unity so just added it to a list
(could use a little higher quality icon, not unexpected there

And how did you do this?

---

### Post by fjgaude on 2011-05-14
> **bigsmitty64 said:**
> I just wish they could have made the Dash Icons a little bigger :P Can't hardly see them. 
[/sarcasm]

You can, you can. Make sure you have installed **compiz-editor**. Go to a command line with **Alt+F2** and type in compiz-editor. From there in go to **Desktop**, then** Ubuntu Unity Plugin.** Now click on **Experimental**. There you see a slider that lets you change the Launcher icon sizes, from 32 to 64 pixels.

---

### Post by bigsmitty64 on 2011-05-17
I was refering to the "dash" not the launcher. I got an answer on that though, the dash icon size is hard coded into the distro, therefore no resizing is possible at this time. This came from a Canonical employee over at askubuntu.com.

---

### Post by eric-yorba on 2011-05-17
> **bigsmitty64 said:**
> I was refering to the "dash" not the launcher. I got an answer on that though, the dash icon size is hard coded into the distro, therefore no resizing is possible at this time. This came from a Canonical employee over at askubuntu.com.
What everyone calls the "dash" is officially called the Launcher.  (Don't ask me why.)  The icon sizes are *not* hard coded, as stated above.

---

### Post by Calash on 2011-05-17
> **eric-yorba said:**
> What everyone calls the "dash" is officially called the Launcher.  (Don't ask me why.)  The icon sizes are *not* hard coded, as stated above.

I believe he is referring to Dash, as in the overlay that you get when clicking on the home button.  These icons you cannot resize at this time.



[http://askubuntu.com/questions/10228/whats-the-right-terminology-for-unitys-ui-elements](http://askubuntu.com/questions/10228/whats-the-right-terminology-for-unitys-ui-elements)

---

### Post by wojox on 2011-05-17
> **eric-yorba said:**
> What everyone calls the "dash" is officially called the Launcher.  (Don't ask me why.)  The icon sizes are *not* hard coded, as stated above.

Huh, what?

---

### Post by eric-yorba on 2011-05-17
Oh you're right, never mind.  I was thinking "dock."  Dock v. Dash.

This UI has to have the most confusing naming scheme I've ever seen.

---

### Post by practic on 2011-05-18
> **burpootus said:**
> When you click the ubuntu button in unity, the Global Search dash comes up and under the search it has a list of shortcuts. The bottom row of shortcuts seems to point to what has been set in preferred applications. One shortcut does not fall into this category, view photos. It automatically takes you to shotwell. I don't use shotwell, I use picasa. Since there is not a setting for a photo viewing application in preferred applications, how can this shortcut be edited?

There is a brute-force way to do this. Go to /usr/share/applications and edit the Shotwell shortcut (you'll need to open it in Gedit as root). You will see this:

```
[Desktop Entry]
Version=1.0
Name=Shotwell
GenericName=Photo Manager
Comment=Organize your photos
Exec=shotwell %U
Icon=shotwell
Terminal=false
Type=Application
MimeType=x-content/image-dcf;
Categories=Graphics;Photography;GNOME;GTK;
X-GIO-NoFuse=true
X-GNOME-Gettext-Domain=shotwell
X-GNOME-FullName=Shotwell Photo Manager
X-Ayatana-Appmenu-Show-Stubs=false
```

At the value where it says "Exec=", just change shotwell to picasa. Save the file. This also means that if you want to launch Shotwell, you'll have to do it from a terminal...but if you never use it, then no problem!:)

Also, you can change the icon by editing the "Icon=" value. Put in the path to your Picasa icon.

Oh, yeah...and make sure you don't have any Shotwell shortcuts at .local/share/applications, as these might take precedence over the one in /usr/share/applications.

---

