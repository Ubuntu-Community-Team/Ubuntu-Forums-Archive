---
title: "Whrere's the config file of vinagre?"
date: 2008-05-27
forum: Desktop Environments
---

### Post by saffolino on 2008-05-27
Hi, where can I find the config file of vinagre?

---

### Post by saffolino on 2008-05-29
No idea?

---

### Post by dustigroove on 2008-07-01
> **saffolino said:**
> Hi, where can I find the config file of vinagre?

This reply may be a bit late, but as I have just now come across your question and it was never answered I feel obliged to post.  :)

Vinagre uses the Gconf configuration database for saving its settings. The file is located here: ~/.gconf/apps/vinagre/%gconf.xml

However it may ultimately be better to just use the gconf-editor or Vinagre's built in preferences to make any changes.

Cheers,

---

### Post by benste on 2008-09-20
i know this post is written at an older date,
but I want to thank you for your solution,
I really needed the vnc solution yesterday, but someone disconnected my network during a fullscreen remote.
Afterwards I wasn't able to start the program, only a white screen appeared.

---

### Post by bobbob1016 on 2008-10-11
The white screen is vinagre starting in fullscreen with nothing to display.  A hack to get this working is by typing "vinagre reset" or you can substitute anything instead of reset, basically this forces it to get an error and go out of fullscreen.

---

### Post by benste on 2008-10-11
thx, sounds faster

---

### Post by mavitm3 on 2008-11-17
That worked for me, thanks very much.

---

### Post by gcbzzzz on 2008-11-26
I ssh to a host i use vinagre often, and wanted to get the IP from the recent connection list. but that file only has UI stuff.

anyone knows where I can find the saved last connections that vinagre displays to you?


```

<?xml version="1.0"?>
<gconf>
        <entry name="window_height" mtime="1227648058" type="int" value="1025">
        </entry>
        <entry name="window_width" mtime="1227648058" type="int" value="1280">
        </entry>
        <entry name="window_state" mtime="1227633537" type="int" value="4">
        </entry>
        <entry name="side_panel_size" mtime="1225928919" type="int" value="123">
        </entry>
        <entry name="statusbar_visible" mtime="1227629148" type="bool" value="true">
        </entry>
        <entry name="toolbar_visible" mtime="1225930975" type="bool" value="false">
        </entry>
        <entry name="side_pane_visible" mtime="1225930976" type="bool" value="false">
        </entry>
</gconf>

```

---

### Post by gcbzzzz on 2008-11-26
duh. found. 

~/.local/share/vinagre/history

simple ```
find . -name vinagre
``` did the trick

---

### Post by s3a on 2012-01-03
Thanks gcbzzzz, Post #9 did it for me.

---

### Post by oldos2er on 2012-01-03
Closed, necromancy.

---

