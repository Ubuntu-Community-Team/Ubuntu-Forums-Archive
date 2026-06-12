---
title: "How to change computertemp applet background color to match curent theme?"
date: 2010-06-19
forum: Desktop Environments
---

### Post by impact on 2010-06-19
The Computer Temperature Monitor Applet's background color stays constant and ignores current theme settings. 

I have attached a picture which shows the Radiance theme with the applet on the top bar. Notice how the background under the applet is a completely different color than the rest of the applets?

Is there any way to fix this?

---

### Post by infinito on 2010-06-28
This bug is fixed in current svn trunk. To install enter these commands on terminal:

```
$ sudo apt-get remove --purge computertemp
$ sudo apt-get build-dep computertemp
$ sudo apt-get install gnome-common subversion
$ svn co [http://svn.infinicode.org/computertemp/trunk/computertemp](http://svn.infinicode.org/computertemp/trunk/computertemp)
$ cd computertemp
$ sh autogen.sh --prefix /usr
$ make
$ sudo make install
```

---

### Post by phosphoricx on 2010-08-27
You can also use checkinstall to make the sources into a package and install them: 

[     https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by Budchekov on 2010-09-28
Hi,

I'm experiencing the same white background as impact.
I tried the code suggested  by infinito but it was not recognized, didn't work.
Any ideas, it looks so darned ugly, using 10.04 and  Bisigi Exotic panel. 

Edit: I guess the key is SVN trunk, looks like a whole lot of work to simply chance a background color.

Thanks, guess I'll live with it.

---

### Post by stinkeye on 2010-09-29
See this post....
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9629583&postcount=5[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9629583&postcount=5")

---

### Post by Budchekov on 2010-10-02
Checked out that link, no such file exists to edit.

Thanks for trying, it's no big deal, simpler to just use sensors-applet, I give up !

---

### Post by stinkeye on 2010-10-03
It's there.
Each theme has it's own gtkrc file.
Eg for the Ambiance theme it will be in the
**/usr/share/themes/Ambiance/gtk-2.0** folder.

Then, because the themes in usr/share/themes are owned by root
you would use in the terminal.
```
gksudo gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```

or 
start the file browser with root privileges with
```
gksudo nautilus
```
and navigate to the gtkrc file.

If the theme has a **panel.rc** file you will need to edit that file.

---

### Post by Budchekov on 2010-10-03
Thanks stinkeye, I should have said I found the file but couldn't fine the code posted.
I'll give it a go again later and report back.
I'm new at this stuff and haven't been brave enough to touch anything root related...yet.
 

Edit: OK found Exotic panel.rc file and put a hash mark in front of 'bg_pixmap [NORMAL] = "panel.png" '.
Saved , logged off/in and it didn't work. Tried it with a space after the hash mark too.

Edit: Solved ! appended this line as described here, it worked

[[gnome] Customising gnome panel applets - Page 2 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=884268&page=2")

@Thanks for your help with the 'root stuff' stinkeye,__ think I'm figuring things out. :)

---

### Post by impact on 2011-02-16
Thank you infinito and phosphoricx, it worked perfectly. I managed to download, compile and install the resulting package without a hitch and the background problem is fixed.

---

### Post by wooleyte on 2011-05-11
> **Budchekov said:**
> ...simpler to just use sensors-applet, I give up !


I tried everything this thread said, and I have come to the conclusion that this statement is true.

---

