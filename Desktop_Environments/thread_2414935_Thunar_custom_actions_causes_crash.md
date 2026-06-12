---
title: "Thunar custom actions causes crash"
date: 2019-03-17
forum: Desktop Environments
---

### Post by rattskjelke on 2019-03-17
I had been using Xubuntu 18.10 for several months with no problems and had several Thunar custom actions that worked with no problems. A few weeks ago I switched to another distro and yesterday I got tired of it so I wiped the hard drive and did a clean install of Xubuntu 18.10.

Something changed in the past few weeks and now my custom actions make thunar crash, not start from the menu or keyboard, and there is no desktop right-click menu.

I thought maybe my ~/.config/Thunar/uca.xml file got corrupted so I replaced it with a backup copy. That did not fix the problem. I delete accels.scm and uca.xml and started over. The default custom actions and desktop right-click menu work but if I create any new custom actions it breaks Thunar. I reinstalled Thunar and that did not help. This does not make sense. I think something else is breaking Thunar but I don't know which log to check for thunar errors or crashes or how to troubleshoot this.

---

### Post by ajgreeny on 2019-03-17
Try starting thunar from terminal with command **thunar** then use a custom action and look for any clues in the terminal output

Just out of interest have a look at the output of ```
ls -l .config/Thunar.uca.xml
``` which in my case shows
```
-rw------- 1 user user 6.9K Sat Mar 09 2019 22:24 /home/user/.config/Thunar/uca.xml
```
I see no reason why there should be any problem with this but I'm "grasping at straws" to try to get some sort of answer for you.

---

### Post by rattskjelke on 2019-03-17
Here is the default uca.xml file:
```

<?xml encoding="UTF-8" version="1.0"?>
<actions>
<action>
	<icon>Terminal</icon>
	<name>Open Terminal Here</name>
	<unique-id>1552855857388716-1</unique-id>
	<command>exo-open --working-directory %f --launch TerminalEmulator</command>
	<description>Example for a custom action</description>
	<patterns>*</patterns>
	<directories/>
</action>
<action>
	<icon>Terminal</icon>
	<name>Open Terminal Here</name>
	<unique-id>1552855857388768-2</unique-id>
	<command>exo-open --working-directory %d --launch TerminalEmulator</command>
	<description>Open terminal in containing directory</description>
	<patterns>*</patterns>
	<audio-files/>
	<image-files/>
	<other-files/>
	<text-files/>
	<video-files/>
</action>
<action>
	<icon>filefind</icon>
	<name>Find in this folder</name>
	<unique-id>1552855857388859-3</unique-id>
	<command>catfish --path=%f</command>
	<description>Search for files within this folder</description>
	<patterns>*</patterns>
	<directories/>
</action>
<action>
	<icon>document-print</icon>
	<name>Print file/s</name>
	<unique-id>1552855857388878-4</unique-id>
	<command>thunar-print %F</command>
	<description>Send one or multiple files to the default printer</description>
	<patterns>*.asc;*.brf;*.css;*.doc;*.docm;*.docx;*.dotm;*.dotx;*.fodg;*.fodp;*.fods;*.fodt;*.gif;*.htm;*.html;*.jpe;*.jpeg;*.jpg;*.odb;*.odf;*.odg;*.odm;*.odp;*.ods;*.odt;*.otg;*.oth;*.otp;*.ots;*.ott;*.pbm;*.pdf;*.pgm;*.png;*.pnm;*.pot;*.potm;*.potx;*.ppm;*.ppt;*.pptm;*.pptx;*.rtf;*.shtml;*.srt;*.text;*.tif;*.tiff;*.txt;*.xbm;*.xls;*.xlsb;*.xlsm;*.xlsx;*.xltm;*.xltx;*.xpm;*.xwd</patterns>
	<image-files/>
	<other-files/>
	<text-files/>
</action>
</actions>

```
Here is one that breaks Thunar:
```

<?xml encoding="UTF-8" version="1.0"?>
<actions>
<action>
	<icon>firefox</icon>
	<name>Firefox</name>
	<unique-id>1552861590850571-1</unique-id>
	<command>firefox</command>
	<description>Firefox</description>
	<patterns>*</patterns>
	<startup-notify/>
	<directories/>
</action>
<action>
	<icon>thunderbird</icon>
	<name>Thunderbird</name>
	<unique-id>1552861621767243-2</unique-id>
	<command>thunderbird</command>
	<description>Thunderbird</description>
	<patterns>*</patterns>
	<startup-notify/>
	<directories/>
</action>
<action>
	<icon>accessories-text-editor</icon>
	<name>Mousepad</name>
	<unique-id>1552861663127821-3</unique-id>
	<command>mousepad</command>
	<description>Mousepad</description>
	<patterns>*</patterns>
	<directories/>
</action>
<action>
	<icon></icon>
	<name>Edit as Root</name>
	<unique-id>1552861727038831-5</unique-id>
	<command>pkexec mousepad %f</command>
	<description>Edit as Root</description>
	<patterns>*</patterns>
	<text-files/>
</action>
<action>
	<icon></icon>
	<name>Open Root Thunar Here</name>
	<unique-id>1552861692502761-4</unique-id>
	<command>pkexec thunar</command>
	<description>Open Root Thunar Here</description>
	<patterns>*</patterns>
	<directories/>
</action>
<action>
	<icon>Terminal</icon>
	<name>Open Terminal Here</name>
	<unique-id>1552855857388716-1</unique-id>
	<command>exo-open --working-directory %f --launch TerminalEmulator</command>
	<description>Open Terminal Here</description>
	<patterns>*</patterns>
	<directories/>
</action>
<action>
	<icon>filefind</icon>
	<name>Find in this folder</name>
	<unique-id>1552855857388859-3</unique-id>
	<command>catfish --path=%f</command>
	<description>Search for files within this folder</description>
	<patterns>*</patterns>
	<directories/>
</action>
<action>
	<icon>document-print</icon>
	<name>Print file/s</name>
	<unique-id>1552855857388878-4</unique-id>
	<command>thunar-print %F</command>
	<description>Send one or multiple files to the default printer</description>
	<patterns>*.asc;*.brf;*.css;*.doc;*.docm;*.docx;*.dotm;*.dotx;*.fodg;*.fodp;*.fods;*.fodt;*.gif;*.htm;*.html;*.jpe;*.jpeg;*.jpg;*.odb;*.odf;*.odg;*.odm;*.odp;*.ods;*.odt;*.otg;*.oth;*.otp;*.ots;*.ott;*.pbm;*.pdf;*.pgm;*.png;*.pnm;*.pot;*.potm;*.potx;*.ppm;*.ppt;*.pptm;*.pptx;*.rtf;*.shtml;*.srt;*.text;*.tif;*.tiff;*.txt;*.xbm;*.xls;*.xlsb;*.xlsm;*.xlsx;*.xltm;*.xltx;*.xpm;*.xwd</patterns>
	<image-files/>
	<other-files/>
	<text-files/>
</action>
</actions>

```

After I made the second file Thunar won't run. If I try to run it from a terminal window I get:
[I]$ thunar
Segmentation fault (core dumped)[/I]

If I go back and delete the ~/.config/Thunar folder then run thunar again it recreates the folder with the default files and everything works again, but without my custom actions.

---

### Post by again? on 2019-03-17
I dropped your uac.xml file into my thunar config and works without error.
When I do this, permissions differ from my original(.bak) file.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls -l .config/Thunar/**
total 16
-rw-r--r-- 1 glen glen 6158 Mar 18 07:50 accels.scm
-rw-rw-r-- 1 glen glen 2439 Mar 18 07:43 uca.xml
-rw------- 1 glen glen 1564 Mar  6 07:51 uca.xml.bak
```

But changing permissions to match original uac.xml makes no difference.
Still runs without error.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls -l .config/Thunar/**
total 16
-rw-r--r-- 1 glen glen 6158 Mar 18 07:50 accels.scm
-rw------- 1 glen glen 2439 Mar 18 07:43 uca.xml
-rw------- 1 glen glen 1564 Mar  6 07:51 uca.xml.bak
```

Xubuntu 18.04
Thunar 1.6.15

---

### Post by rattskjelke on 2019-03-17
I think I figured out what happened. After I did the clean install of Xubuntu I removed Ristretto and Parole and replaced them with Nomacs and VLC. I think that somehow breaks Thunar. I purged nomacs*, vlc* and xubuntu-desktop then reinstalled xubuntu-desktop to get everything the way it originally was. Now Thunar and my custom actions work again.


I just reinstalled VLC and everything still works. It must have been nomacs.

---

### Post by again? on 2019-03-17
I see you have solved it but here's some info I gathered after testing in 18.10.
Your uac.xml produced the segmentation fault.

The section that was producing the fault was...
```
<action>
	[COLOR="#FF0000"]<icon></icon>[/COLOR]
	<name>Open Root Thunar Here</name>
	<unique-id>1552861692502761-4</unique-id>
	<command>pkexec thunar</command>
	<description>Open Root Thunar Here</description>
	<patterns>*</patterns>
	<directories/>
</action>
```

If I added an icon thunar would start without error...
```
[COLOR="#FF0000"]<icon>locked</icon>[/COLOR]
```

Strange as it doesn't affect the mousepad as root section which also doesn't have an icon set.

---

### Post by rattskjelke on 2019-03-18
> **rattskjelke said:**
> I just reinstalled VLC and everything still works. It must have been nomacs.
I was wrong about that. Now I don't think Nomacs or VLC had anything to do with it.
Thunar, or something else, in 18.10 has bugs that don't like custom actions without an icon. This doesn't happen on a 18.04.2 live USB.

---

### Post by rattskjelke on 2019-05-12
> **rattskjelke said:**
> This doesn't happen on a 18.04.2 live USB.
I installed 19.04 the other day and have not had the problem so far.

---

