---
title: "accessing firefox bookmarks. through live cd session"
date: 2009-03-29
forum: General Help
---

### Post by mefistofeles666 on 2009-03-29
My 8.10 broke down, I upgraded from hardy, and it just didn't work. I have all the files the I need except my firefox bookmarks. Well they aren't really bookmarks, you know how you can just drag the symbol next to the url bar, and have it be a link in the bar below the url. Well I have several links like that, and I just need to get them back b4 I re-install hardy, but I don't know if theres a way to access them. so if anybody knows PLEASE let me know. I was trying opening nautilus through terminal but I couldn't get to the firefox folder.


any help truly appreciated.

I really need those bookmarks!!!! my life depends on them!!!

---

### Post by lovinglinux on 2009-03-29
> **mefistofeles666 said:**
> Well they aren't really bookmarks, you know how you can just drag the symbol next to the url bar, and have it be a link in the bar below the url. 

They are bookmarks.

> **mefistofeles666 said:**
> Well I have several links like that, and I just need to get them back b4 I re-install hardy, but I don't know if theres a way to access them. so if anybody knows PLEASE let me know. I was trying opening nautilus through terminal but I couldn't get to the firefox folder.

Bookmarks are stored in places.sqlite, which is a database file. You can copy it or your entire FF profile, which is located under *~/.mozilla/firefox/*

Next time, make backups of your FF profile using [FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109") extension.

---

### Post by mefistofeles666 on 2009-04-02
okay...sorry for the noob question but, how do you open ~./mozilla/firefox/ ?

---

### Post by sgosnell on 2009-04-02
With the file manager.  In your home directory, press Ctrl-H to show hidden files, and you should then see .mozilla.

---

### Post by mefistofeles666 on 2009-04-02
thank you for the quick response. I did it and  it has this orange symbol with a square and an X on the top right corner. and it says

"the file content could not be displayed
You do not have the permissions necessary to view the contents of ".mozilla"."

I think I have to mount it first, but I forgot how to mount my old home directory in the terminal

---

### Post by sgosnell on 2009-04-02
You may need root permissions.  Start Nautilus from the terminal with "gksudo nautilus".

If you really depend on your bookmarks, install foxmarks.  It synchronizes your bookmarks and saves them on a server, so you can access them from anywhere, with any copy of firefox.  

The bookmarks should be stored on your computer in /home/user/.mozilla/firefox/random, where user is your username, and random is a directory with seemingly random characters.  In that directory, there should be another named bookmarkbackups, or similar.  In that directory, there should be files with a date for a name, and .json for an extension.  You should be able to import the latest of these and get your bookmarks back, or at least most of them.  You should also get into the habit of backing up your bookmarks regularly, if they're that important to you.  That is done from the Bookmarks/Organize Bookmarks... menu.  That's also where you import the .json files.

---

