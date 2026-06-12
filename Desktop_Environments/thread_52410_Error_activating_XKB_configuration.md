---
title: "Error activating XKB configuration"
date: 2005-07-27
forum: Desktop Environments
---

### Post by LazyIvan on 2005-07-27
For about the past few weeks, I have had an error message pop up upon each fresh boot.  I have searched the forums, and found solutions to this problem, but it was for the Warty release and included using an xorg.conf file, of which I am already using.  I have re-ran fglrxconfig to generate a new xorg.conf file but it still has the same error upon a fresh boot.  Here is the text from the error message:

"Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>"

Does anyone have any ideas on how to fix this?  It does not seem to have any influence on how the system runs, but I figure it can't be good to have an error pop up on every boot.  Thanks for any input you may have.

---

### Post by huwshimi on 2005-07-27
Are you running Hoary or Breezy? If you are running Breezy there's a whole list of solutions in the dev forums.

---

### Post by LazyIvan on 2005-07-27
Sorry, forgot to mention that I am running Hoary 5.04, and that this problem was not occuring before I got my ati video drivers working.  It started showing up partway through my attempts at getting those to work, and the information that I have found on the forums all relates to the Breezy version of Ubuntu, and if i recall correctly that entailed moving from an XFree86 config file to using xorg.conf.  Here is a link to my Xorg.0.log from a clean boot if that helps as well: [Xorg.0.log](http://www.uweb.ucsb.edu/~cabair)

---

### Post by djSHY on 2005-07-28
i have the exact problem and it havent been occurring before i installed the gfx drivers either.. as the error askes to include result of xprop -root | grep XKB, here it is:

[B]_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "xorg", "sk-qwerty", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "xorg", "sk-qwerty", "", ""[/B]

and gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd:

[B] layouts = [us]
 model = pc105
 overrideSettings = true
 options = []
[/B]

thanks in advance

---

### Post by bdamon on 2005-07-28
This is what worked for me.

cd /etc/X11/xkb/rules
sudo ln -s xorg.lst xfree86.lst

Another possibility, check your xorg.conf file for 

Option "XkbRules" "xorg"
or
Option "XkbRules" "xfree86"

it should read "xorg" and not "xfree86"



Ben

---

### Post by LazyIvan on 2005-07-28
No luck with those solutions, bdamon, even though my Option "XkbRules" was "xfree86" instead of "xorg".
All that happened was to cause 2 of the same error messages (the same as listed above) to pop up on a reboot, and another information panel saying:
> The X system keyboard settings differ from your current GNOME keyboard settings.  Which set would you like to use?

This leads me to believe that there are 2 conflicting keyboard settings files that it can possibly use, rather than only /etc/X11/xorg.conf

If this suspicion is true, then does anyone know where the GNOME keyboard settings are stored?

Also - here is the results of my xprop -root | grep XKB:

> _XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc101", "en_US", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc101", "en_US", "", ""

I cannot perform the gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd as it seems I have no /desktop directory and and am unsure where the actual gnome directory would be.

Thanks in advance.

---

### Post by charlieg on 2005-07-28
[QUOTE=LazyIvan]I cannot perform the gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd as it seems I have no /desktop directory and and am unsure where the actual gnome directory would be.[/QUOTE]
Nobody does, it's not a standard posix directory.

Anyway, this should locate that for you:
```
sudo find / -name peripherals
```
Warning: it may take a little while (10-15 minutes).

---

### Post by jamesrw on 2005-08-22
[QUOTE=bdamon]This is what worked for me.

cd /etc/X11/xkb/rules
sudo ln -s xorg.lst xfree86.lst

Another possibility, check your xorg.conf file for 

Option "XkbRules" "xorg"
or
Option "XkbRules" "xfree86"

it should read "xorg" and not "xfree86"



Ben[/QUOTE]

thanx

---

### Post by refdoc on 2005-09-07
I have the same problem, I use a gb and and an ir keymap. The problem persist despite having checked all the above.

Thanks for any advise.

I am using breezy

---

### Post by panabar on 2005-10-25
I was having problems with xkb layout, and somewhere in the forums someone mentioned copying the /etc/X11/xkb directory from the live breezy cd to installed breezy  and then 

$ setxkbmap xx

where xx is the code of your keyboard map (mine is tr)  solves the problem.

Beause I didn't have the live cd I copied the /etc/X11/xkb/ directory from my hoary installation and pasted (after making a backup copy of /etc/X11/xkb/ directory ) it over the breezy installations /etc/X11/xkb/ directory. Then I executed the command and my keyboard was running with all keys working.  :)
But chaning the keyboard from keyboar selector still produced the same problem  :( , so I rebooted and got the same xkb error at the startup.  so I issued the same "setxkbmap tr" command and my keyboard was working again.  This seemed a decent enough solution until an update solved the problem, BUT after rebooting again xkb error disappeared. I don't know how or why but it dissappeared.

I hope This helps.

---

### Post by gerbman on 2005-10-28
[QUOTE=bdamon]Another possibility, check your xorg.conf file for 

Option "XkbRules" "xorg"
or
Option "XkbRules" "xfree86"

it should read "xorg" and not "xfree86"[/QUOTE]

Thanks.  That fixed it.

---

