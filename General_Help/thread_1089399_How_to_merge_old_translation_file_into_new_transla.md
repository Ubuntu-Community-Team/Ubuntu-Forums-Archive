---
title: "How to merge old translation file into new translation ascii .po file?"
date: 2009-03-07
forum: General Help
---

### Post by abcuser on 2009-03-07
Hi,
I have translated chess game program PyChess 0.8 from English to Slovenian. This 0.8 version is included by default in Ubuntu 8.10 repository. I translated program using Launchpad translation system. But know I have found out that 0.8 has some nasty bug and it is useless for me, but found out that this bug was solved in 0.10 alfa development version. So I downloaded this 0.10 alfa version from subversion. PyChess is written in Python language so I don't need to compile, just run program.

Now to my problem. I have translated .po file. Each translation string has three lines like following sample:
```

#: glade/newInOut.glade:8 lib/pychess/widgets/ionest.py:495
msgid "New Game"
msgstr "Nova igra"

```

The new alfa .po file has the following content:
```

#: glade/newInOut.glade:8 lib/pychess/widgets/ionest.py:537
msgid "New Game"
msgstr ""

```

New alfa .po file has many new strings. So I would like to merge my translation file from older version to new file. The logic is. Compare msgid from old file to new file and where equal then msgstr string from old file should be copied to msgstr in new file.

How to merge two .po files?

When Google-ing I have found there is WinMerge program on Windows. Is there any like tool in Ubuntu?

Regards

---

### Post by abcuser on 2009-03-07
Hi,
found out solution.

1. I installed Lokalize (KDE translation program):
sudo apt-get install localize

2. I opened new translation file using File | Open

3. I opened old translation file using Sync | Open file for sync/merge

4. I executed Sync | Copy all new translations

5. File | Save

Problem solved.

Regards

---

