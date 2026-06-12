---
title: "Making file links for the desktop"
date: 2018-05-04
forum: Desktop Environments
---

### Post by luddite2k on 2018-05-04
Hi all....

So I've used Ubuntu since 12.04 and have been happy. I decided to try 18.04 and it looks OK....running it side by side with 16.04 for insurance ;-)  I have one simple issue I can't figure out? I use dropbox for some of my files and in 16.04 all I needed to do to make a desktop link was to right-click on the dropbox file (spreadsheet for example) and select "Make Link" and then drag it to my desktop. That way I had easy access to often used files that are automatically backed up. So I tried this in 18.04 and I have no "Make Link" option and cannot see how I can make file links on the desktop. Seems like a pretty simple thing after 6 years using Ubuntu but it escapes me. Anyone have the solution? I did a forum search but came up empty handed.

Thanks
Gene in the wilds of Wyoming!

---

### Post by Dennis N on 2018-05-04
You can make one using the terminal.

1) cd to Desktop
2) run a command with this pattern:

```
ln -s <path-to-link-target> <desktop-link-name>
```

An example:
```
dmn@Sydney:~/Desktop$ ln -s /mnt/Data/ Link-to-Data
```

---

