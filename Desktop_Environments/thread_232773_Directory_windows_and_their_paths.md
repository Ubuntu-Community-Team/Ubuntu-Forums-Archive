---
title: "Directory windows and their paths"
date: 2006-08-09
forum: Desktop Environments
---

### Post by anroy on 2006-08-09
I often have to deal with full paths to directories.

When you are viewing a directory window, Ctrl-l displays this full path in a Location bar.

1) Does anyone know how to make this Location bar always appear by default, whenever I open a new window?  I don't want to have to hit Ctrl-l every time.

2) In KDE directory windows have a menu item that opens the console terminal with the current directory set to that directory.  I can't find such a menu item in Ubuntu windows.  Even in Windows you can install a small utility called "Command Prompt Here".  I am finding it pretty inconvenient not having such a thing.

---

### Post by ajgreeny on 2006-08-09
Is this question about nautilus and gnome?  In KDE, konqueror gives the full address of the file or folder open in the address bar, or at least it does on my system, I don't know if it is the default.  I do agree, however, it's very useful to know where you are all the time.

---

### Post by bscbrit on 2006-08-09
This script will do what you want for opening a terminal

```

#!/usr/bin/perl -w
#
# Open terminal here
#
# Nautilus script that opens a gnome-terminal at the current location, if it's
# a valid one. This could be done in shell script, but I love Perl!.
#
# 20020930 -- Javier Donaire <jyuyu@fraguel.org>
# http://www.fraguel.org/~jyuyu/
# Licensed under the GPL v2+
#
# Modified by: Dexter Ang [thepoch@mydestiny.net]
# 2003-12-08: Modified for Gnome 2.4
#		- Added checking if executed on Desktop "x-nautilus-desktop:///"
#		  so that it opens in /home/{user}/Desktop

use strict;

$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
if ($_ and m#^file:///#) {
  s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
  s#^file://##;
  exec "gnome-terminal --working-directory='$_'";
}

# Added 2003-12-08 Dexter Ang
if ($_ == "x-nautilus-desktop:///") {
  $_ = $ENV{'HOME'};
  $_ = $_.'/Desktop';
  exec "gnome-terminal --working-directory='$_'";
}

```

Save it in ~/.gnome2/nautilus-scripts/Open_Dir

Make sure it is executable and it will then appear in the scripts field when you right-click.

There is another way of doing this, but I cannot for the life of me remember how to do it!

---

### Post by Ramses de Norre on 2006-08-09
To question 1: ```
gconf-editor /apps/nautilus/preferences/
``` and check "always_use_location_entry", you can set this somewhere in the preferences dialog of nautilus too.

---

### Post by anroy on 2006-08-10
> **Ramses de Norre said:**
> To question 1: ```
gconf-editor /apps/nautilus/preferences/
``` and check "always_use_location_entry", you can set this somewhere in the preferences dialog of nautilus too.
Thanks, I found this in the preferences dialog.

From the Help guide:
> To set your preferences for files and folders, choose Edit &#8594; Preferences. Click on the Behavior tab to display the Behavior tabbed section.

Selecting the option "Always use text entry location bar" accomplishes what I was looking for.

---

### Post by anroy on 2006-08-10
> **bscbrit said:**
> This script will do what you want for opening a terminal

```

#!/usr/bin/perl -w
#
# Open terminal here
#
# Nautilus script that opens a gnome-terminal at the current location, if it's
# a valid one. This could be done in shell script, but I love Perl!.
#
# 20020930 -- Javier Donaire <jyuyu@fraguel.org>
# http://www.fraguel.org/~jyuyu/
# Licensed under the GPL v2+
#
# Modified by: Dexter Ang [thepoch@mydestiny.net]
# 2003-12-08: Modified for Gnome 2.4
#		- Added checking if executed on Desktop "x-nautilus-desktop:///"
#		  so that it opens in /home/{user}/Desktop

use strict;

$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
if ($_ and m#^file:///#) {
  s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
  s#^file://##;
  exec "gnome-terminal --working-directory='$_'";
}

# Added 2003-12-08 Dexter Ang
if ($_ == "x-nautilus-desktop:///") {
  $_ = $ENV{'HOME'};
  $_ = $_.'/Desktop';
  exec "gnome-terminal --working-directory='$_'";
}

```

Save it in ~/.gnome2/nautilus-scripts/Open_Dir

Make sure it is executable and it will then appear in the scripts field when you right-click.

There is another way of doing this, but I cannot for the life of me remember how to do it!
Thank you very much :D 

It worked like a charm.

---

