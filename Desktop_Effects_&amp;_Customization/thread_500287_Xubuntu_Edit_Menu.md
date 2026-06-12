---
title: "Xubuntu Edit Menu"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by shavenlunatic on 2007-07-13
Hi, was trying to edit some launchers in the Xubuntu Applications menu... if I choose "Applications > Settings > Menu Editor" all I get is the system menu...

Found a thread that said "ooh, edit the xml file" or such like..

```
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
	</menu>
	<separator/>
	<include type="system" style="simple" unique="true" legacy="true"/>
	<separator/>
	<app name="About Xfce" cmd="xfce4-about"/>
	<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>

```

this is a clean install of xubuntu... any ideas?




edit: it seems "/usr/share/applications" may have something to do with it.. no idea how it sets up the menu just with a lite of files but hey.. i'll have a play (any further suggestions/help still VERY welcome!)

---

### Post by crimesaucer on 2007-07-13
Are the launchers that you want to edit located in the --include-- --system-- part of the menu editor when you right click the Xfce Menu button?

Or are they viewable in that "separated" area below the Settings Manager?



Anyway, I think you might want to look at this thread about editing those areas of --include-- --system-- that aren't changeable in the Xfce Menu Editor: [http://ubuntuforums.org/showthread.php?t=421973&highlight=menu+edit+include+system](http://ubuntuforums.org/showthread.php?t=421973&highlight=menu+edit+include+system)

---

