---
title: "Update errors, please help"
date: 2009-01-20
forum: General Help
---

### Post by aykc88 on 2009-01-20
I've searched the archive and tried the following:
sudo dpkg --configure --force-all -a

What I got is:

Setting up gnome-power-manager (2.24.0-0ubuntu8.2) ...

(gconftool-2:9014): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-cs.xml": Line 8071 character 50: No text is allowed inside element <local_schema>

(gconftool-2:9014): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-nl.xml": Line 7298 character 50: No text is allowed inside element <local_schema>

(gconftool-2:9014): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-it.xml": Error on line 4873 char 99: Odd character '<', expected a '>' or '/' character to end the start tag of element 'loca', or optionally an attribute; perhaps you used an invalid character in an attribute name

(gconftool-2:9014): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-en_GB.xml": Line 7521 character 36: No text is allowed inside element <local_schema>

(gconftool-2:9014): GConf-CRITICAL **: Failed to load file "/var/lib/gconf/defaults/%gconf-tree-ar.xml": Error on line 9062 char 81: Odd character '<', expected a '>' or '/' character to end the start tag of element 'local_s', or optionally an attribute; perhaps you used an invalid character in an attribute name
**
GConf-Backends:ERROR:markup-tree.c:3378:end_element_handler: assertion failed: (g_slist_length (info->local_schemas) == 1)
dpkg: error processing gnome-power-manager (--configure):
 subprocess post-installation script returned error exit status 250
Errors were encountered while processing:
 gnome-power-manager

Can someone help?

Thanks!

---

### Post by Hagbard on 2009-01-22
I have also encountered this error. It renders gnome basically unusable. I have done both a fresh install using the alternate CD and an upgrade from hardy heron. Both produce a metacity that segfaults when attempting to run.

Any help?

---

