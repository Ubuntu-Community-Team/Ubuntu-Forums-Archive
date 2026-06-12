---
title: "freemind doesn't start and got out of memory"
date: 2005-12-19
forum: General Help
---

### Post by gix on 2005-12-19
Hi all
I've just installed freemind through the following repository:
```
deb http://eric.lavar.de/comp/linux/debian/ experimental/
```

When I launch freemind from the command line I've got this output:

```

<user>@<host>:~$ freemind

Looking for user properties:
/home/<user>/.freemind/user.properties

User properties found.
Default (System) Look & Feel: javax.swing.plaf.metal.MetalLookAndFeel
Warning - resource string not found:property_dialog
Warning: the font you have set as standard - null - is not available.
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module.
19-dic-2005 10.59.39 freemind.modes.ModesCreator getAllModes
INFO: Modes:[freemind.modes.browsemode.BrowseMode, freemind.modes.filemode.FileMode, freemind.modes.mindmapmode.MindMapMode]
19-dic-2005 10.59.39 freemind.modes.ModesCreator getMode
INFO: Initializing mode MindMap
Warning - resource string not found:undo
Warning - resource string not found:redo
Warning - resource string not found:underlined
Warning - resource string not found:font_size
Warning - resource string not found:font_family
Warning - resource string not found:edit_node
Warning - resource string not found:add_link
Warning - resource string not found:change_arrows_in_arrow_link
Warning - resource string not found:node_background_color
Warning - resource string not found:remove_node_background_color
Warning - resource string not found:add_local_link
Warning - resource string not found:goto_link_node_action
Warning - resource string not found:reset_node_position
Warning - resource string not found:change_link_arrows
Warning - resource string not found:RevertAction
Warning - resource string not found:select_branch
Warning - resource string not found:select_all
19-dic-2005 10.59.39 freemind.modes.mindmapmode.MindMapController <init>
INFO: createIconActions
Warning - resource string not found:icon_full-1
Warning - resource string not found:icon_full-1
Warning - resource string not found:icon_full-2
Warning - resource string not found:icon_full-2
Warning - resource string not found:icon_full-3
Warning - resource string not found:icon_full-3
Warning - resource string not found:icon_full-4
Warning - resource string not found:icon_full-4
Warning - resource string not found:icon_full-5
Warning - resource string not found:icon_full-5
Warning - resource string not found:icon_full-6
Warning - resource string not found:icon_full-6
Warning - resource string not found:icon_full-7
Warning - resource string not found:icon_full-7
19-dic-2005 10.59.39 freemind.modes.mindmapmode.MindMapController <init>
INFO: createNodeHookActions
Exception in thread "main" java.lang.OutOfMemoryError

```

soooooo sad :(

---

### Post by BathroomNinja on 2005-12-19
By any chance, did you follow the guide? [https://wiki.ubuntu.com/FreeMindInBreezy](https://wiki.ubuntu.com/FreeMindInBreezy)

---

### Post by gix on 2005-12-19
[QUOTE=BathroomNinja]By any chance, did you follow the guide? [https://wiki.ubuntu.com/FreeMindInBreezy](https://wiki.ubuntu.com/FreeMindInBreezy)[/QUOTE]

uhmmm, no I didn't follow these instructions ... thanks guy, I'll try them!

---

### Post by BathroomNinja on 2005-12-19
Good stuff.  Let me know how it goes.

---

### Post by gix on 2005-12-19
thank you man!
the wiki-howto is simple and clean!

keep on *buntu-ing! ;-)

---

