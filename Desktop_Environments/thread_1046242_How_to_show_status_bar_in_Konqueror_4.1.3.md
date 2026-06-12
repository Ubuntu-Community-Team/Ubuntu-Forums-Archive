---
title: "How to show status bar in Konqueror 4.1.3"
date: 2009-01-21
forum: Desktop Environments
---

### Post by hopo on 2009-01-21
Hi all!
I just ran into a minor problem with Konqueror in Ubuntu 8.10 after upgrading from 8.04: Konqueror does not show the status bar by default.

I have tried googling and nobody seems to have had this exact problem before.

I understand that showing the status bar in some way is related to the current View Profile, but I can't find anywhere to tell Konqueror that I want it back! For instance, when I select a number of documents, I want the status bar to show me the sum total file size of the selected files.

My desktop uses Gnome, but I have added Konqueror for file management. The version is 4.1.3; the same as the KDE [libraries] installed.

---

### Post by Footer on 2009-11-29
Sorry to resurrect an old thread but I just started looking in to this and it appears to still be a problem.  I'm running Kubuntu 9.10 and I can't find how to enable the status bar in Konqueror either.  I managed to Google around and find out how to enable it via the 'filemanagement' file found in:

```
~/.kde/share/apps/konqueror/profiles
```

Change the line:

```
StatusBar=Disabled
```

to:

```
StatusBar=Enabled
```

Close and reopen Konqueror and you'll see the status bar again, but in my case it was only for a couple of tabs?  I have four tabs currently and only two of them show the status bar at the bottom.

Perhaps this is a bug?  Anyone else experiencing this behavior with Konqueror file management?

---

### Post by emaydubya on 2009-12-02
Thank you very much!

---

