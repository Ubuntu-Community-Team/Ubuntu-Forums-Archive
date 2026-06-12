---
title: "GPRename as nautilus-action"
date: 2009-11-26
forum: Desktop Environments
---

### Post by piedro on 2009-11-26
Hi! 

I installed gprename via the ubuntu repositories for karmic. 
On their Website it say's I should import the file 

"gprename.schemas" 

in nautilus-actions to create that functionality in nautilus' context menue. 

But when trying to import I get: 

> This XML file is not a valid configuration file for nautilus-actions 
(missing keys) 

What keys are we talking about? How do I get this to run? 

Here's the file (gprename is installed and running stand-alone): 

```
<?xml version="1.0" encoding="UTF-8"?>
<gconfschemafile>
  <schemalist>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/label</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/label</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <default>GPRename</default>
        <short>The label of the menu item</short>
        <long>The label of the menu item that will appear in the Nautilus popup menu when the selection matches the appearance condition settings</long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/tooltip</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/tooltip</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <default>Batch rename files or folders</default>
        <short>The tooltip of the menu item</short>
        <long>The tooltip of the menu item that will appear in the Nautilus statusbar when the user points to the Nautilus popup menu item with his/her mouse</long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/icon</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/icon</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The icon of the menu item</short>
        <long>The icon of the menu item that will appear next to the label in the Nautilus popup menu when the selection matches the appearance conditions settings</long>
      </locale>
      <default>/usr/local/share/pixmaps/gprename/gprename_nautilus-action.png</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/path</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/path</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The path of the command</short>
        <long>The path of the command to start when the user select the menu item in the Nautilus popup menu</long>
      </locale>
      <default>/usr/local/bin/gprename</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/parameters</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/parameters</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The parameters of the command</short>
        <long>The parameters of the command to start when the user selects the menu item in the Nautilus popup menu.

The parameters can contain some special tokens which are replaced by Nautilus information before starting the command:

%d: base folder of the selected file(s)
%f: the name of the selected file or the first one if many are selected
%m: space-separated list of the basenames of the selected file(s)/folder(s)
%M: space-separated list of the selected file(s)/folder(s), with their full paths
%u: GnomeVFS URI
%s: scheme of the GnomeVFS URI
%h: hostname of the GnomeVFS URI
%U: username of the :%s/GnomeVFS URI
%%: a percent sign</long>
      </locale>
      <default>%M</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/basenames</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/basenames</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of pattern to match the selected file(s)/folder(s)</short>
        <long>A list of strings with joker '*' or '?' to match the name of the selected file(s)/folder(s). Each selected items must match at least one of the filename patterns for the action to appear</long>
      </locale>
      <default>[*]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/matchcase</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/matchcase</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the filename patterns have to be case sensitive, 'false' otherwise</short>
        <long>If you need to match a filename in a case-sensitive manner, set this key to 'true'. If you also want, for example '*.jpg' to match 'photo.JPG', set 'false'</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/mimetypes</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/mimetypes</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of patterns to match the mimetypes of the selected file(s)</short>
        <long>A list of strings with joker '*' or '?' to match the mimetypes of the selected file(s). Each selected items must match at least one of the mimetype patterns for the action to appear</long>
      </locale>
      <default>[*/*]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/isfile</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/isfile</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have files, 'false' otherwise</short>
        <long>This setting is tied in with the 'isdir' setting. The valid combinations are:

isfile=TRUE and isdir=FALSE: the selection may hold only files
isfile=FALSE and isdir=TRUE: the selection may hold only folders
isfile=TRUE and isdir=TRUE': the selection may hold both files and folders
isfile=FALSE and isdir=FALSE: this is an invalid combination (your configuration will never appear)</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/isdir</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/isdir</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have folders, 'false' otherwise</short>
        <long>This setting is tied in with the 'isfile' setting. The valid combinations are:

isfile=TRUE and isdir=FALSE: the selection may hold only files
isfile=FALSE and isdir=TRUE: the selection may hold only folders
isfile=TRUE and isdir=TRUE': the selection may hold both files and folders
isfile=FALSE and isdir=FALSE: this is an invalid combination (your configuration will never appear)</long>
      </locale>
      <default>true</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/accept-multiple-files</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/accept-multiple-files</applyto>
      <owner>nautilus-actions</owner>
      <type>bool</type>
      <locale name="C">
        <short>'true' if the selection can have several items, 'false' otherwise</short>
        <long>If you need one or more files or folders to be selected, set this key to 'true'. If you want just one file or folder, set 'false'</long>
      </locale>
      <default>false</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/schemes</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/schemes</applyto>
      <owner>nautilus-actions</owner>
      <type>list</type>
      <list_type>string</list_type>
      <locale name="C">
        <short>The list of GnomeVFS schemes where the selected files should be located</short>
        <long>Defines the list of valid GnomeVFS schemes to be matched against the selected items. The GnomeVFS scheme is the protocol used to access the files. The keyword to use is the one used in the GnomeVFS URI.

Examples of GnomeVFS URI include: 
file:///tmp/foo.txt
sftp:///root@test.example.net/tmp/foo.txt

The most common schemes are:

'file': local files
'sftp': files accessed via SSH
'ftp': files accessed via FTP
'smb': files accessed via Samba (Windows share)
'dav': files accessed via WebDav

All GnomeVFS schemes used by Nautilus can be used here.</long>
      </locale>
      <default>[file]</default>
    </schema>
    <schema>
      <key>/schemas/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/version</key>
      <applyto>/apps/nautilus-actions/configurations/1dae491a-64c4-42d5-b5cc-76ff269213b5/version</applyto>
      <owner>nautilus-actions</owner>
      <type>string</type>
      <locale name="C">
        <short>The version of the configuration format</short>
        <long>The version of the configuration format that will be used to manage backward compatibility</long>
      </locale>
      <default>1.1</default>
    </schema>
  </schemalist>
</gconfschemafile>
``` 


I'd be gald to get this running. 

thx, 
piedro

---

### Post by piedro on 2009-11-26
Now I found pyRenamer. 

That is really a great script if you don't want to batch rename folders and renaming for files is enough. 

I still don't know how to integrate this into the cantext menues of nautilus. Any ideas? 

thx, p.

---

