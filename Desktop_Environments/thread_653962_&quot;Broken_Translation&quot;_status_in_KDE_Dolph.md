---
title: "&quot;Broken Translation&quot; status in KDE Dolphin"
date: 2007-12-30
forum: Desktop Environments
---

### Post by nadrach on 2007-12-30
Kubuntu 7.10 running on various machines (ages 7 yrs to very recent, desktop/laptop) displays a common status message in KDE Dolphin of "Broken Translation" for every panel, rather than expected report on files/directories. No info on this status message (or on possible status messages) in KDE help. What is this message indicating? What is broken? How can "broken" items be repaired?

---

### Post by les-h on 2007-12-31
I Have the same message displayed!!!

---

### Post by oimon on 2008-01-01
this is a known bug with people that use en-GB language. i understand there is a workaround, but it seems a bit tedious. see here:
[https://bugs.launchpad.net/ubuntu/+source/language-pack-en/+bug/164873](https://bugs.launchpad.net/ubuntu/+source/language-pack-en/+bug/164873)


this is what i did:
cd tmp
msgunfmt /usr/share/locale-langpack/en_GB/LC_MESSAGES/d3lphin.mo  > d3lphin.po
sudo apt-get install kbabel
kbabel d3lphin.po

make changes to the last line. 
_n: 1 Item\n
%n Items

And the translated string is:
1 Item

The Translated string should be:
1 Item\n
%n Items



just to double check, here's the last few lines of my .po file
$ tail /tmp/d3lphin.po
"%n Folders selected"
msgstr "1 Folder selected"

msgid ""
"_n: 1 Item\n"
"%n Items"
msgstr ""
"1 Item\n"
"%n Items"



then do:
msgfmt d3lphin.po -o d3lphin.mo
cd /usr/share/locale-langpack/en_GB/LC_MESSAGES/
sudo cp d3lphin.mo d3lphin.mo.backup
sudo cp /tmp/d3lphin.mo .


et voila, restart dolphin, and this fixed the problem

---

### Post by nadrach on 2008-01-03
Thank you. Looks like a fix is on it's way when changes are synced. I can wait for that. Satisfying to know it is not something I have done in the installs.

---

### Post by nadrach on 2008-01-05
OK, so I couldn't wait. I needed to install "gettext" as well as "kbabel", and configure kbabel; but outside that, things now work. Thank you!

---

### Post by nadrach on 2008-01-05
Well ... one item is fixed, but there appears to be another. General Dolphin use is OK, as is hovering  the mouse pointer over files/directories, but if you actually select a file, another "Broken Translation" message appears. I'm looking, but suggestions would be appreciated.

---

### Post by oimon on 2008-01-05
woops, its the last three items that need editing...i'm not on a machine with a gui to run Kbabel at the moment, but you need to add "%n items" for the last 3 categories using kbabel, not just the last category. here are the bad bits from the po file that will need changing

msgid ""
"_n: 1 File selected (%1)\n"
"%n Files selected (%1)"
msgstr "1 File selected (%1)"

msgid ""
"_n: 1 Folder selected\n"
"%n Folders selected"
msgstr "1 Folder selected"

msgid ""
"_n: 1 Item\n"
"%n Items"
msgstr "1 Item"

---

### Post by nadrach on 2008-01-05
Found it ... them. Not just the last line of file "d3lphin.po" which relates to "Item", but the last three lines must be given the same treatment, including the penultimate and pre-penultimate translations relating to "Item selected" and "Folder selected"; with the missing second line of each translation reinstated.
Now it works ... !

---

### Post by oimon on 2008-01-05
hurray for open source! would have annoyed me to have to wait until the next version!

---

### Post by Netsurfer on 2008-03-27
If it can help Italian users, I confirm the resolution fix works great. You only have to change "item" on translation by "elemento" ("elementi" al plurale).

Thanks a lot!
Bye

---

