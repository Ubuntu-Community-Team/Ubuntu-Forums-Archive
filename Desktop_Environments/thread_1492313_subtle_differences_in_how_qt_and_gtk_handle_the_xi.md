---
title: "subtle differences in how qt and gtk handle the xim IM_MODULE"
date: 2010-05-24
forum: Desktop Environments
---

### Post by roberto.tomas on 2010-05-24
how do I get compose keys to work the same in qt, x apps like xterm, and gtk apps ? -- seems like a simple enough question right? it's not.




I followed the instructions here: [https://wiki.ubuntu.com/ComposeKey](https://wiki.ubuntu.com/ComposeKey) and that worked, sort of. but I notice some differences. gnome and gtk apps get a different set of compose keys than qt and apps like xedit, xterm, etc. After finding that first wiki page and going through it I found [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey) , but that does not appear to differ substantially in its instructions.


what appears to happen is that, however xim actually returns compose keys to gnome, gnome behaves as if:
1. it first reads the /usr/share/X11/locale/compose.dir and finds the compose file for you locale.
2. it loads those compose key definitions.
3. it loads and overwrites previous definitions with ~/.XCompose definitions, but
4.  it won't load lines with more than 3 keys: compose + the other two. effectively they have to look like dead keys. it won't load lines with more than one character of output. (this is despite the fact that those bounds do not apply in the global Compose file for your locale.) and I *think* it doesn't load files that are "include"-d in the .XCompose file.


for the rest of xwindows, it works like this:
1. it first checks for .XCompose, if it is there, it ignores the global compose file. if it is not there, it loads the global compose file.
2. lt loads all include files in the .XCompose file.
3. it has no restrictions on the number of characters in the compose sequence, nor in the result they return, niether in the local nor global files.

if I could get compose keys to load regardless of layout with ibus, I'd use that. but as things stand with ibus, I understand you have to define eg an ibus-tables map for your compose keys, and the you'd have to define one for each XKB layout you use. this seems impractical.

I've been trying to build a decent kreyòl asyisyen locale for the better part of a month now, and I understand a lot of the system .. with digraphs and multigraphs, this is where I'm at. I have two other issues relating to keyboard layout, if anyone can help me in a general way...  I notice that:



*xedit/xterm, qt, etc do not accept unicode input with ctrl+shift -- in any locale.

*xedit/xterm do not handle custom defined deadkeys in the symbols/xx files -- at least not dead_tilde in the es file specified on the ñ key on my keyboard :)



Any help please?

---

### Post by simosx on 2010-05-24
> **roberto.tomas said:**
> how do I get compose keys to work the same in qt, x apps like xterm, and gtk apps ? -- seems like a simple enough question right? it's not.


GTK+ apps use their own copy of the Compose file from Xorg. The vast majority of compose sequences should continue to work, with a few legacy exceptions. xterm and QT apps use the XOrg compose sequences which is the en_US.UTF-8 file in /usr/share/X11/locate and the ~/.XCompose file if it exists.

The Ctrl+Shift+u feature is a GTK+ feature, so it is not available in xterm or QT apps.

> **roberto.tomas said:**
> 
I followed the instructions here: [https://wiki.ubuntu.com/ComposeKey](https://wiki.ubuntu.com/ComposeKey) and that worked, sort of. but I notice some differences. gnome and gtk apps get a different set of compose keys than qt and apps like xedit, xterm, etc. After finding that first wiki page and going through it I found [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey) , but that does not appear to differ substantially in its instructions.


GTK+ apps have their own copy of compose sequences which is fairly in sync with what is available from X.Org (/usr/share/X11/locale/...).

> **roberto.tomas said:**
> 
what appears to happen is that, however xim actually returns compose keys to gnome, gnome behaves as if:
1. it first reads the /usr/share/X11/locale/compose.dir and finds the compose file for you locale.
2. it loads those compose key definitions.
3. it loads and overwrites previous definitions with ~/.XCompose definitions, but
4.  it won't load lines with more than 3 keys: compose + the other two. effectively they have to look like dead keys. it won't load lines with more than one character of output. (this is despite the fact that those bounds do not apply in the global Compose file for your locale.) and I *think* it doesn't load files that are "include"-d in the .XCompose file.


For a GTK+ file to read your .XCompose (and /usr/share/X11/locale/...), you need to set the variable 'GTK_IM_MODULE' to 'xim'. This bypasses the GTK+ input method, and lets GTK+ apps behave like X apps or QT apps. You lose however features such as Ctrl+Shift+u.

> **roberto.tomas said:**
> 
for the rest of xwindows, it works like this:
1. it first checks for .XCompose, if it is there, it ignores the global compose file. if it is not there, it loads the global compose file.
2. lt loads all include files in the .XCompose file.
3. it has no restrictions on the number of characters in the compose sequence, nor in the result they return, niether in the local nor global files.

if I could get compose keys to load regardless of layout with ibus, I'd use that. but as things stand with ibus, I understand you have to define eg an ibus-tables map for your compose keys, and the you'd have to define one for each XKB layout you use. this seems impractical.


I do not have much experience with IBus; I current view is that it adds some extra complexity and you need in-depth understanding to figure out if something is wrong. You would need to visit the IBus mailing list for help.

> **roberto.tomas said:**
> 
I've been trying to build a decent kreyòl asyisyen locale for the better part of a month now, and I understand a lot of the system .. with digraphs and multigraphs, this is where I'm at. I have two other issues relating to keyboard layout, if anyone can help me in a general way...  I notice that:

*xedit/xterm, qt, etc do not accept unicode input with ctrl+shift -- in any locale.

*xedit/xterm do not handle custom defined deadkeys in the symbols/xx files -- at least not dead_tilde in the es file specified on the ñ key on my keyboard :)

Any help please?

I do not know about the kreyòl asyisyen alphabet and typical keyboard layout. If you can provide info on this for a non-speaker, I might be able to help.

---

### Post by roberto.tomas on 2010-05-24
thank you :)

> **simosx said:**
> GTK+ apps use their own copy of the Compose file from Xorg. The vast majority of compose sequences should continue to work, with a few legacy exceptions. xterm and QT apps use the XOrg compose sequences which is the en_US.UTF-8 file in /usr/share/X11/locate and the ~/.XCompose file if it exists.

that's only if you don't set GTK_IM_MODULE, right?

> **simosx said:**
> The Ctrl+Shift+u feature is a GTK+ feature, so it is not available in xterm or QT apps.

do you know if it is implimented as an XCompose style set of definitons? I'd be happy to hack it out of the source code to give the rest of my system the same functionality if I knew where to look and that it was feasible.

> **simosx said:**
> GTK+ apps have their own copy of compose sequences which is fairly in sync with what is available from X.Org (/usr/share/X11/locale/...).

For a GTK+ file to read your .XCompose (and /usr/share/X11/locale/...), you need to set the variable 'GTK_IM_MODULE' to 'xim'. This bypasses the GTK+ input method, and lets GTK+ apps behave like X apps or QT apps. You lose however features such as Ctrl+Shift+u.

actually I'm not lossing ctl+shift+u

> **simosx said:**
> I do not have much experience with IBus; I current view is that it adds some extra complexity and you need in-depth understanding to figure out if something is wrong. You would need to visit the IBus mailing list for help.

I do not know about the kreyòl asyisyen alphabet and typical keyboard layout. If you can provide info on this for a non-speaker, I might be able to help.

yea sure, but first I'd really like to get all the lines in my XCompose working in gnome. that's gonna be a major part of a haitian language keymap, there's a whole lot of mutligraphs.

---

### Post by simosx on 2010-05-25
> **roberto.tomas said:**
> thank you :)

that's only if you don't set GTK_IM_MODULE, right?

That's right.

> **roberto.tomas said:**
> do you know if it is implimented as an XCompose style set of definitons? I'd be happy to hack it out of the source code to give the rest of my system the same functionality if I knew where to look and that it was feasible.


See the bug report [Configurable compose tables for gtkimcontextsimple.c (patch)]("https://bugzilla.gnome.org/show_bug.cgi?id=155010").

You would probably need to make changes to the GTK+ library, around the file 
[http://git.gnome.org/browse/gtk+/tree/gtk/gtkimcontextsimple.c](http://git.gnome.org/browse/gtk+/tree/gtk/gtkimcontextsimple.c) (see function 'gtk_im_context_simple_add_table()')
Look at the documentation for 'jhbuild' that allows to compile the latest 'gtk+' library only. When you compile your own gtk+ library with your changes, it is possible to run your system applications such ask gedit against your new gtk+ library and therefore test if it works for you.

Good luck! :guitar:

---

