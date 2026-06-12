---
title: "want to delete .private folder"
date: 2012-11-20
forum: Desktop Environments
---

### Post by madeel12 on 2012-11-20
I have 36 GB parition for Ubuntu whereas the folder .private has eaten up over 25 GB. I want to delete its contents. I would like to know whether it can cause any harm or not. 

Thanks in advance

---

### Post by Bucky Ball on 2012-11-20
Where is this .private folder?

---

### Post by madeel12 on 2012-11-20
It is hidden folder located in my home folder which become visible by pressing Ctrl+H. I think it is holding some encrypted data as I had chosen my home folder to be encrypted at the time installation. The system was suppose to be multi login so I thought administrator account should be encrypted. 

I didn't encrypt any of my files in my home folder. It is something which is system is doing on its own. That is why I think I should be safe to delete the files in this folder. However, I want to confirm it before doing so.

---

### Post by Cheesemill on 2012-11-20
Don't delete it. This file contains the encrypted contents of your home folder.

Deleting this file would have the same effect as deleting everything in your home folder.

---

### Post by madeel12 on 2012-11-20
> **Cheesemill said:**
> Don't delete it. This file contains the encrypted contents of your home folder.

Deleting this file would have the same effect as deleting everything in your home folder.
But how can then I free the space available. It seems that this folder will continue to grow its size. My own data is less than 10 GB. There should be then some solution to circumvent this problem.

---

### Post by varunendra on 2012-11-21
> **madeel12 said:**
> But how can then I free the space available. It seems that this folder will continue to grow its size. My own data is less than 10 GB. There should be then some solution to circumvent this problem.I have never tried encryption myself, so can't explain the folder size, but one easy way to ensure safety of your data is to just copy all your user data in home to another (non-encrypted) partition while being logged in as the user which you have encrypted.

Once done, you may proceed to either removing encryption or doing whatever you want with that folder. Should anything go wrong, at least your data would be safe.


[COLOR=DarkRed]**EDIT :**[/COLOR]
This may be an interesting read for you : [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup)

---

### Post by Cheesemill on 2012-11-21
Can you open a terminal and post the output of:
```
cd && du -h
```

---

### Post by madeel12 on 2012-11-21
> **Cheesemill said:**
> Can you open a terminal and post the output of:
```
cd && du -h
```

There output is a huge list.  The last line was like this:

23G    . 

The list has vitually all the main folder starting with . /. 

I think the last line was representing the total size of private folder. Perhaps it is keeping a back log in that folder?

---

### Post by Cheesemill on 2012-11-21
Can you post the full output of that last command please.

---

### Post by madeel12 on 2012-11-26
> **Cheesemill said:**
> Can you post the full output of that last command please.

<pre> 

```
311M    ./Music
16K    ./.gconf/desktop/gnome/shell/windows
28K    ./.gconf/desktop/gnome/shell
16K    ./.gconf/desktop/gnome/background
16K    ./.gconf/desktop/gnome/url-handlers/mailto
28K    ./.gconf/desktop/gnome/url-handlers
84K    ./.gconf/desktop/gnome
96K    ./.gconf/desktop
16K    ./.gconf/apps/compiz-1/plugins/gnomecompat/screen0/options
28K    ./.gconf/apps/compiz-1/plugins/gnomecompat/screen0
40K    ./.gconf/apps/compiz-1/plugins/gnomecompat
16K    ./.gconf/apps/compiz-1/plugins/unityshell/screen0/options
28K    ./.gconf/apps/compiz-1/plugins/unityshell/screen0
40K    ./.gconf/apps/compiz-1/plugins/unityshell
92K    ./.gconf/apps/compiz-1/plugins
16K    ./.gconf/apps/compiz-1/general/screen0/options
28K    ./.gconf/apps/compiz-1/general/screen0
40K    ./.gconf/apps/compiz-1/general
144K    ./.gconf/apps/compiz-1
16K    ./.gconf/apps/deja-dup/s3
32K    ./.gconf/apps/deja-dup
16K    ./.gconf/apps/update-manager
16K    ./.gconf/apps/totem
16K    ./.gconf/apps/gnucash/dialogs/open_save
16K    ./.gconf/apps/gnucash/dialogs/tip_of_the_day
16K    ./.gconf/apps/gnucash/dialogs/new_user
16K    ./.gconf/apps/gnucash/dialogs/account
16K    ./.gconf/apps/gnucash/dialogs/preferences
92K    ./.gconf/apps/gnucash/dialogs
16K    ./.gconf/apps/gnucash/window/pages/account_tree
16K    ./.gconf/apps/gnucash/window/pages/register
44K    ./.gconf/apps/gnucash/window/pages
56K    ./.gconf/apps/gnucash/window
16K    ./.gconf/apps/gnucash/history
16K    ./.gconf/apps/gnucash/general
192K    ./.gconf/apps/gnucash
16K    ./.gconf/apps/gedit-2/plugins
16K    ./.gconf/apps/gedit-2/preferences/ui/statusbar
28K    ./.gconf/apps/gedit-2/preferences/ui
40K    ./.gconf/apps/gedit-2/preferences
68K    ./.gconf/apps/gedit-2
16K    ./.gconf/apps/update-notifier
16K    ./.gconf/apps/eog/ui
16K    ./.gconf/apps/eog/view
44K    ./.gconf/apps/eog
16K    ./.gconf/apps/nm-applet
16K    ./.gconf/apps/compizconfig-1
16K    ./.gconf/apps/file-roller/dialogs/batch-add
16K    ./.gconf/apps/file-roller/dialogs/extract
44K    ./.gconf/apps/file-roller/dialogs
16K    ./.gconf/apps/file-roller/ui
16K    ./.gconf/apps/file-roller/listing
16K    ./.gconf/apps/file-roller/general
104K    ./.gconf/apps/file-roller
16K    ./.gconf/apps/gnome-terminal/profiles/Default
28K    ./.gconf/apps/gnome-terminal/profiles
40K    ./.gconf/apps/gnome-terminal
16K    ./.gconf/apps/metacity/window_keybindings
16K    ./.gconf/apps/metacity/global_keybindings
16K    ./.gconf/apps/metacity/general
60K    ./.gconf/apps/metacity
16K    ./.gconf/apps/nautilus/preferences
28K    ./.gconf/apps/nautilus
804K    ./.gconf/apps
904K    ./.gconf
4.0K    ./.mozilla/extensions
6.3M    ./.mozilla/firefox/Crash Reports/pending
6.5M    ./.mozilla/firefox/Crash Reports
420K    ./.mozilla/firefox/nf0t40de.default/extensions
268K    ./.mozilla/firefox/nf0t40de.default/OfflineCache
4.0K    ./.mozilla/firefox/nf0t40de.default/mozilla-media-cache
4.3M    ./.mozilla/firefox/nf0t40de.default/thumbnails
1.3M    ./.mozilla/firefox/nf0t40de.default/startupCache
16K    ./.mozilla/firefox/nf0t40de.default/useragentswitcher
4.0K    ./.mozilla/firefox/nf0t40de.default/weave/failed
4.0K    ./.mozilla/firefox/nf0t40de.default/weave/changes
4.0K    ./.mozilla/firefox/nf0t40de.default/weave/toFetch
16K    ./.mozilla/firefox/nf0t40de.default/weave
11M    ./.mozilla/firefox/nf0t40de.default/minidumps
2.4M    ./.mozilla/firefox/nf0t40de.default/safebrowsing
244K    ./.mozilla/firefox/nf0t40de.default/bookmarkbackups
4.0K    ./.mozilla/firefox/nf0t40de.default/webapps
32K    ./.mozilla/firefox/nf0t40de.default/Cache/5/C1
84K    ./.mozilla/firefox/nf0t40de.default/Cache/5/81
32K    ./.mozilla/firefox/nf0t40de.default/Cache/5/99
44K    ./.mozilla/firefox/nf0t40de.default/Cache/5/9D
48K    ./.mozilla/firefox/nf0t40de.default/Cache/5/4E
124K    ./.mozilla/firefox/nf0t40de.default/Cache/5/FD
40K    ./.mozilla/firefox/nf0t40de.default/Cache/5/DC
196K    ./.mozilla/firefox/nf0t40de.default/Cache/5/BE
32K    ./.mozilla/firefox/nf0t40de.default/Cache/5/EF
80K    ./.mozilla/firefox/nf0t40de.default/Cache/5/F1
32K    ./.mozilla/firefox/nf0t40de.default/Cache/5/DD
32K    ./.mozilla/firefox/nf0t40de.default/Cache/5/26
44K    ./.mozilla/firefox/nf0t40de.default/Cache/5/62
824K    ./.mozilla/firefox/nf0t40de.default/Cache/5
52K    ./.mozilla/firefox/nf0t40de.default/Cache/D/34
40K    ./.mozilla/firefox/nf0t40de.default/Cache/D/12
44K    ./.mozilla/firefox/nf0t40de.default/Cache/D/CD
164K    ./.mozilla/firefox/nf0t40de.default/Cache/D/AE
32K    ./.mozilla/firefox/nf0t40de.default/Cache/D/BA
60K    ./.mozilla/firefox/nf0t40de.default/Cache/D/2A
36K    ./.mozilla/firefox/nf0t40de.default/Cache/D/0E
72K    ./.mozilla/firefox/nf0t40de.default/Cache/D/4A
40K    ./.mozilla/firefox/nf0t40de.default/Cache/D/AC
40K    ./.mozilla/firefox/nf0t40de.default/Cache/D/45
40K    ./.mozilla/firefox/nf0t40de.default/Cache/D/68
32K    ./.mozilla/firefox/nf0t40de.default/Cache/D/B4
40K    ./.mozilla/firefox/nf0t40de.default/Cache/D/6D
696K    ./.mozilla/firefox/nf0t40de.default/Cache/D
184K    ./.mozilla/firefox/nf0t40de.default/Cache/F/F9
4.0K    ./.mozilla/firefox/nf0t40de.default/Cache/F/C1
40K    ./.mozilla/firefox/nf0t40de.default/Cache/F/D7
32K    ./.mozilla/firefox/nf0t40de.default/Cache/F/83
32K    ./.mozilla/firefox/nf0t40de.default/Cache/F/09
32K    ./.mozilla/firefox/nf0t40de.default/Cache/F/D1
36K    ./.mozilla/firefox/nf0t40de.default/Cache/F/5D
56K    ./.mozilla/firefox/nf0t40de.default/Cache/F/75
48K    ./.mozilla/firefox/nf0t40de.default/Cache/F/03
468K    ./.mozilla/firefox/nf0t40de.default/Cache/F
40K    ./.mozilla/firefox/nf0t40de.default/Cache/6/94
36K    ./.mozilla/firefox/nf0t40de.default/Cache/6/3B
56K    ./.mozilla/firefox/nf0t40de.default/Cache/6/6E
48K    ./.mozilla/firefox/nf0t40de.default/Cache/6/28
68K    ./.mozilla/firefox/nf0t40de.default/Cache/6/C2
32K    ./.mozilla/firefox/nf0t40de.default/Cache/6/21
72K    ./.mozilla/firefox/nf0t40de.default/Cache/6/18
32K    ./.mozilla/firefox/nf0t40de.default/Cache/6/4C
96K    ./.mozilla/firefox/nf0t40de.default/Cache/6/33
32K    ./.mozilla/firefox/nf0t40de.default/Cache/6/D5
516K    ./.mozilla/firefox/nf0t40de.default/Cache/6
4.0K    ./.mozilla/firefox/nf0t40de.default/Cache/7/C9
72K    ./.mozilla/firefox/nf0t40de.default/Cache/7/F3
68K    ./.mozilla/firefox/nf0t40de.default/Cache/7/B8
52K    ./.mozilla/firefox/nf0t40de.default/Cache/7/19
68K    ./.mozilla/firefox/nf0t40de.default/Cache/7/48
36K    ./.mozilla/firefox/nf0t40de.default/Cache/7/D6
36K    ./.mozilla/firefox/nf0t40de.default/Cache/7/E3
32K    ./.mozilla/firefox/nf0t40de.default/Cache/7/0C
52K    ./.mozilla/firefox/nf0t40de.default/Cache/7/2D
92K    ./.mozilla/firefox/nf0t40de.default/Cache/7/1D
44K    ./.mozilla/firefox/nf0t40de.default/Cache/7/F8
32K    ./.mozilla/firefox/nf0t40de.default/Cache/7/E1
32K    ./.mozilla/firefox/nf0t40de.default/Cache/7/B4
36K    ./.mozilla/firefox/nf0t40de.default/Cache/7/5F
68K    ./.mozilla/firefox/nf0t40de.default/Cache/7/2E
52K    ./.mozilla/firefox/nf0t40de.default/Cache/7/B3
780K    ./.mozilla/firefox/nf0t40de.default/Cache/7
152K    ./.mozilla/firefox/nf0t40de.default/Cache/C/34
44K    ./.mozilla/firefox/nf0t40de.default/Cache/C/88
40K    ./.mozilla/firefox/nf0t40de.default/Cache/C/3F
68K    ./.mozilla/firefox/nf0t40de.default/Cache/C/AB
68K    ./.mozilla/firefox/nf0t40de.default/Cache/C/E6
32K    ./.mozilla/firefox/nf0t40de.default/Cache/C/1E
224K    ./.mozilla/firefox/nf0t40de.default/Cache/C/8E
152K    ./.mozilla/firefox/nf0t40de.default/Cache/C/20
32K    ./.mozilla/firefox/nf0t40de.default/Cache/C/0C
72K    ./.mozilla/firefox/nf0t40de.default/Cache/C/EE
44K    ./.mozilla/firefox/nf0t40de.default/Cache/C/2D
124K    ./.mozilla/firefox/nf0t40de.default/Cache/C/41
48K    ./.mozilla/firefox/nf0t40de.default/Cache/C/02
32K    ./.mozilla/firefox/nf0t40de.default/Cache/C/92
1.2M    ./.mozilla/firefox/nf0t40de.default/Cache/C
56K    ./.mozilla/firefox/nf0t40de.default/Cache/1/54
48K    ./.mozilla/firefox/nf0t40de.default/Cache/1/81
376K    ./.mozilla/firefox/nf0t40de.default/Cache/1/99
36K    ./.mozilla/firefox/nf0t40de.default/Cache/1/21
32K    ./.mozilla/firefox/nf0t40de.default/Cache/1/EE
172K    ./.mozilla/firefox/nf0t40de.default/Cache/1/1B
36K    ./.mozilla/firefox/nf0t40de.default/Cache/1/1D
84K    ./.mozilla/firefox/nf0t40de.default/Cache/1/5C
44K    ./.mozilla/firefox/nf0t40de.default/Cache/1/B5
888K    ./.mozilla/firefox/nf0t40de.default/Cache/1
32K    ./.mozilla/firefox/nf0t40de.default/Cache/0/15
164K    ./.mozilla/firefox/nf0t40de.default/Cache/0/52
40K    ./.mozilla/firefox/nf0t40de.default/Cache/0/BB
44K    ./.mozilla/firefox/nf0t40de.default/Cache/0/77
68K    ./.mozilla/firefox/nf0t40de.default/Cache/0/60
44K    ./.mozilla/firefox/nf0t40de.default/Cache/0/DD
44K    ./.mozilla/firefox/nf0t40de.default/Cache/0/A5
68K    ./.mozilla/firefox/nf0t40de.default/Cache/0/5B
88K    ./.mozilla/firefox/nf0t40de.default/Cache/0/92
32K    ./.mozilla/firefox/nf0t40de.default/Cache/0/4F
252K    ./.mozilla/firefox/nf0t40de.default/Cache/0/2E
40K    ./.mozilla/firefox/nf0t40de.default/Cache/0/B5
920K    ./.mozilla/firefox/nf0t40de.default/Cache/0
100K    ./.mozilla/firefox/nf0t40de.default/Cache/B/DA
40K    ./.mozilla/firefox/nf0t40de.default/Cache/B/AE
40K    ./.mozilla/firefox/nf0t40de.default/Cache/B/BA
52K    ./.mozilla/firefox/nf0t40de.default/Cache/B/B9
40K    ./.mozilla/firefox/nf0t40de.default/Cache/B/37
40K    ./.mozilla/firefox/nf0t40de.default/Cache/B/18
36K    ./.mozilla/firefox/nf0t40de.default/Cache/B/6C
44K    ./.mozilla/firefox/nf0t40de.default/Cache/B/7B
60K    ./.mozilla/firefox/nf0t40de.default/Cache/B/E7
32K    ./.mozilla/firefox/nf0t40de.default/Cache/B/58
32K    ./.mozilla/firefox/nf0t40de.default/Cache/B/E9
92K    ./.mozilla/firefox/nf0t40de.default/Cache/B/72
116K    ./.mozilla/firefox/nf0t40de.default/Cache/B/F4
32K    ./.mozilla/firefox/nf0t40de.default/Cache/B/85
52K    ./.mozilla/firefox/nf0t40de.default/Cache/B/26
56K    ./.mozilla/firefox/nf0t40de.default/Cache/B/B4
84K    ./.mozilla/firefox/nf0t40de.default/Cache/B/32
32K    ./.mozilla/firefox/nf0t40de.default/Cache/B/75
72K    ./.mozilla/firefox/nf0t40de.default/Cache/B/7D
1.1M    ./.mozilla/firefox/nf0t40de.default/Cache/B
44K    ./.mozilla/firefox/nf0t40de.default/Cache/3/47
52K    ./.mozilla/firefox/nf0t40de.default/Cache/3/FA
32K    ./.mozilla/firefox/nf0t40de.default/Cache/3/57
44K    ./.mozilla/firefox/nf0t40de.default/Cache/3/BB
112K    ./.mozilla/firefox/nf0t40de.default/Cache/3/79
32K    ./.mozilla/firefox/nf0t40de.default/Cache/3/DC
80K    ./.mozilla/firefox/nf0t40de.default/Cache/3/17
60K    ./.mozilla/firefox/nf0t40de.default/Cache/3/C5
88K    ./.mozilla/firefox/nf0t40de.default/Cache/3/60
32K    ./.mozilla/firefox/nf0t40de.default/Cache/3/0F
44K    ./.mozilla/firefox/nf0t40de.default/Cache/3/16
52K    ./.mozilla/firefox/nf0t40de.default/Cache/3/02
32K    ./.mozilla/firefox/nf0t40de.default/Cache/3/97
32K    ./.mozilla/firefox/nf0t40de.default/Cache/3/1C
88K    ./.mozilla/firefox/nf0t40de.default/Cache/3/11
828K    ./.mozilla/firefox/nf0t40de.default/Cache/3
32K    ./.mozilla/firefox/nf0t40de.default/Cache/A/19
48K    ./.mozilla/firefox/nf0t40de.default/Cache/A/46
408K    ./.mozilla/firefox/nf0t40de.default/Cache/A/9F
32K    ./.mozilla/firefox/nf0t40de.default/Cache/A/C8
36K    ./.mozilla/firefox/nf0t40de.default/Cache/A/B2
40K    ./.mozilla/firefox/nf0t40de.default/Cache/A/09
60K    ./.mozilla/firefox/nf0t40de.default/Cache/A/E7
36K    ./.mozilla/firefox/nf0t40de.default/Cache/A/0D
56K    ./.mozilla/firefox/nf0t40de.default/Cache/A/80
52K    ./.mozilla/firefox/nf0t40de.default/Cache/A/2C
32K    ./.mozilla/firefox/nf0t40de.default/Cache/A/DB
84K    ./.mozilla/firefox/nf0t40de.default/Cache/A/E8
36K    ./.mozilla/firefox/nf0t40de.default/Cache/A/98
52K    ./.mozilla/firefox/nf0t40de.default/Cache/A/05
40K    ./.mozilla/firefox/nf0t40de.default/Cache/A/42
40K    ./.mozilla/firefox/nf0t40de.default/Cache/A/7D
1.1M    ./.mozilla/firefox/nf0t40de.default/Cache/A
32K    ./.mozilla/firefox/nf0t40de.default/Cache/E/43
36K    ./.mozilla/firefox/nf0t40de.default/Cache/E/12
56K    ./.mozilla/firefox/nf0t40de.default/Cache/E/53
32K    ./.mozilla/firefox/nf0t40de.default/Cache/E/D7
32K    ./.mozilla/firefox/nf0t40de.default/Cache/E/CB
68K    ./.mozilla/firefox/nf0t40de.default/Cache/E/BA
132K    ./.mozilla/firefox/nf0t40de.default/Cache/E/2A
32K    ./.mozilla/firefox/nf0t40de.default/Cache/E/E3
140K    ./.mozilla/firefox/nf0t40de.default/Cache/E/AC
44K    ./.mozilla/firefox/nf0t40de.default/Cache/E/6C
532K    ./.mozilla/firefox/nf0t40de.default/Cache/E/77
32K    ./.mozilla/firefox/nf0t40de.default/Cache/E/DF
188K    ./.mozilla/firefox/nf0t40de.default/Cache/E/90
48K    ./.mozilla/firefox/nf0t40de.default/Cache/E/A6
84K    ./.mozilla/firefox/nf0t40de.default/Cache/E/44
72K    ./.mozilla/firefox/nf0t40de.default/Cache/E/EB
32K    ./.mozilla/firefox/nf0t40de.default/Cache/E/51
1.6M    ./.mozilla/firefox/nf0t40de.default/Cache/E
36K    ./.mozilla/firefox/nf0t40de.default/Cache/2/3B
40K    ./.mozilla/firefox/nf0t40de.default/Cache/2/54
88K    ./.mozilla/firefox/nf0t40de.default/Cache/2/99
420K    ./.mozilla/firefox/nf0t40de.default/Cache/2/82
116K    ./.mozilla/firefox/nf0t40de.default/Cache/2/10
56K    ./.mozilla/firefox/nf0t40de.default/Cache/2/7E
32K    ./.mozilla/firefox/nf0t40de.default/Cache/2/B2
32K    ./.mozilla/firefox/nf0t40de.default/Cache/2/68
52K    ./.mozilla/firefox/nf0t40de.default/Cache/2/E8
36K    ./.mozilla/firefox/nf0t40de.default/Cache/2/EB
912K    ./.mozilla/firefox/nf0t40de.default/Cache/2
176K    ./.mozilla/firefox/nf0t40de.default/Cache/4/F9
52K    ./.mozilla/firefox/nf0t40de.default/Cache/4/3A
36K    ./.mozilla/firefox/nf0t40de.default/Cache/4/7F
40K    ./.mozilla/firefox/nf0t40de.default/Cache/4/B9
88K    ./.mozilla/firefox/nf0t40de.default/Cache/4/27
48K    ./.mozilla/firefox/nf0t40de.default/Cache/4/F6
164K    ./.mozilla/firefox/nf0t40de.default/Cache/4/0C
88K    ./.mozilla/firefox/nf0t40de.default/Cache/4/01
44K    ./.mozilla/firefox/nf0t40de.default/Cache/4/6C
48K    ./.mozilla/firefox/nf0t40de.default/Cache/4/C6
40K    ./.mozilla/firefox/nf0t40de.default/Cache/4/0D
40K    ./.mozilla/firefox/nf0t40de.default/Cache/4/1F
32K    ./.mozilla/firefox/nf0t40de.default/Cache/4/41
40K    ./.mozilla/firefox/nf0t40de.default/Cache/4/1D
44K    ./.mozilla/firefox/nf0t40de.default/Cache/4/02
32K    ./.mozilla/firefox/nf0t40de.default/Cache/4/1C
48K    ./.mozilla/firefox/nf0t40de.default/Cache/4/B3
84K    ./.mozilla/firefox/nf0t40de.default/Cache/4/31
72K    ./.mozilla/firefox/nf0t40de.default/Cache/4/3C
1.2M    ./.mozilla/firefox/nf0t40de.default/Cache/4
36K    ./.mozilla/firefox/nf0t40de.default/Cache/9/F2
44K    ./.mozilla/firefox/nf0t40de.default/Cache/9/2B
76K    ./.mozilla/firefox/nf0t40de.default/Cache/9/1A
80K    ./.mozilla/firefox/nf0t40de.default/Cache/9/CD
104K    ./.mozilla/firefox/nf0t40de.default/Cache/9/65
52K    ./.mozilla/firefox/nf0t40de.default/Cache/9/4B
32K    ./.mozilla/firefox/nf0t40de.default/Cache/9/84
60K    ./.mozilla/firefox/nf0t40de.default/Cache/9/E6
92K    ./.mozilla/firefox/nf0t40de.default/Cache/9/8E
56K    ./.mozilla/firefox/nf0t40de.default/Cache/9/09
76K    ./.mozilla/firefox/nf0t40de.default/Cache/9/F0
40K    ./.mozilla/firefox/nf0t40de.default/Cache/9/F4
32K    ./.mozilla/firefox/nf0t40de.default/Cache/9/36
40K    ./.mozilla/firefox/nf0t40de.default/Cache/9/4F
32K    ./.mozilla/firefox/nf0t40de.default/Cache/9/B3
168K    ./.mozilla/firefox/nf0t40de.default/Cache/9/B5
32K    ./.mozilla/firefox/nf0t40de.default/Cache/9/98
52K    ./.mozilla/firefox/nf0t40de.default/Cache/9/05
1.1M    ./.mozilla/firefox/nf0t40de.default/Cache/9
32K    ./.mozilla/firefox/nf0t40de.default/Cache/8/29
48K    ./.mozilla/firefox/nf0t40de.default/Cache/8/57
124K    ./.mozilla/firefox/nf0t40de.default/Cache/8/99
156K    ./.mozilla/firefox/nf0t40de.default/Cache/8/EA
84K    ./.mozilla/firefox/nf0t40de.default/Cache/8/70
36K    ./.mozilla/firefox/nf0t40de.default/Cache/8/7E
140K    ./.mozilla/firefox/nf0t40de.default/Cache/8/AC
132K    ./.mozilla/firefox/nf0t40de.default/Cache/8/63
48K    ./.mozilla/firefox/nf0t40de.default/Cache/8/F1
52K    ./.mozilla/firefox/nf0t40de.default/Cache/8/00
56K    ./.mozilla/firefox/nf0t40de.default/Cache/8/36
132K    ./.mozilla/firefox/nf0t40de.default/Cache/8/DD
32K    ./.mozilla/firefox/nf0t40de.default/Cache/8/78
44K    ./.mozilla/firefox/nf0t40de.default/Cache/8/2E
32K    ./.mozilla/firefox/nf0t40de.default/Cache/8/30
36K    ./.mozilla/firefox/nf0t40de.default/Cache/8/EB
60K    ./.mozilla/firefox/nf0t40de.default/Cache/8/05
32K    ./.mozilla/firefox/nf0t40de.default/Cache/8/7D
1.3M    ./.mozilla/firefox/nf0t40de.default/Cache/8
23M    ./.mozilla/firefox/nf0t40de.default/Cache
132M    ./.mozilla/firefox/nf0t40de.default
138M    ./.mozilla/firefox
138M    ./.mozilla
62M    ./Pictures/temp2
7.8M    ./Pictures/slect-piks/tie3
20M    ./Pictures/slect-piks/tie4
4.7M    ./Pictures/slect-piks/tie5
5.1M    ./Pictures/slect-piks/tie2
6.2M    ./Pictures/slect-piks/tie1
333M    ./Pictures/slect-piks
46M    ./Pictures/Pics/canon80IX-brochurenew
100M    ./Pictures/Pics/metal pics
569M    ./Pictures/Pics
964M    ./Pictures
772K    ./.cache/wallpaper
4.0K    ./.cache/indicator/sound/album-art-cache
8.0K    ./.cache/indicator/sound
12K    ./.cache/indicator
4.0K    ./.cache/gnome-screenshot
16K    ./.cache/unity
8.4M    ./.cache/chromium/Default/Cache
8.4M    ./.cache/chromium/Default
8.4M    ./.cache/chromium
16K    ./.cache/indicators/messages
20K    ./.cache/indicators
16K    ./.cache/update-manager-core
4.0K    ./.cache/folks/avatars
8.0K    ./.cache/folks
4.0K    ./.cache/gvfs-burn
7.7M    ./.cache/software-center/icons
2.5M    ./.cache/software-center/piston-helper
240K    ./.cache/software-center/rnrclient
4.1M    ./.cache/software-center/software-center-agent.db
1.1M    ./.cache/software-center/reviews.ubuntu.com_reviews_api_1.0_review-stats-pkgnames.p__5.1.db.dbenv
3.2M    ./.cache/software-center/download-cache
21M    ./.cache/software-center
16K    ./.cache/indicator-appmenu
16K    ./.cache/dconf
268K    ./.cache/sso
332K    ./.cache/compizconfig-1
52K    ./.cache/transmission/favicons
56K    ./.cache/transmission
108K    ./.cache/oneconf/529fc1cf144e37d4ce69c38400000011
112K    ./.cache/oneconf
16K    ./.cache/unity-lens-video
4.0K    ./.cache/ubuntuone/partials
372K    ./.cache/ubuntuone/log
380K    ./.cache/ubuntuone
31M    ./.cache
648K    ./PDF
4.0K    ./.scribus/swatches/locked
8.0K    ./.scribus/swatches
4.0K    ./.scribus/scrapbook/tmp
4.0K    ./.scribus/scrapbook/main
12K    ./.scribus/scrapbook
382M    ./.scribus
80K    ./Documents/Accounts
4.0K    ./Documents/cpp/groupexplorer/branches/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/branches/.svn/tmp/prop-base
4.0K    ./Documents/cpp/groupexplorer/branches/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/.svn/tmp/props
16K    ./Documents/cpp/groupexplorer/branches/.svn/tmp
4.0K    ./Documents/cpp/groupexplorer/branches/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/.svn/props
56K    ./Documents/cpp/groupexplorer/branches/.svn
148K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/tmp/prop-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/tmp/props
16K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/tmp
340K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn/props
536K    ./Documents/cpp/groupexplorer/branches/toQt4/.svn
1.3M    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/tmp/prop-base
24K    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/tmp/props
36K    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/tmp
2.6M    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/props
3.9M    ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn
6.4M    ./Documents/cpp/groupexplorer/branches/toQt4/src
456K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/tmp/prop-base
12K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/tmp/props
24K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/tmp
660K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn/props
1.2M    ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn
1.8M    ./Documents/cpp/groupexplorer/branches/toQt4/images
9.1M    ./Documents/cpp/groupexplorer/branches/toQt4
9.1M    ./Documents/cpp/groupexplorer/branches
4.0K    ./Documents/cpp/groupexplorer/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/.svn/tmp/prop-base
4.0K    ./Documents/cpp/groupexplorer/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/.svn/tmp/props
16K    ./Documents/cpp/groupexplorer/.svn/tmp
4.0K    ./Documents/cpp/groupexplorer/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/.svn/props
56K    ./Documents/cpp/groupexplorer/.svn
148K    ./Documents/cpp/groupexplorer/trunk/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/trunk/.svn/tmp/prop-base
4.0K    ./Documents/cpp/groupexplorer/trunk/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/trunk/.svn/tmp/props
16K    ./Documents/cpp/groupexplorer/trunk/.svn/tmp
340K    ./Documents/cpp/groupexplorer/trunk/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/trunk/.svn/props
548K    ./Documents/cpp/groupexplorer/trunk/.svn
4.0K    ./Documents/cpp/groupexplorer/trunk/src/.moc
1.3M    ./Documents/cpp/groupexplorer/trunk/src/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/trunk/src/.svn/tmp/prop-base
24K    ./Documents/cpp/groupexplorer/trunk/src/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/trunk/src/.svn/tmp/props
36K    ./Documents/cpp/groupexplorer/trunk/src/.svn/tmp
2.6M    ./Documents/cpp/groupexplorer/trunk/src/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/trunk/src/.svn/props
4.0M    ./Documents/cpp/groupexplorer/trunk/src/.svn
2.4M    ./Documents/cpp/groupexplorer/trunk/src/.obj
284K    ./Documents/cpp/groupexplorer/trunk/src/.ui
9.2M    ./Documents/cpp/groupexplorer/trunk/src
456K    ./Documents/cpp/groupexplorer/trunk/images/.svn/prop-base
4.0K    ./Documents/cpp/groupexplorer/trunk/images/.svn/tmp/prop-base
12K    ./Documents/cpp/groupexplorer/trunk/images/.svn/tmp/text-base
4.0K    ./Documents/cpp/groupexplorer/trunk/images/.svn/tmp/props
24K    ./Documents/cpp/groupexplorer/trunk/images/.svn/tmp
672K    ./Documents/cpp/groupexplorer/trunk/images/.svn/text-base
4.0K    ./Documents/cpp/groupexplorer/trunk/images/.svn/props
1.2M    ./Documents/cpp/groupexplorer/trunk/images/.svn
1.9M    ./Documents/cpp/groupexplorer/trunk/images
2.3M    ./Documents/cpp/groupexplorer/trunk/Resources/groups
4.0K    ./Documents/cpp/groupexplorer/trunk/Resources/sheets
16K    ./Documents/cpp/groupexplorer/trunk/Resources/help/iconimg/_notes
820K    ./Documents/cpp/groupexplorer/trunk/Resources/help/iconimg
16K    ./Documents/cpp/groupexplorer/trunk/Resources/help/Templates
112K    ./Documents/cpp/groupexplorer/trunk/Resources/help/img/_notes
6.0M    ./Documents/cpp/groupexplorer/trunk/Resources/help/img
7.5M    ./Documents/cpp/groupexplorer/trunk/Resources/help
9.8M    ./Documents/cpp/groupexplorer/trunk/Resources
22M    ./Documents/cpp/groupexplorer/trunk
31M    ./Documents/cpp/groupexplorer
508K    ./Documents/cpp/KU
66M    ./Documents/cpp
311M    ./Documents/usb-backup/qalander
1.4M    ./Documents/usb-backup/TEMP/2012-05-26
6.2M    ./Documents/usb-backup/TEMP
720K    ./Documents/usb-backup/4-pdcts-Nishyma
12M    ./Documents/usb-backup/crdls
49M    ./Documents/usb-backup/tech-drawing
7.8M    ./Documents/usb-backup/slect-piks/tie3
20M    ./Documents/usb-backup/slect-piks/tie4
4.7M    ./Documents/usb-backup/slect-piks/tie5
5.1M    ./Documents/usb-backup/slect-piks/tie2
6.2M    ./Documents/usb-backup/slect-piks/tie1
333M    ./Documents/usb-backup/slect-piks
46M    ./Documents/usb-backup/Pics/canon80IX-brochurenew
100M    ./Documents/usb-backup/Pics/metal pics
569M    ./Documents/usb-backup/Pics
2.8M    ./Documents/usb-backup/acdmc/Project-MAJU/test images
1.5M    ./Documents/usb-backup/acdmc/Project-MAJU/Mathematica Fonts
17M    ./Documents/usb-backup/acdmc/Project-MAJU
9.7M    ./Documents/usb-backup/acdmc/credtls/credentials
21M    ./Documents/usb-backup/acdmc/credtls
164K    ./Documents/usb-backup/acdmc/CPP
488K    ./Documents/usb-backup/acdmc/bklt
218M    ./Documents/usb-backup/acdmc
1.6G    ./Documents/usb-backup
6.1M    ./Documents/2012-09-05
240K    ./Documents/latex-doc
20M    ./Documents/urdu-fonts/Jameel Noori Nastaleeq
33M    ./Documents/urdu-fonts
5.7M    ./Documents/Tayyab
224K    ./Documents/PTI
164K    ./Documents/Tooling-cost-injection-mold-ITS
46M    ./Documents/Khum/QM/video-lectures/lec-02
53M    ./Documents/Khum/QM/video-lectures/lec-01
98M    ./Documents/Khum/QM/video-lectures
99M    ./Documents/Khum/QM
99M    ./Documents/Khum
4.3G    ./Documents
4.0K    ./Videos
28K    ./.dbus/session-bus
32K    ./.dbus
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com/[[IMPORT]]/79423.analytics.edgekey.net/csma/plugin/csma.swf/Akama#
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com/[[IMPORT]]/79423.analytics.edgekey.net/csma/plugin/csma.swf
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com/[[IMPORT]]/79423.analytics.edgekey.net/csma/plugin
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com/[[IMPORT]]/79423.analytics.edgekey.net/csma
32K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com/[[IMPORT]]/79423.analytics.edgekey.net
36K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com/[[IMPORT]]
40K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/admin.brightcove.com
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/media.kyte.tv/#KytePersist
32K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/media.kyte.tv
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/login.yahoo.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/d.yimg.com/ks/5.6/AdPlugin_5_6_0_4.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/d.yimg.com/ks/5.6
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/d.yimg.com/ks
52K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/d.yimg.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.bluehost.com/media/shared/general/trackr.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.bluehost.com/media/shared/general
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.bluehost.com/media/shared
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.bluehost.com/media
32K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.bluehost.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/pub.widgetbox.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.k2s.cc/ext/evercookie/evercookie.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.k2s.cc/ext/evercookie
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.k2s.cc/ext
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.k2s.cc
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/skypeassets.com/#ui
8.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/skypeassets.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/effectivemeasure.net
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/swf.docstoc.com/swf/FlexViewer.169.[www.swf/Fac#]("http://www.swf/Fac#")
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/swf.docstoc.com/swf/FlexViewer.169.[www.swf]("http://www.swf")
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/swf.docstoc.com/swf
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/swf.docstoc.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.wix.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/ocw.mit.edu
40K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.battledawn.com/highscores/bdHighscoresClient.swf/b#
68K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.battledawn.com/highscores/bdHighscoresClient.swf
72K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.battledawn.com/highscores
76K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.battledawn.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/core.insightexpressai.com/adserver/fscookie/fscookie.swf
8.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/core.insightexpressai.com/adserver/fscookie
12K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/core.insightexpressai.com/adserver
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/core.insightexpressai.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/irs01.net
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.widgetserver.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/stat.ed.cupidplc.com/images/ed2.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/stat.ed.cupidplc.com/images
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/stat.ed.cupidplc.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/feedjit.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/rapidgator.net/storage.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/rapidgator.net
40K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/d1.scribdassets.com/ScribdViewer.swf
44K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/d1.scribdassets.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/affiliates.bookdepository.co.uk
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com/GEHgmUI6xj3DpGF#
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com/gNzPbnnZRH7OdEMf#
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com/GEHgmUI6xj3DpGFv#
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com/swf/ZClientController.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com/swf
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com/gNzPbnnZRH7OdEM#
88K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.zopim.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/acjs.aliyun.com/actionlog/flash/JSocket.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/acjs.aliyun.com/actionlog/flash
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/acjs.aliyun.com/actionlog
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/acjs.aliyun.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/login.alibaba.com/flash/lsa.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/login.alibaba.com/flash
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/login.alibaba.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system/web/view/collaboration/cdn/share/cobrowse.swf
8.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system/web/view/collaboration/cdn/share
12K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system/web/view/collaboration/cdn
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system/web/view/collaboration
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system/web/view
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system/web
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com/system
32K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/kbsupport.cusa.canon.com
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/a.blip.tv
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.issuu.com
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/s.ytimg.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/mail.google.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/mpsnare.iesnare.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/flash.quantserve.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.tripadvisor.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/dunya.com.pk
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cfiles.5min.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/l.yimg.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/sysimages.tq.cn/js/vip/shareObject.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/sysimages.tq.cn/js/vip
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/sysimages.tq.cn/js
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/sysimages.tq.cn
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/appassets.kickstatic.com/compiled/mediasuite_STATIC_3796/AppShell_vlycc9un.swf/org.o#
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/appassets.kickstatic.com/compiled/mediasuite_STATIC_3796/AppShell_vlycc9un.swf
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/appassets.kickstatic.com/compiled/mediasuite_STATIC_3796
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/appassets.kickstatic.com/compiled
56K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/appassets.kickstatic.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.merriam-webster.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/cdn.gigya.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/filepost.com/static/flash/storage.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/filepost.com/static/flash
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/filepost.com/static
28K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/filepost.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/content.adriver.ru
52K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/static.propellerads.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/www.askmefast.com
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/shell-open.miomni.com/Shell_2012/LIVE/SWFs
8.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/shell-open.miomni.com/Shell_2012/LIVE
12K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/shell-open.miomni.com/Shell_2012
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/shell-open.miomni.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/g-ecx.images-amazon.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/a.vimeocdn.com
16K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/i0.poll.fm/swf/storage.swf
20K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/i0.poll.fm/swf
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/i0.poll.fm
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/skype.com/#ui
4.0K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/skype.com/#user
12K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/skype.com
24K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/battlegalaxy.com/highscores/bdHighscoresClient.swf/bat#
52K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/battlegalaxy.com/highscores/bdHighscoresClient.swf
56K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/battlegalaxy.com/highscores
60K    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7/battlegalaxy.com
1.2M    ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7
1.2M    ./.macromedia/Flash_Player/#SharedObjects
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#appassets.kickstatic.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#dunya.com.pk
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#feedjit.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mail.google.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#core.insightexpressai.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#acjs.aliyun.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#stat.ed.cupidplc.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#d1.scribdassets.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#a.blip.tv
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/##/affiliates.bookdepository.co.uk
20K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/##
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#login.yahoo.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.tripadvisor.com]("http://www.tripadvisor.com")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.battledawn.com]("http://www.battledawn.com")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#g-ecx.images-amazon.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#ocw.mit.edu
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#static.issuu.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#content.adriver.ru
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#kbsupport.cusa.canon.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#shell-open.miomni.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cfiles.5min.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.merriam-webster.com]("http://www.merriam-webster.com")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#skypeassets.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#admin.brightcove.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#irs01.net
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.bluehost.com]("http://www.bluehost.com")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#filepost.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#login.alibaba.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#rapidgator.net
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.taiwanmoldmaker.com]("http://www.taiwanmoldmaker.com")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#mpsnare.iesnare.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#i0.poll.fm
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#pub.widgetbox.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#skype.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#battlegalaxy.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#swf.docstoc.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.assocomaplast.org]("http://www.assocomaplast.org")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#effectivemeasure.net
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#a.vimeocdn.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#l.yimg.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.askmefast.com]("http://www.askmefast.com")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.gresham.ac.uk]("http://www.gresham.ac.uk")
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#media.kyte.tv
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#static.wix.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#static.propellerads.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.zopim.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#cdn.widgetserver.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#static.k2s.cc
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#d.yimg.com
16K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#sysimages.tq.cn
860K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
864K    ./.macromedia/Flash_Player/macromedia.com/support/flashplayer
868K    ./.macromedia/Flash_Player/macromedia.com/support
872K    ./.macromedia/Flash_Player/macromedia.com
2.1M    ./.macromedia/Flash_Player
2.1M    ./.macromedia
0    ./.gvfs
1.7M    ./.adobe/Flash_Player/AssetCache/RB84ZYDV
1.7M    ./.adobe/Flash_Player/AssetCache
1.7M    ./.adobe/Flash_Player
16K    ./.adobe/Acrobat/9.0/Synchronizer
24K    ./.adobe/Acrobat/9.0/JavaScripts
8.0K    ./.adobe/Acrobat/9.0/Cert
4.0K    ./.adobe/Acrobat/9.0/Forms
4.0K    ./.adobe/Acrobat/9.0/Collab/Temp
8.0K    ./.adobe/Acrobat/9.0/Collab
236K    ./.adobe/Acrobat/9.0/Cache
16K    ./.adobe/Acrobat/9.0/Preferences/mozilla
40K    ./.adobe/Acrobat/9.0/Preferences
440K    ./.adobe/Acrobat/9.0
444K    ./.adobe/Acrobat
2.1M    ./.adobe
4.0K    ./Public
4.0K    ./.gnome2/nautilus-scripts
76K    ./.gnome2/keyrings
24K    ./.gnome2/accels
108K    ./.gnome2
56K    ./.pki/nssdb
60K    ./.pki
84K    ./.pulse
4.0K    ./Templates
4.0K    ./.config/goa-1.0
20K    ./.config/enchant
16K    ./.config/LibreCAD
24K    ./.config/gedit
20K    ./.config/compiz-1/compizconfig
24K    ./.config/compiz-1
32K    ./.config/evince
4.0K    ./.config/gnome-session/saved-session
8.0K    ./.config/gnome-session
4.0K    ./.config/libreoffice/3/user/autocorr
4.0K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
56K    ./.config/libreoffice/3/user/extensions/shared/registry
104K    ./.config/libreoffice/3/user/extensions/shared
28K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
92K    ./.config/libreoffice/3/user/extensions/bundled/registry
128K    ./.config/libreoffice/3/user/extensions/bundled
236K    ./.config/libreoffice/3/user/extensions
4.0K    ./.config/libreoffice/3/user/template
16K    ./.config/libreoffice/3/user/autotext
908K    ./.config/libreoffice/3/user/database/biblio
924K    ./.config/libreoffice/3/user/database
4.0K    ./.config/libreoffice/3/user/store
4.0K    ./.config/libreoffice/3/user/backup
16K    ./.config/libreoffice/3/user/temp
4.0K    ./.config/libreoffice/3/user/uno_packages/cache/uno_packages
4.0K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
16K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
4.0K    ./.config/libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
56K    ./.config/libreoffice/3/user/uno_packages/cache/registry
100K    ./.config/libreoffice/3/user/uno_packages/cache
104K    ./.config/libreoffice/3/user/uno_packages
52K    ./.config/libreoffice/3/user/gallery
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/schart/images/Bitmaps
8.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/schart/images
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/schart/menubar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/schart/toolbar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/schart/statusbar
24K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/schart
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/sweb/images/Bitmaps
8.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/sweb/images
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/sweb/menubar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/sweb/toolbar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/sweb/statusbar
24K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/sweb
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/StartModule/images/Bitmaps
8.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/StartModule/images
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/StartModule/menubar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/StartModule/toolbar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/StartModule/statusbar
24K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/StartModule
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/simpress/images/Bitmaps
8.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/simpress/images
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/simpress/menubar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/simpress/toolbar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/simpress/statusbar
24K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/simpress
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/scalc/images/Bitmaps
8.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/scalc/images
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/scalc/menubar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/scalc/toolbar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/scalc/statusbar
24K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/scalc
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/images/Bitmaps
8.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/images
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/menubar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/toolbar
4.0K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/swriter/statusbar
24K    ./.config/libreoffice/3/user/config/soffice.cfg/modules/swriter
148K    ./.config/libreoffice/3/user/config/soffice.cfg/modules
152K    ./.config/libreoffice/3/user/config/soffice.cfg
724K    ./.config/libreoffice/3/user/config
4.0K    ./.config/libreoffice/3/user/Scripts
16K    ./.config/libreoffice/3/user/wordbook
4.0K    ./.config/libreoffice/3/user/psprint/fontmetric
4.0K    ./.config/libreoffice/3/user/psprint/driver
64K    ./.config/libreoffice/3/user/psprint
40K    ./.config/libreoffice/3/user/basic/Standard
68K    ./.config/libreoffice/3/user/basic
2.4M    ./.config/libreoffice/3/user
2.4M    ./.config/libreoffice/3
2.4M    ./.config/libreoffice
444K    ./.config/chromium/Dictionaries
12K    ./.config/chromium/Default/User StyleSheets
1.5M    ./.config/chromium/Default
6.6M    ./.config/chromium
16K    ./.config/totem
16K    ./.config/software-center
4.0K    ./.config/calibre/plugins
16K    ./.config/calibre/conversion
16K    ./.config/calibre/metadata_sources
140K    ./.config/calibre
16K    ./.config/update-notifier
24K    ./.config/dconf
28K    ./.config/eog
16K    ./.config/DjVuLibre
264K    ./.config/transmission/resume
272K    ./.config/transmission/torrents
4.0K    ./.config/transmission/blocklists
580K    ./.config/transmission
16K    ./.config/gnome-control-center/backgrounds
20K    ./.config/gnome-control-center
16K    ./.config/yelp
4.0K    ./.config/ibus/bus
8.0K    ./.config/ibus
16K    ./.config/nautilus
4.0K    ./.config/gnome-disk-utility/ata-smart-ignore
8.0K    ./.config/gnome-disk-utility
4.0K    ./.config/ubuntuone
10M    ./.config
368K    ./.fontconfig
92M    ./.thumbnails/normal
2.0M    ./.thumbnails/fail/gnome-thumbnail-factory
2.1M    ./.thumbnails/fail
94M    ./.thumbnails
2.5M    ./.compiz-1/session
2.5M    ./.compiz-1
4.0K    ./.gphoto
8.0K    ./Ubuntu One
28K    ./.thunderbird/Crash Reports/submitted
4.0K    ./.thunderbird/Crash Reports/pending
108K    ./.thunderbird/Crash Reports
24K    ./.thunderbird/qcc91tvc.default/Mail/Feeds
44K    ./.thunderbird/qcc91tvc.default/Mail/Local Folders
152M    ./.thunderbird/qcc91tvc.default/Mail/pop.googlemail.com
152M    ./.thunderbird/qcc91tvc.default/Mail
456K    ./.thunderbird/qcc91tvc.default/startupCache
4.0K    ./.thunderbird/qcc91tvc.default/minidumps
4.0K    ./.thunderbird/qcc91tvc.default/Cache/5
4.0K    ./.thunderbird/qcc91tvc.default/Cache/D
4.0K    ./.thunderbird/qcc91tvc.default/Cache/F
4.0K    ./.thunderbird/qcc91tvc.default/Cache/6
4.0K    ./.thunderbird/qcc91tvc.default/Cache/7
44K    ./.thunderbird/qcc91tvc.default/Cache/C/4F
48K    ./.thunderbird/qcc91tvc.default/Cache/C
4.0K    ./.thunderbird/qcc91tvc.default/Cache/1
4.0K    ./.thunderbird/qcc91tvc.default/Cache/0
4.0K    ./.thunderbird/qcc91tvc.default/Cache/B
4.0K    ./.thunderbird/qcc91tvc.default/Cache/3
4.0K    ./.thunderbird/qcc91tvc.default/Cache/A
4.0K    ./.thunderbird/qcc91tvc.default/Cache/E
4.0K    ./.thunderbird/qcc91tvc.default/Cache/2
68K    ./.thunderbird/qcc91tvc.default/Cache/4/48
72K    ./.thunderbird/qcc91tvc.default/Cache/4
44K    ./.thunderbird/qcc91tvc.default/Cache/9/C0
48K    ./.thunderbird/qcc91tvc.default/Cache/9
4.0K    ./.thunderbird/qcc91tvc.default/Cache/8
352K    ./.thunderbird/qcc91tvc.default/Cache
167M    ./.thunderbird/qcc91tvc.default
167M    ./.thunderbird
20K    ./.emacs.d/auto-save-list
32K    ./.emacs.d
4.0K    ./.gnome2_private
16K    ./.gnucash/books
4.0K    ./.gnucash/translog
4.0K    ./.gnucash/checks
76K    ./.gnucash
896K    ./.gstreamer-0.10
8.0M    ./Desktop
420K    ./Downloads/Nishiyama/Gas-meter-japan/BRASS INSERET
29M    ./Downloads/Nishiyama/Gas-meter-japan
584K    ./Downloads/Nishiyama/4-products
596K    ./Downloads/Nishiyama/Taiwan/valvedrawing/valve-drawing-previous
1.9M    ./Downloads/Nishiyama/Taiwan/valvedrawing
668K    ./Downloads/Nishiyama/Taiwan/valve-drawing-taiwan-latest
19M    ./Downloads/Nishiyama/Taiwan
1.7M    ./Downloads/Nishiyama/SPCC
2.1M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_COVER/Valve_Cover_2
2.1M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_COVER/Valve_Cover_1
4.2M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_COVER
2.1M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_SEAT/Valve_Seat_2
11M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_SEAT/Valve_Seat_1
13M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_SEAT
2.3M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID/VALVE_GRID_DRAWING
3.9M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID/VALVE_GRID_CHANGED
1.8M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID/VALVE_GRID_PART_DRAFT
8.3M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID
2.2M    ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE
27M    ./Downloads/Nishiyama/TAYYAB_BACKUP
712K    ./Downloads/Nishiyama/Italy/enquiryforquotation
1.5M    ./Downloads/Nishiyama/Italy
94M    ./Downloads/Nishiyama
7.3M    ./Downloads/Kalekalip/Shipping-instruction
1.3M    ./Downloads/Kalekalip/purchase-orders
312K    ./Downloads/Kalekalip/comm-invoice-n-packing-list-for-samples
6.4M    ./Downloads/Kalekalip/Lapping-machine/Model-24-M
3.3M    ./Downloads/Kalekalip/Lapping-machine/Own-made
40M    ./Downloads/Kalekalip/Lapping-machine
8.4M    ./Downloads/Kalekalip/Sample-inspection-report
2.1M    ./Downloads/Kalekalip/shipping-docs/NC-167
1.3M    ./Downloads/Kalekalip/shipping-docs/scan document 60000 set
4.7M    ./Downloads/Kalekalip/shipping-docs/scan docs 42000sets
1.5M    ./Downloads/Kalekalip/shipping-docs/shipping doc lot 160
15M    ./Downloads/Kalekalip/shipping-docs
73M    ./Downloads/Kalekalip
2.3M    ./Downloads/TEMP/Cal-cmpt/CRS4/Part1
2.4M    ./Downloads/TEMP/Cal-cmpt/CRS4/Part2
2.6M    ./Downloads/TEMP/Cal-cmpt/CRS4/Part3
2.6M    ./Downloads/TEMP/Cal-cmpt/CRS4/Part4
11M    ./Downloads/TEMP/Cal-cmpt/CRS4
672K    ./Downloads/TEMP/Cal-cmpt/cal-3/Crs2/exam-n-sol
1.5M    ./Downloads/TEMP/Cal-cmpt/cal-3/Crs2/hws
18M    ./Downloads/TEMP/Cal-cmpt/cal-3/Crs2
13M    ./Downloads/TEMP/Cal-cmpt/cal-3/Crs3
1.4M    ./Downloads/TEMP/Cal-cmpt/cal-3/Crs1/hws
2.2M    ./Downloads/TEMP/Cal-cmpt/cal-3/Crs1
33M    ./Downloads/TEMP/Cal-cmpt/cal-3
1.2M    ./Downloads/TEMP/Cal-cmpt/competion-cal
45M    ./Downloads/TEMP/Cal-cmpt
93M    ./Downloads/TEMP/EXCEL
9.5M    ./Downloads/TEMP/OB
1.8M    ./Downloads/TEMP/LA-cmpt/LA-2/prjcts
2.5M    ./Downloads/TEMP/LA-cmpt/LA-2
35M    ./Downloads/TEMP/LA-cmpt/LA-4
8.5M    ./Downloads/TEMP/LA-cmpt/LA-1
3.6M    ./Downloads/TEMP/LA-cmpt/LA-5
4.3M    ./Downloads/TEMP/LA-cmpt/LA-3
54M    ./Downloads/TEMP/LA-cmpt
2.3M    ./Downloads/TEMP/Resources/groups
4.0K    ./Downloads/TEMP/Resources/sheets
16K    ./Downloads/TEMP/Resources/help/iconimg/_notes
820K    ./Downloads/TEMP/Resources/help/iconimg
16K    ./Downloads/TEMP/Resources/help/Templates
112K    ./Downloads/TEMP/Resources/help/img/_notes
6.0M    ./Downloads/TEMP/Resources/help/img
7.5M    ./Downloads/TEMP/Resources/help
9.8M    ./Downloads/TEMP/Resources
475M    ./Downloads/TEMP
24M    ./Downloads/die-sets
1.4M    ./Downloads/Natek/2012-05-26
1.7M    ./Downloads/Natek/500 SETS AG4
1.7M    ./Downloads/Natek/sample-NC-705
244K    ./Downloads/Natek/shipping-instructions
1.8M    ./Downloads/Natek/Valve-Problem
252K    ./Downloads/Natek/purchase-orders
74M    ./Downloads/Natek/piks-june-28-2012
17M    ./Downloads/Natek/Drawings/New
17M    ./Downloads/Natek/Drawings
124M    ./Downloads/Natek
230M    ./Downloads/video-lec
113M    ./Downloads/inventory-software/Fishbowl
18M    ./Downloads/inventory-software/Fishbowl Training Videos/8-Transfer Order
54M    ./Downloads/inventory-software/Fishbowl Training Videos/5-Sales
40M    ./Downloads/inventory-software/Fishbowl Training Videos/7-Manufacturing
52M    ./Downloads/inventory-software/Fishbowl Training Videos/3-purchasing
14M    ./Downloads/inventory-software/Fishbowl Training Videos/6-Picking
18M    ./Downloads/inventory-software/Fishbowl Training Videos/4-Products
53M    ./Downloads/inventory-software/Fishbowl Training Videos/2- Part
63M    ./Downloads/inventory-software/Fishbowl Training Videos/1-Setup
310M    ./Downloads/inventory-software/Fishbowl Training Videos
422M    ./Downloads/inventory-software
320K    ./Downloads/.Remittance
188K    ./Downloads/CE/die-costing-Loads/TOOLING & QUOTATION
404K    ./Downloads/CE/die-costing-Loads/New folder
2.1M    ./Downloads/CE/die-costing-Loads
164K    ./Downloads/CE/Tooling-cost-injection-mold-ITS
8.0M    ./Downloads/CE
192K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i/assignments
48K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i/calendar
124K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i/readings
6.3M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i/lectures
48K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i/study-questions
6.7M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i
240K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/Overview
80K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship/assignments/stakeholder-analysis
52K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship/assignments/the-three-perspectives-on-organizational-processes
176K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship/assignments
4.3M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship/session-schedule-and-materials
4.5M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship
44K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-ii/assignments
924K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-ii/session-overviews
44K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-ii/readings
1.1M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-ii
13M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents
252K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/styles
20K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/search
252K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images/highslide/graphics/outlines
496K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images/highslide/graphics
500K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images/highslide
148K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images/jquerybubblepopup-theme/grey/ie
296K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images/jquerybubblepopup-theme/grey
300K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images/jquerybubblepopup-theme
1.4M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images
20K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/jsp
660K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/scripts
60K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/terms/trademarks
224K    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/terms
2.5M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common
16M    ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009
16M    ./Downloads/bks/OB/15-317-summer-2009-leadership
212K    ./Downloads/bks/OB/abs-malay
40M    ./Downloads/bks/OB/Academic-Writing
27M    ./Downloads/bks/OB/fmly-biz
332K    ./Downloads/bks/OB/abs-cbm
3.5M    ./Downloads/bks/OB/Mgmt/6666.Short Guide to Writing About History, A (6th Edition) by Richard A. Marius
26M    ./Downloads/bks/OB/Mgmt
48K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/Syllabus
8.4M    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/lecture-notes
48K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/calendar
60K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/readings
48K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/projects
56K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/study-questions
8.8M    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents
248K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/styles
20K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/search
252K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images/highslide/graphics/outlines
496K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images/highslide/graphics
500K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images/highslide
148K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images/jquerybubblepopup-theme/grey/ie
296K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images/jquerybubblepopup-theme/grey
300K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images/jquerybubblepopup-theme
1.4M    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images
20K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/jsp
664K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/scripts
60K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/terms/trademarks
224K    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/terms
2.5M    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common
12M    ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011
12M    ./Downloads/bks/OB/15-320-spring-2011-stratagy
11M    ./Downloads/bks/OB/AI-prctice/workshop-material
13M    ./Downloads/bks/OB/AI-prctice
323M    ./Downloads/bks/OB
2.8M    ./Downloads/bks/talks/Khum/test images
1.5M    ./Downloads/bks/talks/Khum/Mathematica Fonts
16M    ./Downloads/bks/talks/Khum
34M    ./Downloads/bks/talks
13M    ./Downloads/bks/tech-drawing/iso-tolerence-system/Engineering-design
16K    ./Downloads/bks/tech-drawing/iso-tolerence-system/iso_shafts_files
68K    ./Downloads/bks/tech-drawing/iso-tolerence-system/tolerances_files/tolerancestxt_data
16K    ./Downloads/bks/tech-drawing/iso-tolerence-system/tolerances_files/tolerancestoc_data
16K    ./Downloads/bks/tech-drawing/iso-tolerence-system/tolerances_files/links_data
220K    ./Downloads/bks/tech-drawing/iso-tolerence-system/tolerances_files
16K    ./Downloads/bks/tech-drawing/iso-tolerence-system/iso_holes_files
224K    ./Downloads/bks/tech-drawing/iso-tolerence-system/fit_files/fastbutton_data
464K    ./Downloads/bks/tech-drawing/iso-tolerence-system/fit_files
15M    ./Downloads/bks/tech-drawing/iso-tolerence-system
82M    ./Downloads/bks/tech-drawing
37M    ./Downloads/bks/summaries
45M    ./Downloads/bks/inject-mould/InTECH/Nb
55M    ./Downloads/bks/inject-mould/InTECH
2.6M    ./Downloads/bks/inject-mould/Plenco
34M    ./Downloads/bks/inject-mould/1224.Handbook of Thermoset Plastics, 2nd Ed., Second Edition (Plastics & Elastomers) by Sidney W. Goodman
314M    ./Downloads/bks/inject-mould
22M    ./Downloads/bks/QuranPdf
42M    ./Downloads/bks/docs/CG
196K    ./Downloads/bks/docs/matlab-code-IP
1012K    ./Downloads/bks/docs/Science and Maths | Indra's Pearls_files
23M    ./Downloads/bks/docs/USB-24May2012/misc
3.5M    ./Downloads/bks/docs/USB-24May2012/CE/asd/rev-pbms
3.7M    ./Downloads/bks/docs/USB-24May2012/CE/asd
14M    ./Downloads/bks/docs/USB-24May2012/CE
188K    ./Downloads/bks/docs/USB-24May2012/Die Costing/TOOLING & QUOTATION
404K    ./Downloads/bks/docs/USB-24May2012/Die Costing/New folder
2.1M    ./Downloads/bks/docs/USB-24May2012/Die Costing
1.8M    ./Downloads/bks/docs/USB-24May2012/summaries/unsorted/Geom-n-topology
38M    ./Downloads/bks/docs/USB-24May2012/summaries/unsorted
75M    ./Downloads/bks/docs/USB-24May2012/summaries
1.8M    ./Downloads/bks/docs/USB-24May2012/Geom-n-topology
375M    ./Downloads/bks/docs/USB-24May2012
1.8M    ./Downloads/bks/docs/Geom-n-topology
486M    ./Downloads/bks/docs
274M    ./Downloads/bks/myst
1.9G    ./Downloads/bks
524K    ./Downloads/latex-installer/install-tl-20120511/tlpkg/TeXLive
1.2M    ./Downloads/latex-installer/install-tl-20120511/tlpkg/translations
2.5M    ./Downloads/latex-installer/install-tl-20120511/tlpkg/installer/wget
2.1M    ./Downloads/latex-installer/install-tl-20120511/tlpkg/installer/xz
4.9M    ./Downloads/latex-installer/install-tl-20120511/tlpkg/installer
6.5M    ./Downloads/latex-installer/install-tl-20120511/tlpkg
164K    ./Downloads/latex-installer/install-tl-20120511/readme-html.dir
220K    ./Downloads/latex-installer/install-tl-20120511/readme-txt.dir
7.1M    ./Downloads/latex-installer/install-tl-20120511
9.6M    ./Downloads/latex-installer
896K    ./Downloads/invoices/ACE-cargo
6.7M    ./Downloads/invoices
5.2M    ./Downloads/Toyota/taxes
5.2M    ./Downloads/Toyota
64M    ./Downloads/Machinery/ITS/CNC TURNING CENTER
2.2M    ./Downloads/Machinery/ITS/treatment furnaces/photograph
9.1M    ./Downloads/Machinery/ITS/treatment furnaces
75M    ./Downloads/Machinery/ITS
772K    ./Downloads/Machinery/model24
508K    ./Downloads/Machinery/EDM-wire-cut/NZ booting 
1.3M    ./Downloads/Machinery/EDM-wire-cut
248M    ./Downloads/Machinery
259M    ./Downloads/trade/bks2
3.6M    ./Downloads/trade/catalog/image/css
12K    ./Downloads/trade/catalog/image/@eaDir/Thumbs.db
16K    ./Downloads/trade/catalog/image/@eaDir
3.9M    ./Downloads/trade/catalog/image
12K    ./Downloads/trade/catalog/infor/c01/@eaDir/Thumbs.db
16K    ./Downloads/trade/catalog/infor/c01/@eaDir
9.6M    ./Downloads/trade/catalog/infor/c01
9.6M    ./Downloads/trade/catalog/infor
14M    ./Downloads/trade/catalog
1.7M    ./Downloads/trade/Jean-Cherng-quote-v2
25M    ./Downloads/trade/KTDMC
15M    ./Downloads/trade/DIAMOND TOOLS
442M    ./Downloads/trade
314M    ./Downloads/TTC - Heroes Heroines and The Wisdom of Myth
6.8G    ./Downloads/TTC - Exploring The Roots Of Religion
52M    ./Downloads/software
1.9G    ./Downloads/Philosophy, Religion, and the Meaning of Life
1.5G    ./Downloads/TTC - Meaning of Life
2.2M    ./Downloads/SSGC/protection-washer/Email-nabeel-2aug2012
1.4M    ./Downloads/SSGC/protection-washer/Protection- washer-cad-Ishtiaq
5.8M    ./Downloads/SSGC/protection-washer
204K    ./Downloads/SSGC/Lock-Assembly
15M    ./Downloads/SSGC/piks-june25-2012/temp
53M    ./Downloads/SSGC/piks-june25-2012
60M    ./Downloads/SSGC
236K    ./Downloads/.Quotations/non-local
36K    ./Downloads/.Quotations/local
276K    ./Downloads/.Quotations
15G    ./Downloads
2.2M    ./.local/share/gvfs-metadata
16K    ./.local/share/applications
16K    ./.local/share/mime/application
16K    ./.local/share/mime/packages
160K    ./.local/share/mime
32K    ./.local/share/webkit/icondatabase
36K    ./.local/share/webkit
12K    ./.local/share/folks
4.0K    ./.local/share/totem
16K    ./.local/share/telepathy/mission-control
20K    ./.local/share/telepathy
16K    ./.local/share/icc
152M    ./.local/share/zeitgeist/fts.index
165M    ./.local/share/zeitgeist
4.0K    ./.local/share/Trash/expunged
84K    ./.local/share/Trash/info
179M    ./.local/share/Trash/files/dynaform57/CRACK
1.2G    ./.local/share/Trash/files/dynaform57
1.3G    ./.local/share/Trash/files
1.3G    ./.local/share/Trash
4.0K    ./.local/share/ubuntuone/shares
4.0K    ./.local/share/ubuntuone/syncdaemon/fsm
4.0K    ./.local/share/ubuntuone/syncdaemon/vm/shared
4.0K    ./.local/share/ubuntuone/syncdaemon/vm/shares
4.0K    ./.local/share/ubuntuone/syncdaemon/vm/udfs
28K    ./.local/share/ubuntuone/syncdaemon/vm
436K    ./.local/share/ubuntuone/syncdaemon/tritcask
484K    ./.local/share/ubuntuone/syncdaemon
492K    ./.local/share/ubuntuone
1.4G    ./.local/share
1.4G    ./.local
104K    ./.fonts
4.0K    ./.kde/share/apps/kile/scripts
4.0K    ./.kde/share/apps/kile/complete/abbreviation
8.0K    ./.kde/share/apps/kile/complete
16K    ./.kde/share/apps/kile
88K    ./.kde/share/apps/okular/docdata
92K    ./.kde/share/apps/okular
24K    ./.kde/share/apps/kfileplaces
4.0K    ./.kde/share/apps/kpdf
24K    ./.kde/share/apps/kconf_update/log
28K    ./.kde/share/apps/kconf_update
168K    ./.kde/share/apps
4.0K    ./.kde/share/kde4/services
8.0K    ./.kde/share/kde4
280K    ./.kde/share/config
460K    ./.kde/share
476K    ./.kde
4.0K    ./.subversion/auth/svn.simple
4.0K    ./.subversion/auth/svn.username
4.0K    ./.subversion/auth/svn.ssl.server
4.0K    ./.subversion/auth/svn.ssl.client-passphrase
20K    ./.subversion/auth
72K    ./.subversion
808K    ./Calibre Library/Bernstein, Albert J_/Emotional Vampires_ Dealing With People Who Drain You Dry (2)
812K    ./Calibre Library/Bernstein, Albert J_
728K    ./Calibre Library/Helen McGrath/Difficult Personalities (3)
732K    ./Calibre Library/Helen McGrath
312K    ./Calibre Library/John Schember/Calibre Quick Start Guide (1)
316K    ./Calibre Library/John Schember
2.0M    ./Calibre Library
16K    ./.mission-control/accounts
20K    ./.mission-control
4.0K    ./.lyx
23G    .
```

</pre>

---

### Post by madeel12 on 2012-11-26
Let's hope that this output will be some use.  BTW, some people paste such output in a whitebox. How can we do that? The way I've publish it here is looks ugly and has eaten up a lot of space.

---

### Post by Lars Noodén on 2012-11-26
> **madeel12 said:**
> Let's hope that this output will be some use.  BTW, some people paste such output in a whitebox. How can we do that? The way I've publish it here is looks ugly and has eaten up a lot of space.

You can wrap it in [code****][/code] tags.

---

### Post by apollothethird on 2012-11-26
> **madeel12 said:**
> Let's hope that this output will be some use.  BTW, some people paste such output in a whitebox. How can we do that? The way I've publish it here is looks ugly and has eaten up a lot of space.

It's of plenty use.  I don't know exactly how the encryption work, but it appears from your output that your files are actually stored in that private folder.  If you delete that folder your files will be gone.

I'm sure this is similar to a person running wubi and getting the impression they find a resource while running Windows and delete that hidden directory.  Their wubi and all their files there would be gone too.

In order to have a personal better control and understanding of your hard drive usage, you might consider backing up your home directory, then deleting that directory (from a different (possibly temporary) login.  Make a new directory to the same path and restore your home directory to that new path.

I don't think you'd gain any space, but at least your full usage would then be clearer to you.

As far as the block output you refer to ("whitebox"), the users use code tags.  The output is pasted between the tags.

Code tags:
[ code ]
code placed here...
there are spaces between the brackets
[ /code ]

```

code placed here...
the brackets in the tags don't have spaces in them

```

An example of the code tags is above.  The code text would be in the "whitebox" had I not put spaces between the brackets.

When providing output or code you should always use code tags.  It makes your message more legible.  It makes it easier for the users to help when browsing the messages.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames))

---

### Post by varunendra on 2012-11-26
> **madeel12 said:**
> BTW, some people paste such output in a whitebox. How can we do that?

You mean like this ? *(a size-wise sorted list of your outputs, containing only those items whose size is in MBs)* -
```
1.1M ./.cache/software-center/reviews.ubuntu.com_reviews_api_1.0_review-stats-pkgnames.p__5.1.db.dbenv
1.1M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-ii
1.1M ./.mozilla/firefox/nf0t40de.default/Cache/9
1.1M ./.mozilla/firefox/nf0t40de.default/Cache/A
1.1M ./.mozilla/firefox/nf0t40de.default/Cache/B
1.2M ./Documents/cpp/groupexplorer/branches/toQt4/images/.svn
1.2M ./Documents/cpp/groupexplorer/trunk/images/.svn
1.2M ./Downloads/latex-installer/install-tl-20120511/tlpkg/translations
1.2M ./Downloads/TEMP/Cal-cmpt/competion-cal
1.2M ./.macromedia/Flash_Player/#SharedObjects
1.2M ./.macromedia/Flash_Player/#SharedObjects/JHL3K5Q7
1.2M ./.mozilla/firefox/nf0t40de.default/Cache/4
1.2M ./.mozilla/firefox/nf0t40de.default/Cache/C
1.3M ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/prop-base
1.3M ./Documents/cpp/groupexplorer/trunk/src/.svn/prop-base
1.3M ./Downloads/Kalekalip/purchase-orders
1.3M ./Downloads/Kalekalip/shipping-docs/scan document 60000 set
1.3M ./Downloads/Machinery/EDM-wire-cut
1.3M ./.mozilla/firefox/nf0t40de.default/Cache/8
1.3M ./.mozilla/firefox/nf0t40de.default/startupCache
1.4M ./Documents/usb-backup/TEMP/2012-05-26
1.4M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common/images
1.4M ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common/images
1.4M ./Downloads/Natek/2012-05-26
1.4M ./Downloads/SSGC/protection-washer/Protection- washer-cad-Ishtiaq
1.4M ./Downloads/TEMP/Cal-cmpt/cal-3/Crs1/hws
1.5M ./.config/chromium/Default
1.5M ./Documents/usb-backup/acdmc/Project-MAJU/Mathematica Fonts
1.5M ./Downloads/bks/talks/Khum/Mathematica Fonts
1.5M ./Downloads/Kalekalip/shipping-docs/shipping doc lot 160
1.5M ./Downloads/Nishiyama/Italy
1.5M ./Downloads/TEMP/Cal-cmpt/cal-3/Crs2/hws
1.6M ./.mozilla/firefox/nf0t40de.default/Cache/E
1.7M ./.adobe/Flash_Player
1.7M ./.adobe/Flash_Player/AssetCache
1.7M ./.adobe/Flash_Player/AssetCache/RB84ZYDV
1.7M ./Downloads/Natek/500 SETS AG4
1.7M ./Downloads/Natek/sample-NC-705
1.7M ./Downloads/Nishiyama/SPCC
1.7M ./Downloads/trade/Jean-Cherng-quote-v2
1.8M ./Documents/cpp/groupexplorer/branches/toQt4/images
1.8M ./Downloads/bks/docs/Geom-n-topology
1.8M ./Downloads/bks/docs/USB-24May2012/Geom-n-topology
1.8M ./Downloads/bks/docs/USB-24May2012/summaries/unsorted/Geom-n-topology
1.8M ./Downloads/Natek/Valve-Problem
1.8M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID/VALVE_GRID_PART_DRAFT
1.8M ./Downloads/TEMP/LA-cmpt/LA-2/prjcts
1.9M ./Documents/cpp/groupexplorer/trunk/images
1.9M ./Downloads/Nishiyama/Taiwan/valvedrawing
2.0M ./Calibre Library
2.0M ./.thumbnails/fail/gnome-thumbnail-factory
2.1M ./.adobe
2.1M ./Downloads/bks/docs/USB-24May2012/Die Costing
2.1M ./Downloads/CE/die-costing-Loads
2.1M ./Downloads/Kalekalip/shipping-docs/NC-167
2.1M ./Downloads/latex-installer/install-tl-20120511/tlpkg/installer/xz
2.1M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_COVER/Valve_Cover_1
2.1M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_COVER/Valve_Cover_2
2.1M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_SEAT/Valve_Seat_2
2.1M ./.macromedia
2.1M ./.macromedia/Flash_Player
2.1M ./.thumbnails/fail
2.2M ./Downloads/Machinery/ITS/treatment furnaces/photograph
2.2M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE
2.2M ./Downloads/SSGC/protection-washer/Email-nabeel-2aug2012
2.2M ./Downloads/TEMP/Cal-cmpt/cal-3/Crs1
2.2M ./.local/share/gvfs-metadata
2.3M ./Documents/cpp/groupexplorer/trunk/Resources/groups
2.3M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID/VALVE_GRID_DRAWING
2.3M ./Downloads/TEMP/Cal-cmpt/CRS4/Part1
2.3M ./Downloads/TEMP/Resources/groups
2.4M ./.config/libreoffice
2.4M ./.config/libreoffice/3
2.4M ./.config/libreoffice/3/user
2.4M ./Documents/cpp/groupexplorer/trunk/src/.obj
2.4M ./Downloads/TEMP/Cal-cmpt/CRS4/Part2
2.4M ./.mozilla/firefox/nf0t40de.default/safebrowsing
2.5M ./.cache/software-center/piston-helper
2.5M ./.compiz-1
2.5M ./.compiz-1/session
2.5M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/common
2.5M ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/common
2.5M ./Downloads/latex-installer/install-tl-20120511/tlpkg/installer/wget
2.5M ./Downloads/TEMP/LA-cmpt/LA-2
2.6M ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn/text-base
2.6M ./Documents/cpp/groupexplorer/trunk/src/.svn/text-base
2.6M ./Downloads/bks/inject-mould/Plenco
2.6M ./Downloads/TEMP/Cal-cmpt/CRS4/Part3
2.6M ./Downloads/TEMP/Cal-cmpt/CRS4/Part4
2.8M ./Documents/usb-backup/acdmc/Project-MAJU/test images
2.8M ./Downloads/bks/talks/Khum/test images
3.2M ./.cache/software-center/download-cache
3.3M ./Downloads/Kalekalip/Lapping-machine/Own-made
3.5M ./Downloads/bks/docs/USB-24May2012/CE/asd/rev-pbms
3.5M ./Downloads/bks/OB/Mgmt/6666.Short Guide to Writing About History, A (6th Edition) by Richard A. Marius
3.6M ./Downloads/TEMP/LA-cmpt/LA-5
3.6M ./Downloads/trade/catalog/image/css
3.7M ./Downloads/bks/docs/USB-24May2012/CE/asd
3.9M ./Documents/cpp/groupexplorer/branches/toQt4/src/.svn
3.9M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID/VALVE_GRID_CHANGED
3.9M ./Downloads/trade/catalog/image
4.0M ./Documents/cpp/groupexplorer/trunk/src/.svn
4.1M ./.cache/software-center/software-center-agent.db
4.2M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_COVER
4.3M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship/session-schedule-and-materials
4.3M ./Downloads/TEMP/LA-cmpt/LA-3
4.3M ./.mozilla/firefox/nf0t40de.default/thumbnails
4.5M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/internship
4.7M ./Documents/usb-backup/slect-piks/tie5
4.7M ./Downloads/Kalekalip/shipping-docs/scan docs 42000sets
4.7M ./Pictures/slect-piks/tie5
4.9M ./Downloads/latex-installer/install-tl-20120511/tlpkg/installer
5.1M ./Documents/usb-backup/slect-piks/tie2
5.1M ./Pictures/slect-piks/tie2
5.2M ./Downloads/Toyota
5.2M ./Downloads/Toyota/taxes
5.7M ./Documents/Tayyab
5.8M ./Downloads/SSGC/protection-washer
6.0M ./Documents/cpp/groupexplorer/trunk/Resources/help/img
6.0M ./Downloads/TEMP/Resources/help/img
6.1M ./Documents/2012-09-05
6.2M ./Documents/usb-backup/slect-piks/tie1
6.2M ./Documents/usb-backup/TEMP
6.2M ./Pictures/slect-piks/tie1
6.3M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i/lectures
6.3M ./.mozilla/firefox/Crash Reports/pending
6.4M ./Documents/cpp/groupexplorer/branches/toQt4/src
6.4M ./Downloads/Kalekalip/Lapping-machine/Model-24-M
6.5M ./Downloads/latex-installer/install-tl-20120511/tlpkg
6.5M ./.mozilla/firefox/Crash Reports
6.6M ./.config/chromium
6.7M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents/part-i
6.7M ./Downloads/invoices
7.1M ./Downloads/latex-installer/install-tl-20120511
7.3M ./Downloads/Kalekalip/Shipping-instruction
7.5M ./Documents/cpp/groupexplorer/trunk/Resources/help
7.5M ./Downloads/TEMP/Resources/help
7.7M ./.cache/software-center/icons
7.8M ./Documents/usb-backup/slect-piks/tie3
7.8M ./Pictures/slect-piks/tie3
8.0M ./Desktop
8.0M ./Downloads/CE
8.3M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_GRID
8.4M ./.cache/chromium
8.4M ./.cache/chromium/Default
8.4M ./.cache/chromium/Default/Cache
8.4M ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents/lecture-notes
8.4M ./Downloads/Kalekalip/Sample-inspection-report
8.5M ./Downloads/TEMP/LA-cmpt/LA-1
8.8M ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011/contents
9.1M ./Documents/cpp/groupexplorer/branches
9.1M ./Documents/cpp/groupexplorer/branches/toQt4
9.1M ./Downloads/Machinery/ITS/treatment furnaces
9.2M ./Documents/cpp/groupexplorer/trunk/src
9.5M ./Downloads/TEMP/OB
9.6M ./Downloads/latex-installer
9.6M ./Downloads/trade/catalog/infor
9.6M ./Downloads/trade/catalog/infor/c01
9.7M ./Documents/usb-backup/acdmc/credtls/credentials
9.8M ./Documents/cpp/groupexplorer/trunk/Resources
9.8M ./Downloads/TEMP/Resources
10M ./.config
11M ./Downloads/bks/OB/AI-prctice/workshop-material
11M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_SEAT/Valve_Seat_1
11M ./Downloads/TEMP/Cal-cmpt/CRS4
11M ./.mozilla/firefox/nf0t40de.default/minidumps
12M ./Documents/usb-backup/crdls
12M ./Downloads/bks/OB/15-320-spring-2011-stratagy
12M ./Downloads/bks/OB/15-320-spring-2011-stratagy/15-320-spring-2011
13M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009/contents
13M ./Downloads/bks/OB/AI-prctice
13M ./Downloads/bks/tech-drawing/iso-tolerence-system/Engineering-design
13M ./Downloads/Nishiyama/TAYYAB_BACKUP/VALVE_SEAT
13M ./Downloads/TEMP/Cal-cmpt/cal-3/Crs3
14M ./Downloads/bks/docs/USB-24May2012/CE
14M ./Downloads/inventory-software/Fishbowl Training Videos/6-Picking
14M ./Downloads/trade/catalog
15M ./Downloads/bks/tech-drawing/iso-tolerence-system
15M ./Downloads/Kalekalip/shipping-docs
15M ./Downloads/SSGC/piks-june25-2012/temp
15M ./Downloads/trade/DIAMOND TOOLS
16M ./Downloads/bks/OB/15-317-summer-2009-leadership
16M ./Downloads/bks/OB/15-317-summer-2009-leadership/15-317-summer-2009
16M ./Downloads/bks/talks/Khum
17M ./Documents/usb-backup/acdmc/Project-MAJU
17M ./Downloads/Natek/Drawings
17M ./Downloads/Natek/Drawings/New
18M ./Downloads/inventory-software/Fishbowl Training Videos/4-Products
18M ./Downloads/inventory-software/Fishbowl Training Videos/8-Transfer Order
18M ./Downloads/TEMP/Cal-cmpt/cal-3/Crs2
19M ./Downloads/Nishiyama/Taiwan
20M ./Documents/urdu-fonts/Jameel Noori Nastaleeq
20M ./Documents/usb-backup/slect-piks/tie4
20M ./Pictures/slect-piks/tie4
21M ./.cache/software-center
21M ./Documents/usb-backup/acdmc/credtls
22M ./Documents/cpp/groupexplorer/trunk
22M ./Downloads/bks/QuranPdf
23M ./Downloads/bks/docs/USB-24May2012/misc
23M ./.mozilla/firefox/nf0t40de.default/Cache
24M ./Downloads/die-sets
25M ./Downloads/trade/KTDMC
26M ./Downloads/bks/OB/Mgmt
27M ./Downloads/bks/OB/fmly-biz
27M ./Downloads/Nishiyama/TAYYAB_BACKUP
29M ./Downloads/Nishiyama/Gas-meter-japan
31M ./.cache
31M ./Documents/cpp/groupexplorer
33M ./Documents/urdu-fonts
33M ./Downloads/TEMP/Cal-cmpt/cal-3
34M ./Downloads/bks/inject-mould/1224.Handbook of Thermoset Plastics, 2nd Ed., Second Edition (Plastics & Elastomers) by Sidney W. Goodman
34M ./Downloads/bks/talks
35M ./Downloads/TEMP/LA-cmpt/LA-4
37M ./Downloads/bks/summaries
38M ./Downloads/bks/docs/USB-24May2012/summaries/unsorted
40M ./Downloads/bks/OB/Academic-Writing
40M ./Downloads/inventory-software/Fishbowl Training Videos/7-Manufacturing
40M ./Downloads/Kalekalip/Lapping-machine
42M ./Downloads/bks/docs/CG
45M ./Downloads/bks/inject-mould/InTECH/Nb
45M ./Downloads/TEMP/Cal-cmpt
46M ./Documents/Khum/QM/video-lectures/lec-02
46M ./Documents/usb-backup/Pics/canon80IX-brochurenew
46M ./Pictures/Pics/canon80IX-brochurenew
49M ./Documents/usb-backup/tech-drawing
52M ./Downloads/inventory-software/Fishbowl Training Videos/3-purchasing
52M ./Downloads/software
53M ./Documents/Khum/QM/video-lectures/lec-01
53M ./Downloads/inventory-software/Fishbowl Training Videos/2- Part
53M ./Downloads/SSGC/piks-june25-2012
54M ./Downloads/inventory-software/Fishbowl Training Videos/5-Sales
54M ./Downloads/TEMP/LA-cmpt
55M ./Downloads/bks/inject-mould/InTECH
60M ./Downloads/SSGC
62M ./Pictures/temp2
63M ./Downloads/inventory-software/Fishbowl Training Videos/1-Setup
64M ./Downloads/Machinery/ITS/CNC TURNING CENTER
66M ./Documents/cpp
73M ./Downloads/Kalekalip
74M ./Downloads/Natek/piks-june-28-2012
75M ./Downloads/bks/docs/USB-24May2012/summaries
75M ./Downloads/Machinery/ITS
82M ./Downloads/bks/tech-drawing
92M ./.thumbnails/normal
93M ./Downloads/TEMP/EXCEL
94M ./Downloads/Nishiyama
94M ./.thumbnails
98M ./Documents/Khum/QM/video-lectures
99M ./Documents/Khum
99M ./Documents/Khum/QM
100M ./Documents/usb-backup/Pics/metal pics
100M ./Pictures/Pics/metal pics
113M ./Downloads/inventory-software/Fishbowl
124M ./Downloads/Natek
132M ./.mozilla/firefox/nf0t40de.default
138M ./.mozilla
138M ./.mozilla/firefox
152M ./.local/share/zeitgeist/fts.index
152M ./.thunderbird/qcc91tvc.default/Mail
152M ./.thunderbird/qcc91tvc.default/Mail/pop.googlemail.com
165M ./.local/share/zeitgeist
167M ./.thunderbird
167M ./.thunderbird/qcc91tvc.default
179M ./.local/share/Trash/files/dynaform57/CRACK
218M ./Documents/usb-backup/acdmc
230M ./Downloads/video-lec
248M ./Downloads/Machinery
259M ./Downloads/trade/bks2
274M ./Downloads/bks/myst
310M ./Downloads/inventory-software/Fishbowl Training Videos
311M ./Documents/usb-backup/qalander
311M ./Music
314M ./Downloads/bks/inject-mould
314M ./Downloads/TTC - Heroes Heroines and The Wisdom of Myth
323M ./Downloads/bks/OB
333M ./Documents/usb-backup/slect-piks
333M ./Pictures/slect-piks
375M ./Downloads/bks/docs/USB-24May2012
382M ./.scribus
422M ./Downloads/inventory-software
442M ./Downloads/trade
475M ./Downloads/TEMP
486M ./Downloads/bks/docs
569M ./Documents/usb-backup/Pics
569M ./Pictures/Pics
964M ./Pictures
```

Just type [noparse]```
 in the beginning and 
```[/noparse] in the end of the text that you want to put in the 'Code' box. Here's an example (**Post #6**, read only the 'PS:' part of the post) - [http://ubuntuforums.org/showthread.php?p=12368389](http://ubuntuforums.org/showthread.php?p=12368389)

I would request you to edit your 2nd last post and put the output in code tags now. I indeed looks ugly (and scary !! :))


By the way, I don't see a **.private** folder at all ! Maybe because it's not a normal file or directory, but a representation of the contents listed above *(just a guess, because I don't know how encryption works)*. But did you follow the link I gave you in my [earlier post]("http://ubuntuforums.org/showthread.php?p=12365449")?

I think you can safely copy all your data to a non-encrypted drive, then copy it back (after removing encryption if you wish).



**EDIT :**
Oops ! Beaten by Two posters in a row !!

---

