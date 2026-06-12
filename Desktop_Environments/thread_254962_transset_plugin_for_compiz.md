---
title: "transset plugin for compiz"
date: 2006-09-10
forum: Desktop Environments
---

### Post by ghotra on 2006-09-10
I have a working aiglx install and I am trying to get the transset plugin working in compiz.  I've downloaded libtransset.so from:

[http://www.ubuntuforums.org/showpost.php?p=839591&postcount=629](http://www.ubuntuforums.org/showpost.php?p=839591&postcount=629)

and did:

$ sudo cp libtransset.so /usr/lib/compiz/

With gconf-editor, I edited the active_plugins key in /apps/compiz/general/allscreens/options

In that key, I placed 'transset' after 'decoration' and before 'wobble'.

As far as I know, that is all I need to do to get compiz to use the plugin.  Is that correct?

I know I need to add a key named 'apps' with value 'Gnome-terminal 85'...but I don't know where or how I need to add it.  Can someone help me? Also, is the key supposed to be a list or a string?

Basically, I'm looking to get the transset plugin working.

---

### Post by ghotra on 2006-09-11
Bumping...I know someone knows how to do this.

---

