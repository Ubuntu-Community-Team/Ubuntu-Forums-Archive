---
title: "Configuration is gone (firefox, evolution)"
date: 2009-05-03
forum: General Help
---

### Post by ENatanael on 2009-05-03
When I started my computer this morning, the first thing I did was starting Evolution to check for mails. Instead I got prompted with a configuration dialog which first asked me if I wanted to restore from a backup. As I haven't made any backup, I pressed next. Then I was asked to fill in my account information at which point I exited the configuration dialog.

After that, I stated Firefox to search for information about what could've caused this. I asked me whether I wanted to restore the previous session. This now happens every time I start Firefox and no web pages are loaded anyway. My bookmarks are gone (history is left), the google search bar isn't working, I was able to load ubuntuforums.org, but not to log in (I'm writing this from Konqueror).

Yesterday evening I noticed that Pidgin crashes almost immediately after startup (and does still).

Is there any way to fix this?

EDIT: I just noticed that my disk is completely full. Could this somehow be the cause?

EDIT2: OK, I removed the backup I made yesterday which was probably the cause of all this and Firefox and Pidgin works again :)

---

### Post by cariboo on 2009-05-03
If your hard drive is full, this will give you all sorts of errors. To clear up some space on your hard drive open an Applications-->Accessories-->Termianl and type:

```
sudo apt-get autoremove
```

and just to be sure:

```
sudo apt-get clean
```

the above two commands will clear out archived packages in /var/cache/apt/archives and remove any un-needed dependencies.

---

