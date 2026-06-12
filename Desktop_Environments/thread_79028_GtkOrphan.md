---
title: "GtkOrphan"
date: 2005-10-19
forum: Desktop Environments
---

### Post by saltydog on 2005-10-19
I have just released very first version of GtkOrphan, a graphical tool to find and remove orphaned libraries from your system.

The deb package can be downloaded [here.]("http://www.marzocca.net/linux/gtkorphan.html")

**Note:**
Read dependencies on the web site, as GtkOrphan uses deborphan v.1.7.17. The version in breezy is buggy, so pls install deborphan from [debian package]("http://packages.debian.org/deborphan").

---

### Post by Dr. Nick on 2005-10-19
Cool App, I just learned about deborphan a few days ago and just tried it yesterday, Had alot of orphaned but didnt feel like removing them all manually, removed  few and havent had any trouble, This will make getting the last 13 out easier.

And yes I understand that their is a chance of error :) but my system is running well so messing it up would be a welcome change :p

---

### Post by saltydog on 2005-10-19
A little care must be taken when playing with "Guessing libraries". Only there.

---

### Post by angkor on 2005-10-19
I've been using deborphan for a while now. My system had a lot of orphaned .debs after dist-upgrading to Breezy and removed em all using deborphan.

---

### Post by Dr. Nick on 2005-10-19
Another thing you may have to be on the lookout for is meta-packages. I deleted the gstreamer multiverse metapackages and now alot of usefull looking gstreamer plugins are listed, not all them though, Does it mean they are no longer needed or possibly deprecated? I think I will keep them around for now, dont seem to be hurting anything.

Also when I guess libraries and hit OK it crahses and just disapperas, I ran from a terminal and no output came up. Any Ideas? Possibly a 64bit thing?

---

### Post by saltydog on 2005-10-19
GtkOrphan works with the results of deborphan, so possible improvements in the core should be sent to Peter Palfrader <weasel@debian.org>.

Anyway, if you have those gstreamer listed in the main window (with NO option selected!) it means that no package in your system depends on any of them. They are "orphaned", sad and lonely...

---

### Post by Dr. Nick on 2005-10-19
[QUOTE=saltydog]GtkOrphan works with the results of deborphan, so possible improvements in the core should be sent to Peter Palfrader <weasel@debian.org>.

Anyway, if you have those gstreamer listed in the main window (with NO option selected!) it means that no package in your system depends on any of them. They are "orphaned", sad and lonely...[/QUOTE]

What the heck I deleted them anyway, It is just weird when I remove all that are listed more show up immediately, I just kept removing them untill none showed up.

---

### Post by saltydog on 2005-10-19
That's normal.. It could be that an orphaned library has dependencies. If you remove the library, you "free" those dependencies and some of them could become new orphans.

---

### Post by ow50 on 2005-10-19
Does this have some advantages over using a filter in Synaptic?

---

### Post by saltydog on 2005-10-20
Yes. Much easier, faster and more precise. It allows you to set up hibernated files not to report anymore as orphaned, and to make deeper search guessing the library section.

---

### Post by saltydog on 2005-10-27
GtkOrphan 0.2.1 is out, and now on Debian main!

You can download it [here]("http://www.marzocca.net/linux/gtkorphan.html").

---

### Post by JurB on 2005-10-27
Tnx, nice program!

---

### Post by saltydog on 2005-11-06
**GtkOrphan** 0.3.0 is out, and now on Debian main!

You can download it [here.]("http://www.marzocca.net/linux/gtkorphan.html")

---

### Post by Kyral on 2005-11-06
Good work Saltydog

~ Kyral (aka Chris Peterman ;p)

---

### Post by ad noiseam on 2005-11-11
Very nice program, it helps a lot. Thank you.

My only question would be about the orphaned config files. Is there a way to remove them with this application?

---

### Post by saltydog on 2005-11-11
[QUOTE=ad noiseam]Very nice program, it helps a lot. Thank you.

My only question would be about the orphaned config files. Is there a way to remove them with this application?[/QUOTE]


Of course...
in the main window, expand the "Options" and you will find what you're looking for!

---

### Post by ad noiseam on 2005-11-11
[QUOTE=saltydog]Of course...
in the main window, expand the "Options" and you will find what you're looking for![/QUOTE]

Perfect, thank you.

---

### Post by opera on 2005-12-03
I might be doing things wrong since I am new to Linux but I have installed GtkOrphan on my system, and there's no way I can find it in the menus. Any suggestions?

---

### Post by ad noiseam on 2005-12-03
[QUOTE=opera]I might be doing things wrong since I am new to Linux but I have installed GtkOrphan on my system, and there's no way I can find it in the menus. Any suggestions?[/QUOTE]

I am not in front of Ubuntu right now, but I think GTKorphan puts itself in the "Administration" menu, not in the application ones.

---

### Post by opera on 2005-12-03
I know but believe me I have looked everywhere in every menu listing. BTW there were no errors reported when the programme installed.

---

### Post by ad noiseam on 2005-12-03
[QUOTE=opera]I know but believe me I have looked everywhere in every menu listing. BTW there were no errors reported when the programme installed.[/QUOTE]

Then you can add a new shortcut. Open up the Menu Editor and add a shortcut to "sudo gtkorphan".

Nicolas

---

### Post by Rob2687 on 2005-12-03
So how do I know which ones are safe to remove? Can I just remove all of the orphaned packages or what?

---

### Post by saltydog on 2005-12-03
[QUOTE=opera]I know but believe me I have looked everywhere in every menu listing. BTW there were no errors reported when the programme installed.[/QUOTE]
If you are running Gnome, it is in the Administration Menu. It is not listed as GtkOrphan, but as "Remove orphaned packages". Look for the "orphan-sam" icon!

---

### Post by saltydog on 2005-12-14
New **GtkOrphan v.0.3.1** is online!

You can download it [here]("http://www.marzocca.net/linux/gtkorphan.html").

---

### Post by Danielle on 2005-12-17
hi, i'd really like to try GtkOrphan but i can't find deborphan v.1.7.17 the link in the first post takes me to this page:
[http://packages.debian.org/deborphan](http://packages.debian.org/deborphan)
the versions on that page are for 1.0-3, 1.7.15 and 1.7.18 so i don't understand how to install v.1.7.17

this is what happened when i tried to install it anyway:

:~/Desktop$ sudo dpkg -i gtkorphan_0.3.0-1_all.deb
Selecting previously deselected package gtkorphan.
(Reading database ... 77089 files and directories currently installed.)
Unpacking gtkorphan (from gtkorphan_0.3.0-1_all.deb) ...
dpkg: dependency problems prevent configuration of gtkorphan:
 gtkorphan depends on deborphan (>= 1.7.17); however:
  Version of deborphan on system is 1.7.15.
dpkg: error processing gtkorphan (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtkorphan

can someone show me where i can get v.1.7.17? please. thanks

---

### Post by Danielle on 2005-12-17
oh, i've just come back from being away for a few days and i just found "Remove Orphaned Packages" in the System Menu. i must have installed it before i went away :rolleyes: 

here is what it finds. can i remove them all? thanks

---

### Post by saltydog on 2005-12-18
[QUOTE=Danielle]
can someone show me where i can get v.1.7.17? please. thanks[/QUOTE]

You can install deborphan v 1.7.18 from here:
[http://packages.debian.org/testing/admin/deborphan](http://packages.debian.org/testing/admin/deborphan)

just check your architecture (386, ppc, amd64, etc..)

---

### Post by Danielle on 2005-12-18
thanks, saltydog. after i posted i ended up doing installing v.1.7.18

---

### Post by saltydog on 2005-12-29
New **GtkOrphan v. 0.4.1** has been released!

Check it out on: [http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

From ChangeLog:
    v. 0.4.1
    * Removed Refresh button. Changes are applied on-the-fly

---

