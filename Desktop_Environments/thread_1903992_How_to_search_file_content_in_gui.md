---
title: "How to search file content in gui"
date: 2012-01-03
forum: Desktop Environments
---

### Post by osx on 2012-01-03
I recently tried searching for files in the desktop version of Ubuntu 11.10 based on content and realized I didn't know how to do that in a GUI. Command line, no problem.

When I tried using Nautilus to search for file content I discovered that it only searches in the file's name, not the content. I could have sworn that I have used GUI tools to search for file content in Ubuntu in the past, but maybe I was think of something else.

So, I went to the [Ubuntu online documentation]("https://help.ubuntu.com/11.10/ubuntu-help/files-search.html") and found instructions only pertaining to filename searches.

Is there really no default GUI tool/method in Ubuntu 11.10 for searching file content? I'm no stranger to the command line, but that doesn't help people who aren't familiar with 'find' or 'grep'.

---

### Post by bluexrider on 2012-01-03
this may give you the answer  [http://ubuntuforums.org/showthread.php?t=986315](http://ubuntuforums.org/showthread.php?t=986315)

---

### Post by lswb on 2012-01-03
10.4 has "gnome-search-tool" which I believe is a GUI front end to grep, locate, find, and possibly some other command line programs. Is it available in 11.10? In 10.4, I added a nautilus script consisting of " gnome-search-tool --path=. " so it's available from right-click context menu when viewing a directory from nautilus. Not sure if you can still do that in 11.10.

---

