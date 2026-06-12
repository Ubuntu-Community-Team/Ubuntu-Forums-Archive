---
title: "I messed up with gconf please help"
date: 2011-07-20
forum: Desktop Environments
---

### Post by me.translucent on 2011-07-20
I probably was out of my mind , i tried editing the 
```
/usr/share/gconf/defaults/05_panel-default-setup.entries
``` 
file by hand , i messed up and finally whenever i try to install/remove anything 

i am getting a huge error msg like this one Please help i swear i won't do it again  
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-getoptions2.0-cil libwildmidi0 libgio-cil libsoundtouch1c2 g++-4.4
  sendmail-base libcodeblocks0 m4 libstdc++6-4.4-dev pidgin-data procmail
  libx264-98 sensible-mda sendmail-cf idle-python2.6 codeblocks-common
  libebml2 libmatroska2 libiptcdata0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  pidgin pidgin-libnotify
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
10 not fully installed or removed.
After this operation, 1,810 kB disk space will be freed.
Do you want to continue [Y/n]? Y 
(Reading database ... 292449 files and directories currently installed.)
Removing pidgin-libnotify ...
Removing pidgin ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up gconf2 (2.32.2-0ubuntu2) ...
/tmp/gconf-J2Qkem/temp.entries:40: parser error : Opening and ending tag mismatch: entry line 40 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:44: parser error : Opening and ending tag mismatch: key line 40 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:70: parser error : Opening and ending tag mismatch: entry line 70 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:74: parser error : Opening and ending tag mismatch: key line 70 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:130: parser error : Opening and ending tag mismatch: entry line 130 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:134: parser error : Opening and ending tag mismatch: key line 130 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:195: parser error : error parsing attribute name
<key><list</key>
          ^
/tmp/gconf-J2Qkem/temp.entries:195: parser error : attributes construct error
<key><list</key>
          ^
/tmp/gconf-J2Qkem/temp.entries:195: parser error : Couldn't find end of Start Tag list line 195
<key><list</key>
          ^
/tmp/gconf-J2Qkem/temp.entries:273: parser error : Opening and ending tag mismatch: entry line 273 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:277: parser error : Opening and ending tag mismatch: key line 273 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:303: parser error : Opening and ending tag mismatch: entry line 303 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:307: parser error : Opening and ending tag mismatch: key line 303 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:321: parser error : Opening and ending tag mismatch: entry line 321 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:325: parser error : Opening and ending tag mismatch: key line 321 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:403: parser error : Opening and ending tag mismatch: entry line 403 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:407: parser error : Opening and ending tag mismatch: key line 403 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:475: parser error : Opening and ending tag mismatch: entry line 475 and key
y><schema_key>/schemas/apps/panel/objects/attached_toplevel_id</schema_key></key
                                                                               ^
/tmp/gconf-J2Qkem/temp.entries:479: parser error : Opening and ending tag mismatch: key line 475 and entry
</entry>
        ^
/tmp/gconf-J2Qkem/temp.entries:481: parser error : error parsing attribute name
<key><entrylist</key>
               ^
/tmp/gconf-J2Qkem/temp.entries:481: parser error : attributes construct error
<key><entrylist</key>
               ^
/tmp/gconf-J2Qkem/temp.entries:481: parser error : Couldn't find end of Start Tag entrylist line 481
<key><entrylist</key>
               ^
/tmp/gconf-J2Qkem/temp.entries:531: parser error : Comment not terminated 
<!--</key>
<value>
  <string>TrashApplet Applet 
  <string>TrashApplet Applet --&gt;</string>
                             ^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Comment not terminated

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag key line 529

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 528

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 474

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 402

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 320

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 302

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 272

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 129

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 69

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag entry line 39

^
/tmp/gconf-J2Qkem/temp.entries:572: gins (-parser error : Premature end of data in tag entrylist line 2

^
/tmp/gconf-J2Qkem/temp.entries:572: parser error : Premature end of data in tag gconfentryfile line 1

^
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-plugins-main:
 compiz-plugins-main depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome | compiz-kde; however:
  Package compiz-gnome is not configured yet.
  Package compiz-kde is not installed.
 compiz depends on compiz-plugins-main (>= 0.9); however:
  Package compiz-plugins-main is not configured yet.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince dependNo apport report written because the error message indicates its a followup error from a previous failure.
                                        No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    s on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder:
 rhythmbox-plugin-cdrecorder depends on rhythmbox (= 0.13.3-0ubuntu6); however:
  Package rhythmbox is not configured yet.
dpkg: error processing rhythmbox-plugin-cdrecorder (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on rhythmbox (= 0.13.3-0ubuntu6); however:
  Package rhythmbox is not configured yet.
dpkg: error processing rhythmbox-plu
```gins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 unity depends on compiz; however:
  Package compiz is not configured yet.
 unity depends on compiz-plugins-main; however:
  Package compiz-plugins-main is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-main:
 compiz-fusion-plugins-main depends on compiz-plugins-main; however:
  Package compiz-plugins-main is not configured yet.
dpkg: error processing compiz-fusion-plugins-main (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 compiz-gnome
 compiz-plugins-main
 compiz
 evince
 rhythmbox
 rhythmbox-plugin-cdrecorder
 rhythmbox-plugins
 unity
 compiz-fusion-plugins-main
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/CODE]

---

### Post by rMatey on 2011-07-20
You can try this:
[http://library.gnome.org/admin/system-admin-guide/stable/gconf-28.html.en](http://library.gnome.org/admin/system-admin-guide/stable/gconf-28.html.en)

---

### Post by ajgreeny on 2011-07-20
You will need to do that with root priviliges to get the default back, I think, as it is the system wide configuration that you have changed.  Try it without root privileges first just in case it works that way, but I think you will also loose any user configuration you have made.

You could also try copying the same filesystem folder or file from a live CD and pasting it into the site where you have made the mess.

I have no idea if it will work, but perhaps worth a try if the method from rMatey is not successful.

The moral of the story is to keep backups before editing anything, or if you used gedit, change the preferences of that to keep backups before saving a file.  It has saved my bacon once or twice.

---

### Post by me.translucent on 2011-07-21
what should i give in place of the parameter ```
config-source user-configuration-source
```

---

### Post by me.translucent on 2011-08-01
i tried copying the file from the live cd too ,but it didn't work

---

