---
title: "Absolutely Friggin' Annoying"
date: 2009-03-02
forum: General Help
---

### Post by ACQ on 2009-03-02
Hello all you Ubuntu geeks. Explain this to me please: I want to have scripts in the Nautilus right-click menu. Every Google search I've made has given me instructions to put my scripts into the ~/.gnome2/nautilus-scripts folder. What absolutely friggin' annoys me is that I DO NOT HAVE A DAMN .gnome2 DIRECTORY AND NONE OF THESE TUTORIALS EXPLAINS HOW TO PUT IT THERE@#!~!!! ](*,) I turned on "Display Hidden Files" and it still ain't there. The assumption that everyone just magically has this path with no exception that it may not be there only further aggravates me! *takes a deep breath* 

I decided to create the folders myself as root, but guess what? Not working. Where, *mon frairs*, might I find instructions on how to setup my scripts folder and thus add to my right-click menu? 

I can't help but get angry about this because every time I try getting into Ubuntu to break the M$ addiction it's stupid stuff like this that makes me format and reinstall Windows.

If the solution is right under my nose, please, consider me apologetic. I appreciate your help, ladies and gentlemen. Good day. :-)

---

### Post by taurus on 2009-03-02
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by ACQ on 2009-03-02
total 248
drwxr-xr-x 38 acq  acq      4096 2009-03-02 11:38 .
drwxr-xr-x  5 root root     4096 2009-03-02 11:38 ..
drwx------  3 acq  acq      4096 2009-02-27 13:57 .adobe
-rw-------  1 acq  acq       637 2009-02-27 15:58 .bash_history
drwx------  6 acq  acq      4096 2009-02-27 15:13 .BitTornado
drwxr-xr-x  5 acq  acq      4096 2009-02-27 13:42 .cache
drwxr-xr-x  2 acq  acq      4096 2009-03-02 11:31 .cellwriter
drwx------  3 acq  acq      4096 2009-02-27 12:20 .compiz
drwxr-xr-x  9 acq  acq      4096 2009-02-27 15:15 .config
drwx------  3 acq  acq      4096 2009-02-27 10:39 .dbus
drwxr-xr-x  2 acq  acq      4096 2009-02-27 14:56 Desktop
-rw-------  1 acq  acq         2 2009-02-27 12:21 .dmrc
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 Documents
drwxrwx---  5 root plugdev 32768 2009-03-02 10:50 dumpster
-rw-------  1 acq  acq        16 2009-02-27 10:39 .esd_auth
drwxr-xr-x  3 acq  acq      4096 2009-02-27 14:02 .evolution
drwxr-xr-x  2 acq  acq      4096 2009-03-02 11:24 .fontconfig
drwx------  5 acq  acq      4096 2009-03-02 11:24 .gconf
drwx------  2 acq  acq      4096 2009-03-02 11:40 .gconfd
-rw-r-----  1 acq  acq         0 2009-03-02 11:38 .gksu.lock
drwx------  9 acq  acq      4096 2009-03-02 10:54 .gnome2
drwx------  2 acq  acq      4096 2009-02-27 10:39 .gnome2_private
drwx------  2 acq  acq      4096 2009-02-27 10:39 .gnupg
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 .gstreamer-0.10
-rw-r--r--  1 acq  acq       100 2009-02-27 15:14 .gtk-bookmarks
dr-x------  2 acq  acq         0 2009-02-27 12:21 .gvfs
-rw-------  1 acq  acq       318 2009-02-27 12:21 .ICEauthority
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:42 .icons
drwx------  3 acq  acq      4096 2009-02-27 10:39 .local
drwx------  3 acq  acq      4096 2009-02-27 13:57 .macromedia
drwx------  4 acq  acq      4096 2009-02-27 10:39 .mozilla
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 Music
drwxr-xr-x  3 acq  acq      4096 2009-02-27 12:20 .nautilus
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 Pictures
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 Public
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 .pulse
-rw-------  1 acq  acq       256 2009-02-27 10:39 .pulse-cookie
drwx------  6 acq  acq      4096 2009-03-02 12:06 .purple
-rw-------  1 acq  acq     11425 2009-03-02 11:38 .recently-used.xbel
-rw-r--r--  1 acq  acq         0 2009-02-27 10:49 .sudo_as_admin_successful
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 Templates
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:42 .themes
drwx------  4 acq  acq      4096 2009-02-27 13:42 .thumbnails
drwxr-xr-x  2 acq  acq      4096 2009-02-27 11:08 .update-manager-core
drwx------  2 acq  acq      4096 2009-02-27 12:34 .update-notifier
drwxr-xr-x  2 acq  acq      4096 2009-02-27 10:39 Videos
drwxr-xr-x  4 acq  acq      4096 2009-03-02 10:56 .wine
-rw-------  1 acq  acq       117 2009-02-27 12:21 .Xauthority
-rw-r--r--  1 acq  acq     30901 2009-03-02 11:34 .xsession-errors

---

### Post by Rallg on 2009-03-02
Hmm, the output shows that you absolutely friggin' have the necessary folder. It is located in your user home directory (turn on hidden). I have the necessary folder (and its subfolders) even though I've never made a custom nautilus script. So you shouldn't have to create any folders: They are there.

Hope that absolutely friggin' helps.

---

### Post by ACQ on 2009-03-02
> **Rallg said:**
> Hmm, the output shows that you absolutely friggin' have the necessary folder. It is located in your user home directory (turn on hidden). I have the necessary folder (and its subfolders) even though I've never made a custom nautilus script. So you shouldn't have to create any folders: They are there.

Hope that absolutely friggin' helps.

ROFL

Right, but I'm the goof who put it there as root! Does that matter?

---

### Post by Slim Odds on 2009-03-02
> **ACQ said:**
> ROFL

Right, but I'm the goof who put it there as root! Does that matter?

It's not owned by root, it's owned by you.

> drwx------  9 [COLOR=Red]acq  acq [/COLOR]     4096 2009-03-02 10:54 .gnome2

---

### Post by taurus on 2009-03-02
> **ACQ said:**
> ROFL

Right, but I'm the goof who put it there as root! Does that matter?

Maybe the other one that you created as root was in friggin' /root/.gnome2.

---

### Post by ACQ on 2009-03-02
> **Slim Odds said:**
> It's not owned by root, it's owned by you.

Probably because I used the "gksudo nautilus &" command to make it. Should I remove it?

---

### Post by Simian Man on 2009-03-02
> **ACQ said:**
> 
I can't help but get angry about this because every time I try getting into Ubuntu to break the M$ addiction it's stupid stuff like this that makes me format and reinstall Windows.


So how would you go about writing Windows Explorer scripts?

Also are you running Gnome?  What is the output of
```
ls ~/.gnome2
```
?

---

### Post by ACQ on 2009-03-02
> **Simian Man said:**
> So how would you go about writing Windows Explorer scripts?

Also are you running Gnome?  What is the output of
```
ls ~/.gnome2
```
?

I don't write scripts. I just copy/paste them from the web.

Yes, I'm running Gnome in Ubuntu 8.10.

Here's the output:
```
accels		 file-roller	     keyrings	       panel2.d
accelsgedit	 gedit-2	     nautilus-scripts  share
backgrounds.xml  gedit-metadata.xml  nautilus-sendto
```

---

### Post by bostonaholic on 2009-03-02
> **ACQ said:**
> I don't write scripts. I just copy/paste them from the web.

Yes, I'm running Gnome in Ubuntu 8.10.

Here's the output:
```
accels		 file-roller	     keyrings	       panel2.d
accelsgedit	 gedit-2	     **nautilus-scripts**  share
backgrounds.xml  gedit-metadata.xml  nautilus-sendto
```

So there's your answer right there.  The folder is there in ~/.gnome2/nautilus-scripts.

---

### Post by Rallg on 2009-03-02
And, once you find your way to the correct subfolder in your home directory, just drop the friggin' script in. Don't use sudo or gksudo anything. Once it's there, you probably need to right-click the file, Properties, permission, and make it executable.

If you wish, you can make a new menu item that launches the script, as if it were an application: System, Preferences, Main Menu, pick your favorite classification, New Item. Application in Terminal. Describe it as you wish. The command would be
/path/to/your-script.sh
if measured from the top of the file system. In your case
~/.gnome2/nautilus-scripts/your-script.sh
does it, since the tilde measures from the user home directory.

---

### Post by bostonaholic on 2009-03-02
> **Rallg said:**
> And, once you find your way to the correct subfolder in your home directory, just drop the friggin' script in. Don't use sudo or gksudo anything. Once it's there, you probably need to right-click the file, Porperties, permission, and make it executable.

If you wish, you can make a new menu item that launches the script, as if it were an application: System, Preferences, Main Menu, pick your favorite classification, New Item. Application in Terminal. Describe it as you wish. The command would be /path/to/your-script.sh if measured from the top of the file system In your case ~/.gnome2/nautilus-scripts/your-script.sh does it, **since the tilde measures from the user home directory.**

That's maybe what the OP is confused about?  ```
~/.gnome2/nautilus-scripts
``` is not the same as ```
/.gnome2/nautilus-scripts
``` it is most likely ```
/home/<username>/.gnome2/nautilus-scripts
```

---

### Post by ACQ on 2009-03-02
FFFFFFUUUUUUUUU----!

I found the problem. The tutorials *assumed* anyone who read them would know that the friggin' tilde before the path meant "user's home folder". MAN I HATE THAT!

You've all been more than helpful. Please excuse my ranting as it's mostly in jest (it's how I deal with frustration rather than break something). I appreciate the effort from each of you and sincerely thank you. :-)

---

