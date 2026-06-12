---
title: "firefox update adds unwanted search plugins"
date: 2006-08-02
forum: Desktop Environments
---

### Post by helicase on 2006-08-02
I deleted  a couple of firefox search plugins that I don't use (from /usr/share/firefox/searchplugins), but after every update they're back. I tried removing all write permissions for this folder, but that didn't help. Does anyone know how I can keep these unwanted search plugins from reappearing?

---

### Post by timetunnel on 2006-08-02
That's the way the package manager works. It ensures that files that have to be there are there (with the right version number if applicable). So every time you update Firefox it recognizes the missing seach plugins and puts the files there again. Fiddling round with permissions won't help because you install packages as root, who can write to every folder. AFAIK there's nothing you can do than to delete the files manually after each update.

I don't like this concept for the Firefox package. Every user should be able to configure and delete the search plugins like he wants to.

---

### Post by helicase on 2006-08-02
> Fiddling round with permissions won't help because you install packages as root, who can write to every folder.
Hm, I removed write permissions for the owner of the folder (which is root), so I thought I had that covered, but apparently not.

> AFAIK there's nothing you can do than to delete the files manually after each update.
Well, that's why I asked; I didn't want to delete them for the umpteenth time.

> I don't like this concept for the Firefox package. Every user should be able to configure and delete the search plugins like he wants to.
Agreed.

Too bad there doesn't seem to be a solution. Thanks for your answer anyway.

---

