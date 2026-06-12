---
title: "Can't open Firefox"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Fipaj on 2005-10-22
Hi!

I have big problem with Firefox... Yesterday it works, but today... :/

When I'm clicking on Firefox icon in menu, nothing happen (I see FF window in panel for just 5 seconds)...

Firefox run, when I run it by sudo. I reinstall FF package, but problem doesn't disappear....

Does somebody have the same problem? Thanks for help ;)

---

### Post by heimo on 2005-10-22
These are the steps I'd try:
alt+F2
xterm

```

killall firefox-bin
mv ~/.mozilla/firefox ~/.mozilla/firefox_backup
firefox

``` 
This way you would lose your settings (could still copy bookmarks.html file to the new profile), if it doesn't work - you can just restore the profile:
```
mv ~/.mozilla/firefox_backup ~/.mozilla/firefox

``` 
You can also try completely removing and reinstalling firefox:
```
sudo apt-get --purge remove firefox
// make note if any other packages will be removed, for me it was:
// blam firefox firefox-gnome-support gnome-app-install libgecko-cil
// libgecko2.0-cil monodevelop monodoc-manual ubuntu-desktop yelp
// and reinstall all those packages:
sudo apt-get install [package-names]

``` no need to worry about ubuntu-desktop being removed, you will still have all the 
Gnome stuff installed

If these instructions don't work, you may want to try Firefox 1.5 beta 2 (notice that this is beta software and has some bugs).
[http://ubuntuforums.org/showthread.php?t=79283]("http://ubuntuforums.org/showthread.php?t=79283")

---

### Post by Fipaj on 2005-10-22
Thanks for help, Heimo...

And sorry for my bad English, I'm learning ;)

---

