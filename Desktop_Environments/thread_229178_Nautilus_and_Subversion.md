---
title: "Nautilus and Subversion"
date: 2006-08-04
forum: Desktop Environments
---

### Post by timhaughton on 2006-08-04
Hi, I've just installed the Subversion tools and Nautilus scripts to enable SVN operations (a la TortoiseSvn), they seem to install OK, but I'm not seeing any SVN operations available in the Nautilus context menus.

What am I missing?

Cheers,

Tim

---

### Post by moma on 2006-08-04
Hello,

Where have you copied the svn-scripts ?

Untar (unzip) the scripts to ".gnome2/nautilus-scripts/"
Restart Nautilus.

Check:
$ [COLOR="Green"]ls -l $HOME/.gnome2/nautilus-scripts/[/COLOR]
```
total 12
-rwxr--r--  1 moma moma 184 2006-07-28 12:30 gedit-root
drwxr-xr-x 10 moma moma 304 2004-10-03 11:26 nautilus-scripts
drwxr-xr-x  3 moma moma 264 2006-04-02 08:16 nautilus-svn-scripts-0.9.2
-rwxr--r--  1 moma moma 201 2006-07-28 12:30 root-nautilus-here
-rwxr--r--  1 moma moma  67 2006-07-28 12:30 search-here
```

You can test svn checkout usin' this URL: [http://svn.python.org/view/peps](http://svn.python.org/view/peps)

Are you using this? 
o---> [http://marius.scurtescu.com/?p=102]("http://marius.scurtescu.com/?p=102")

---

### Post by timhaughton on 2006-08-04
hmmm, I haven't done any manual copying, I guess I had assumed that the install process would have done it. OK, that's good, should be simple to fix.

OK...where do they get dumped when you've done your apt-get?

(Can you tell this is my second day on Ubuntu? :) )

Cheers,

Tim

---

### Post by moma on 2006-08-04
What is the name of that particular apt-get package ?

---

### Post by timhaughton on 2006-08-04
Just realised you can get the installed files from Synaptic. The docs for it are listed in there. I'll RTFM and post back if I'm still stuck. Many thanks for your help.

Tim

---

### Post by moma on 2006-08-04
Ok. Got it now.

$ [COLOR="Green"]apt-cache search svn | grep nautil us[/COLOR]
nautilus-script-collection-svn - Nautilus subversion management scripts

$ [COLOR="Green"]sudo apt-get install nautilus-script-collection-svn[/COLOR]

Where does it put files, the scripts?
$ [COLOR="Green"]sudo dpkg -L  nautilus-script-collection-svn[/COLOR]
```
/.
/usr/share
.....
[COLOR="Indigo"]/usr/share/nautilus-scripts[/COLOR]
/usr/share/nautilus-scripts/Subversion
/usr/share/nautilus-scripts/Subversion/More...
/usr/share/nautilus-scripts/Subversion/More.../Rename
/usr/share/nautilus-scripts/Subversion/More.../Checkout
....
/usr/share/nautilus-scripts/Subversion/Commit
```
[COLOR="Red"]I restarted Nautilus but the Subversion scripts do not appear in the scrips-menu.[/COLOR]

Did this:
$ [COLOR="Green"]sudo mv  /usr/share/nautilus-scripts/Subversion  $HOME/.gnome2/nautilus-scripts/[/COLOR]
And it works now!

---

### Post by bluevoodoo1 on 2006-10-31
> **moma said:**
> 

Did this:
$ [COLOR="Green"]sudo mv  /usr/share/nautilus-scripts/Subversion  $HOME/.gnome2/nautilus-scripts/[/COLOR]
And it works now!

Great. Thank you!

---

