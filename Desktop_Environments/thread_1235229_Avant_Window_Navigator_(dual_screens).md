---
title: "Avant Window Navigator (dual screens)"
date: 2009-08-08
forum: Desktop Environments
---

### Post by mcgodx on 2009-08-08
Hey all,

I am trying to get my Gnome setup just as I want, and I am running into a slight problem.  I installed AWN (much improved since the last time I used it by the way!), but there's one minor issue.  It's putting the dock on the bottom of my left monitor, and I'd like for it to be on the bottom of my right monitor (which is where the Gnome panel is).  I usually use the left monitor for video-watching and such, so I would like to keep that open if I can.

I found a howto saying to change my ~/.gconf/apps/avant-window-navigator/%gconf.xml file but the problem is it doesn't have the lines they are referring to inside it, and I don't know where I would add those lines.  

An example of the lines I am supposed to be looking for is 

```
        <entry name="monitor_height" mtime="1179886419" type="int" value="1024">
        </entry>
        <entry name="monitor_width" mtime="1179886419" type="int" value="1280">
        </entry>
```

However here are the contents of my file:

```
<?xml version="1.0"?>
<gconf>
	<entry name="panel_mode" mtime="1249779736" type="bool" value="true"/>
	<entry name="applets_list" mtime="1249779053" type="list" ltype="string">
		<li type="string">
			<stringvalue>/usr/share/avant-window-navigator/applets/animal-farm.desktop::1249779046</stringvalue>
		</li>
		<li type="string">
			<stringvalue>/usr/share/avant-window-navigator/applets/taskman.desktop::1</stringvalue>
		</li>
	</entry>
</gconf>
```

Any help would be greatly appreciated!

Both of my monitors are 1920x1080 by the way, not 1280x1024.

---

