---
title: "gremlin in FF shortcut key...?"
date: 2011-05-25
forum: Desktop Environments
---

### Post by zika on 2011-05-25
Today I've added FF-trunk on a clean install of NN. It went well, I've changed in Preferred Applications: FF->FF-trunk and ooops, shortcut key (chosen before this addition of FF-trunk) produces, now FF-trunk window (and FF, for what is worth, if I choose FF back in PreferredApplications) that starts FF with some random number as URL, even though it should start with about:blank... If I click on FF, FF-trunk icon in menu, it starts OK. Also, in FluxBox it works like a clock...
Any ideas how to find that gremlin and eradicate it?
In which file is this information stored...?
I know where is information about PreferredApplicatios stored, and it is OK:```

:~/.gconf/desktop/gnome/url-handlers/http$ cat %gconf.xml
<?xml version="1.0"?>
<gconf>
    <entry name="needs_terminal" mtime="1306329201" type="bool" value="false"/>
    <entry name="command" mtime="1306329201" type="string">
        <stringvalue>firefox-trunk %u</stringvalue>
    </entry>
</gconf>
```Numbers are 3354823015, 2787031399,... They change with session, i.e. after I log-out...

---

### Post by zika on 2011-05-27
It is not in```
:~$ cat ~/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml
<?xml version="1.0"?>
<gconf>
    <entry name="volume_up" mtime="1306320332" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Control&gt;Up</stringvalue>
    </entry>
    <entry name="volume_down" mtime="1306320329" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Control&gt;Down</stringvalue>
    </entry>
    <entry name="volume_mute" mtime="1306320279" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Control&gt;m</stringvalue>
    </entry>
    <entry name="home" mtime="1306174721" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Control&gt;&lt;Alt&gt;h</stringvalue>
    </entry>
    <entry name="www" mtime="1306174710" type="string">
        <stringvalue>&lt;Shift&gt;&lt;Control&gt;&lt;Alt&gt;m</stringvalue>
    </entry>
</gconf>

```either... I'll continue searching...

The main question, for me, is: where is the difference between starting FF from the icon in left menu in Unity and starting it with shortcut-key, being written. There is the location of this gremlin which, today, is: [http://3614685543/](http://3614685543/) ...

How did it happen that both FF and FF-trunk got "infected" in course of installing FF-trunk...?
Changing either PreferredApplication or ShortCutKey, of course, doesn't eradicate gremlin...

---

### Post by zika on 2011-05-27
As I've suspected, in Classic mode (no effects) it invokes gremlin, again, so it is not compiz thing, since metacity is, in that case, active...
So, it is sort of Gnome gremlin...
Of course, in Classic, I've used gconf-editor to make new shortcut (metacity) and bypassed Gnome shortcut...
But, still, I'm intrigued to find...
Using gnome.keybinding-properties I've made (add) a new shortcut for FF-trunk (to work in compiz) and it is without gremlin.
So, I need just to find where those &#8222;default&#8220; keybindings (visible in gnome-keybinding-properies) are stored...

---

