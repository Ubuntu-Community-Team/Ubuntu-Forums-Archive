---
title: "Updating errors"
date: 2009-01-17
forum: General Help
---

### Post by rosscollins88 on 2009-01-17
Hi folks

My first post is a long one.  I apologise in advance, but if you could please read all of the post as there is quite a lot of details.

A complete newb here, requiring your help.  I installed ubuntu8.10 with no issues.  I then went on to install vlc player again with no issues.  When i first tried to play a dvd with it, vlc would close once it tried to play it.  At first i thought this might be due to the fact that in window i set my dvd player to a different region. (I am now not so sure about this).  

When installing ubuntu i also set up a sharing partition.  It is NTFS format.  I placed some music and films in there.  Rhythmbox can play the music files, but if i try using vlc for either movie or music, it closes again immediately.  I get the exact same problems with totem movie player.

My next thought was that perhaps its because i havent updated the system yet.  There were 219 updates available.  All downloaded, but when installing my computer froze.  It froze trying to update something to do with the Totem player.  I resorted to rebooting my computer.

This time an orange symbol in the taskbar said that there was 1 update available.  "acpi-support".  I have tried to install that update but got an error message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report".

Am i right in thinking this is to do with my sharing partition as in windows it is known as E:. 

I have also tried uninstalling vlc and totem, from the add/remove applications, but to no avail.  Again i get the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am unsure of what to do.  I had planned on reinstalling vlc and totem but seem unable.  Any advice greatly appreciated.

---

### Post by cdtech on 2009-01-17
> Am i right in thinking this is to do with my sharing partition as in windows it is known as E:. 
That is incorrect. This has nothing to do with your shared drives. Open a terminal and try:
```

sudo apt-get autoremove
sudo dpkg --configure -a

```
This will clear the cache, then try running (in a termianl):
```
sudo apt-get update
```

---

### Post by rosscollins88 on 2009-01-17
hey hope you dont think i was ignorant when i didnt reply in thanks, i was out for a few hours.  That allowed me to update, uninstall, and reinstall.  

Now I'm currently following a beginners guide to get full multimedia set up in ubuntu, so hopefully my other problems regarding vlc and totem will resolve.

Thank you.

One further question, is there any web pages/articles that would help me with the terminal commands and the overall running of the OS.  One of my reasons for switching to linux was to be in control of my computer and it seems to me i will need to be profeccient with the terminal

---

