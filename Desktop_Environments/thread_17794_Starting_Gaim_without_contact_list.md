---
title: "Starting Gaim without contact list?"
date: 2005-03-02
forum: Desktop Environments
---

### Post by Shambler on 2005-03-02
Hello,
is there a way to start Gaim without opening the contact list (since my Gnome fires up Gaim everytime I log in, this seems pretty annoying...)

---

### Post by bored2k on 2005-03-02
[QUOTE=Shambler]Hello,
is there a way to start Gaim without opening the contact list (since my Gnome fires up Gaim everytime I log in, this seems pretty annoying...)[/QUOTE]

u can just disable this start up program,
the EZer way is to close it , clic log off and SAVE current desktop .

Or thru Configuration Editr

---

### Post by p!=f on 2005-03-02
He wants to remove that annoying contact list window which shows up everytime you start gaim not gaim itself from the autostart.

Gaim Extended Preferences is the plugin you're looking for. I gave it a try and I can confirm it works. ;)
[http://gaim-extprefs.sourceforge.net/](http://gaim-extprefs.sourceforge.net/)

If you want Ubuntu package instead, let me know, I'll post it here. 
```

[~/src] > du -h gaim-extprefs_0.4-1_i386.deb
4,0K    gaim-extprefs_0.4-1_i386.deb

```
(built against Gaim 1.1.4)

---

### Post by Shambler on 2005-03-03
Well, if there's a special Ubuntu package: yes, post it!
Thx!

---

### Post by p!=f on 2005-03-03
There's no special Ubuntu package. Just the one I compiled for my personal use. :)
Download the attachement, unzip and install it:
```

gzip -d gaim-extprefs_0.4-1_i386.deb.gz
sudo dpkg -i gaim-extprefs_0.4-1_i386.deb

```

Restart Gaim, activate the plugin, set it up, job's done. ;)

---

### Post by Shambler on 2005-03-03
Hm, I installed the package, but in Gaim preferences/Plugins I cannot see it...

---

### Post by Shambler on 2005-03-03
When I compile it from source, it works. Strange though...

---

### Post by p!=f on 2005-03-03
[QUOTE=Shambler]Hm, I installed the package, but in Gaim preferences/Plugins I cannot see it...[/QUOTE]
I'm on Hoary (Gaim 1.1.4) so if you use Warty it won't work.

---

### Post by Shambler on 2005-03-03
I'm on Hoary, too (as well as Gaim 1.1.4)

---

### Post by p!=f on 2005-03-03
Wierd. There's nothing special and the package has cca 4kB. 
If anyone else can try the attached package and confirm if it works or not, I'll be gratefull.

---

### Post by SUSPECT on 2005-05-04
I tried the .deb package and it did not work as well.

I tried to compile it from source but I get a lot of errors, I think the problem is that I don't have the gtk+-2.0 package but I can't find it on synaptic. :(

Any help is appreciated.

EDIT:
Forgot to mention i'm on Hoary with gaim 1.1.4

---

### Post by word_virus on 2005-07-06
Originally tried to install the gaim extended prefs plug-in from source.  Installed gaim-dev from synaptic and the required dependancy.  Could not compile, exited with multiple errors during 'make'.  Downloaded Debian package I found here on the forums and installed with `dpkg -i', selected it in the Gaim plug-ins list, restarted Gaim and it works like a charm!  No more buddy list cluttering the desktop at start-up.  Thanks!

I'm on Ubuntu Hoary with the most recent gaim that's not a backport. Hope this helps anyone having trouble!

---

