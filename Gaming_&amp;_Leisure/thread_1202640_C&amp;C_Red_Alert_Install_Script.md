---
title: "C&amp;C Red Alert Install Script"
date: 2009-07-02
forum: Gaming &amp; Leisure
---

### Post by Thelasko on 2009-07-02
I've been working on this for a while.  It's an installation script for Command & Conquer: Red Alert.  It utilizes DosBox, so if you are a DosBox user, this may corrupt your settings.  It does download Red Alert from the EA website.  As far as I am aware, this is allowed by the EULA.  This script does not contain a copy of the game.  It is intended as an aid to users who wish to run this game under Ubuntu.  It has been tested on Ubuntu 8.04 only.  

**USE AT YOUR OWN RISK!**

Known issues:
The installation file may crash after installing.  It will display, "please stand by" on the screen.  **Release your curer by pressing ctrl+F10**, and close the window.  The program should still work.
It does not install the Soviet disk.  However, someone knowledgeable in bash could easily figure out how to do it with my script.
It does not remove any unnecessary installation files.  **Be sure you have plenty of space available on your hard drive.**
It does not add RedAlert to the applications menu.  You must do this manually.  **To run the program you must run the script called "redalert1" under the /home/.dosbox folder.**

---

### Post by Thelasko on 2009-07-06
I am attaching a copy of a script I wrote that will install* Command & Conquer: Red Alert* automatically using DosBox.  Be aware that this file does not contain the program, but will download it from EA's website.  As far as I know, this is not against the EULA.  I have only tested it with 64-bit Hardy Heron.  Please, **USE AT YOUR OWN RISK!**

Known issues:
[LIST]
[*]The installation program may freeze after the installation is complete.  This is normal.  **Press ctrl+F10 and close the window.**
[*]A link is not made in the Applications menu.  Instead you must **run a script called redalert1 in the location home/.dosbox/.**
[*]The script does not delete all of the files it downloads.  Only the iso image is necessary.  The .rar files may be deleted.
[*]It currently works for the allied disk only.
[/LIST]
Beware, installing RA requires significant disk space. Greater than 1.4GB.

Please let me know what you think.
Thanks

---

### Post by jpeddicord on 2009-07-07
Moved to Gaming, as this is a script and not really a tutorial.

---

### Post by Thelasko on 2009-07-07
Thanks, Unfortunately I realized this myself.  I Thought my original post was deleted, and reposted in gaming already.

---

### Post by jpeddicord on 2009-07-07
> **Thelasko said:**
> Thanks, Unfortunately I realized this myself.  I Thought my original post was deleted, and reposted in gaming already.

's ok. Merged it with this thread. :)

---

### Post by Thelasko on 2009-07-07
Thanks again!

---

### Post by rCXer on 2009-07-08
Thanks for posting this.  I am currently playing through c&c1.

---

### Post by Thelasko on 2010-06-15
The script appears to be broken in Lucid Lynx.  

"DOS/4GW professional error (2000)"

I don't know what that means.  When I find out, I'll try to fix the script.

---

### Post by Thelasko on 2010-09-12
There doesn't appear to be anything wrong with the script.  I had an old doxbox.conf file that was causing trouble.  It works fine.

---

