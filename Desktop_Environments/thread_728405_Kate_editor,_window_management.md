---
title: "Kate editor, window management"
date: 2008-03-18
forum: Desktop Environments
---

### Post by nimy on 2008-03-18
I have Kubuntu 2.6.15-51-k7 at work and have been wrestling with Kate for some time -  I can only edit different documents within the same window - if I open a new window, the second window displays exactly the same documents, and defaults to displaying the document which is being edited in the first window.

Is it possible to open different documents in different Kate windows?  Does this require having more than one session?  (If I do need more than one session, it will be a problem, since the default on this computer at work is for a single session, with no option to add new ones.)

---

### Post by kellemes on 2008-03-19
Please follow me..
Kate -> Settings -> Configure Kate -> Sessions -> Behavior on Application Startup -> "Manually choose a session"

This will show the dialog-box at startup.. when choosing a new session from the one that's running, a new window will open with a new session.
You can also create a new session from the dialogbox **or** by starting Kate like so..
```
kate -s mynewsession
```

---

### Post by nimy on 2008-03-28
Thanks very much, sorry it's taken forever to respond.

There are no menus to alter Kate on this desktop, and the menus are otherwise so complex that I normally Alt + F2 and type in Kate at the "Run Command" prompt.

The SysAdmin who configured this machine advised me to run kate -p 0 in the Run window to launch a new instance of Kate, and that has worked.

I tried your command prompt and it also opens a new kate "mynewsession," but the output that shows up in the console window is extensive, so I'll probably stick to the above. I post it here FYI:

kio (KSycoca): Trying to open ksycoca from /var/tmp/kdecache-user/ksycoca
kio (KTrader): query for KTextEditor/Plugin : returning 4 offers
kio (KDirWatch): Available methods: Stat, DNotify
Kate (Scripting): add script: /usr/share/apps/katepart/scripts/jstest.js
Kate (Scripting): add script (desktop file): /usr/share/apps/katepart/scripts/jstest.desktop
Kate (Scripting): add script: /usr/share/apps/katepart/scripts/script-indent-c-char.js
Kate (Scripting): add script (desktop file): /usr/share/apps/katepart/scripts/script-indent-c-char.desktop
Kate (Scripting): add script: fallback, no desktop file around!
Kate (Scripting): add script: /usr/share/apps/katepart/scripts/script-indent-c-newline.js
Kate (Scripting): add script (desktop file): /usr/share/apps/katepart/scripts/script-indent-c-newline.desktop
Kate (Scripting): add script: fallback, no desktop file around!
Kate (Scripting): add script: /usr/share/apps/katepart/scripts/sort.js
Kate (Scripting): add script (desktop file): /usr/share/apps/katepart/scripts/sort.desktop
Kate (Scripting): add script: fallback, no desktop file around!
kate: Inserted command:script-indent-c-newline
kate: Inserted command:script-indent-c-char
kate: Inserted command:jstest
kate: Inserted command:sort
Kate (Scripting): Parsing indent script header
Kate (Scripting): key:NAME
Kate (Scripting): value: C style indenter
Kate (Scripting): key-length:4
Kate (Scripting): value-length:17
Kate (Scripting): key:COPYRIGHT
Kate (Scripting): value:
Kate (Scripting): key-length:9
Kate (Scripting): value-length:0
Kate (Scripting): Copyright block:
Kate (Scripting):
Based on work Copyright 2005 by Dominik Haumann
Copyright 2005 by Joseph Wenninger
Here will be the license text, Dominik has to choose
 The following line is not empty

An empty line ends this block
Kate (Scripting): key:VERSION
Kate (Scripting): value: 0.1
Kate (Scripting): key-length:7
Kate (Scripting): value-length:4
Kate (Scripting): key:ANUNKNOWNKEYWORD
Kate (Scripting): value: Version has to be in the format major.minor (both numbers)
Kate (Scripting): key-length:16
Kate (Scripting): value-length:59
Kate (Scripting): ignoring key
Kate (Scripting): key:IGNOREALSO
Kate (Scripting): value: All keywords, except COPYRIGHT are expected to have their data on one line
Kate (Scripting): key-length:10
Kate (Scripting): value-length:75
Kate (Scripting): ignoring key
Kate (Scripting): key:UNKNOWN
Kate (Scripting): value: unknown keywords are simply ignored from the information parser
Kate (Scripting): key-length:7
Kate (Scripting): value-length:64
Kate (Scripting): ignoring key
Kate (Scripting): key:CURRENTLY_KNOWN_KEYWORDS
Kate (Scripting): value: NAME,VERSION, COPYRIGHT
Kate (Scripting): key-length:24
Kate (Scripting): value-length:24
Kate (Scripting): ignoring key
Kate (Scripting): key:INFORMATION
Kate (Scripting): value: This block has to begin in the first line at the first character position
Kate (Scripting): key-length:11
Kate (Scripting): value-length:74
Kate (Scripting): ignoring key
Kate (Scripting): key:INFORMATION
Kate (Scripting): value: It is optional, but at least all files within the kde cvs,
Kate (Scripting): key-length:11
Kate (Scripting): value-length:59
Kate (Scripting): ignoring key
Kate (Scripting): key:INFORMATION
Kate (Scripting): value: which are ment for publishing are supposed to have at least the
Kate (Scripting): key-length:11
Kate (Scripting): value-length:64
Kate (Scripting): ignoring key
Kate (Scripting): key:INFORMATION
Kate (Scripting): value: COPYRIGHT block
Kate (Scripting): key-length:11
Kate (Scripting): value-length:16
Kate (Scripting): ignoring key
Kate (Scripting): key:INFORMATION
Kate (Scripting): value: These files have to be stored as UTF8
Kate (Scripting): key-length:11
Kate (Scripting): value-length:38
Kate (Scripting): ignoring key
Kate (Scripting): end of config block
kate: =================================================
kate: Trying to find Lua scripts
kate: =================================================
kate: Lua script file:/usr/share/apps/katepart/scripts/indent/script-indent-c1-test.lua
kate: Inserted command:indent
kate: Inserted command:unindent
kate: Inserted command:cleanindent
kate: Inserted command:comment
kate: Inserted command:uncomment
kate: Inserted command:goto
kate: Inserted command:kill-line
kate: Inserted command:set-tab-width
kate: Inserted command:set-replace-tabs
kate: Inserted command:set-show-tabs
kate: Inserted command:set-remove-trailing-space
kate: Inserted command:set-indent-spaces
kate: Inserted command:set-indent-width
kate: Inserted command:set-mixed-indent
kate: Inserted command:set-indent-mode
kate: Inserted command:set-auto-indent
kate: Inserted command:set-line-numbers
kate: Inserted command:set-folding-markers
kate: Inserted command:set-icon-border
kate: Inserted command:set-wrap-cursor
kate: Inserted command:set-word-wrap
kate: Inserted command:set-word-wrap-column
kate: Inserted command:set-replace-tabs-save
kate: Inserted command:set-remove-trailing-space-save
kate: Inserted command:set-highlight
kate: Inserted command:run-myself
kate: Inserted command:set-show-indent
kate: Inserted command:s
kate: Inserted command:%s
kate: Inserted command:$s
kate: Inserted command:char
kate: Inserted command:date
kate: Inserted command:find
kate: Inserted command:replace
kate: Inserted command:ifind
Kate (Document): [int KateFileTypeManager::fileType(KateDocument*)]
kio (KTrader): query for Kate/Plugin : returning 15 offers
kate: LOCAL SESSION DIR: /home/user/.kde/share/apps/kate/sessions
kate: Setting KATE_PID: '17428'
kate: FOUND SESSION: Default Session FILE: /home/user/.kde/share/apps/kate/sessions/default.katesession
ScimInputContextPlugin()
kio (KDirLister): +KDirLister
kio (KDirListerCache): +KDirListerCache
kio (KDirLister): [virtual bool KDirLister::openURL(const KURL&, bool, bool)] file:///home/user/ keep=false reload=false
kio (KDirListerCache): [bool KDirListerCache::listDir(KDirLister*, const KURL&, bool, bool)] 0x82d9c20 url=file:///home/ck
luka keep=false reload=false
kio (KDirListerCache): [void KDirListerCache::stop(KDirLister*)] lister: 0x82d9c20
kio (KDirListerCache): [void KDirListerCache::forgetDirs(KDirLister*)] 0x82d9c20
kio (KDirListerCache): listDir: Entry not in cache or reloaded: file:///home/user
kio (KDirWatch): Added Dir /home/user [KDirWatch-2]
kio (KDirWatch):  Setup DNotify (fd 128) for /home/user
kate: diff=0
kate: diff=0
kate: Inserted command:exttool-cvs-diff
kate: Inserted command:exttool-runscript
kate: Inserted command:exttool-google-selection
kio (KDirLister): [virtual bool KDirLister::openURL(const KURL&, bool, bool)] file:///home/user/path/ keep=false reload                     =false
kio (KDirListerCache): [bool KDirListerCache::listDir(KDirLister*, const KURL&, bool, bool)] 0x82d9c20 url=file:///home/ck                     luka/path keep=false reload=false
kio (KDirListerCache): [void KDirListerCache::stop(KDirLister*)] lister: 0x82d9c20
kio (KIOJob): Job::kill this=0x82ec0b8 KIO::ListJob m_progressId=0 quietly=true
kio (KDirListerCache): [void KDirListerCache::forgetDirs(KDirLister*)] 0x82d9c20
kio (KDirListerCache): [void KDirListerCache::forgetDirs(KDirLister*, const KURL&, bool)] 0x82d9c20 _url: file:///home/ckl                     uka
kio (KDirWatch): KDirWatchPrivate::removeEntry for '/home/user' sub_entry: (nil)
kio (KDirWatch): Cancelled DNotify (fd 128) for /home/user
kio (KDirWatch): Removed Dir /home/user [KDirWatch-2]
kio (KDirListerCache): listDir: Entry not in cache or reloaded: file:///home/user/path
kio (KDirWatch): Added Dir /home/user/path [KDirWatch-2]
kio (KDirWatch):  Setup DNotify (fd 128) for /home/user/path
kio (KTrader): query for ThumbCreator : returning 13 offers
kdeui (KToolBar): isearchToolBar KToolBar::removeItem item -33 not found
kdeui (KToolBar): isearchToolBar KToolBar::removeItem item -34 not found
kio (KDirListerCache): [void KDirListerCache::slotEntries(KIO::Job*, const KIO::UDSEntryList&)] new entries for file:///ho                     me/user/path
kio: KSambaShare::readSmbConf /etc/samba/smb.conf
kio: KSambaShare: Found path: /tmp/
kio: KSambaShare: Found path: /var/lib/samba/printers/
kio (KDirWatch): Added File /etc/samba/smb.conf [KDirWatch-2]
kio (KDirWatch): Added Dir /etc/samba for /etc/samba/smb.conf
kio (KDirWatch):  Setup DNotify (fd 129) for /etc/samba
kio (KDirWatch): Added File /etc/security/fileshare.conf NotExisting [KDirWatch-2]
kio (KDirWatch): Added Dir /etc/security for /etc/security/fileshare.conf
kio (KDirWatch):  Setup DNotify (fd 130) for /etc/security
kio: KNFSShare: Could not found exports file!
kio (KDirListerCache): [void KDirListerCache::slotResult(KIO::Job*)] finished listing file:///home/user/path

---

