---
title: "Nautilus actions: &quot;This XML file is not a valid Nautilus-actions config file&quot;"
date: 2010-02-18
forum: Desktop Environments
---

### Post by khughitt on 2010-02-18
Hi all,

I've been trying out Nautilus-actions (Gnome 2.28.4), but have been unable to import most config files from [http://www.grumz.net/index.php?q=configlist](http://www.grumz.net/index.php?q=configlist).

When I attempt to import an action, it complains:

> 
Can't parse file 'convert_flv_to_avi.schemas' as GConf schema description file!

This XML file is not a valid Nautilus-actions config file (missing keys: )


So far, the only one that has worked for me is "Move to custom folder" ([http://www.grumz.net/?q=node/260](http://www.grumz.net/?q=node/260)).

Any suggestions? Any help would be appreciated :)

Thanks!

---

### Post by krige on 2010-03-21
I have the same problem trying to import several batch renaming actions, still trying to figuring it out...

---

### Post by cdaaawg on 2010-11-11
I too had this problem when importing nautilus actions. I solved the problem by changing the configuration format version tag near the end of the schema file. The tag looks like this: 

  "<default>1.1</default>" (without the quotes)

Use your favorite text editor to make it look like this:

  "<default>1.0</default>" (without the quotes)

It seems that the parser does not like any version number with a decimal other than 0. I have also changed it to 2.0 with no ill effects. Go figure.

I have no idea what this version number does.

---

