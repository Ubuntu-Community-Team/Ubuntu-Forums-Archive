---
title: "Import bookmarks from Windows Firefox"
date: 2005-01-05
forum: General Help
---

### Post by Sut on 2005-01-05
Under Windows XP I use Firefox. 
Now I'm running Ubuntu and Firefox. 
Windows/Firefox stores bookmarks in /mnt/windows/xp/Documents and Settings/s/application data/mozilla/Firefox/profiles/default as a bookmarks.html file.
I want to import these bookmarks, but there's no such option. 
With Suse I just copy/paste the bookmarks.html into the Suse Mozilla/Firefox directory.

How do I do this under Ubuntu?

I first copy/paste the bookmarks.html on to the desktop, but then it gets a lock.
Opening it gives "Cannot open bookmarks.html [...] the file might present a security risk to your system[...]" {{Note: fifth try does show the html page in Firefox. Lock still on}}

I can NOT copy/paste the bookmark file into the /etc/mozilla/Firefox/profile directory. It gives an error message: " Error while copying to "/etc/mozilla...fox/profile". You do not have permissions to write to this folder."

---

### Post by tiiim on 2005-01-05
[QUOTE=Sut]Under Windows XP I use Firefox. 
Now I'm running Ubuntu and Firefox. 
Windows/Firefox stores bookmarks in /mnt/windows/xp/Documents and Settings/s/application data/mozilla/Firefox/profiles/default as a bookmarks.html file.
I want to import these bookmarks, but there's no such option. 
With Suse I just copy/paste the bookmarks.html into the Suse Mozilla/Firefox directory.

How do I do this under Ubuntu?

I first copy/paste the bookmarks.html on to the desktop, but then it gets a lock.
Opening it gives "Cannot open bookmarks.html [...] the file might present a security risk to your system[...]" {{Note: fifth try does show the html page in Firefox. Lock still on}}

I can NOT copy/paste the bookmark file into the /etc/mozilla/Firefox/profile directory. It gives an error message: " Error while copying to "/etc/mozilla...fox/profile". You do not have permissions to write to this folder."[/QUOTE]
 if you want to copy it open the root terminal and do it that way or on the normal terminal sudo to copy it.

---

### Post by Sut on 2005-01-05
[QUOTE=tiiim]if you want to copy it open the root terminal and do it that way or on the normal terminal sudo to copy it.[/QUOTE]

There is no copy command in Terminal

---

### Post by tiiim on 2005-01-05
[QUOTE=Sut]There is no copy command in Terminal[/QUOTE]
 ah right if you want to copy that file

you need to

sudo cp [file] /etc/[file name here]/[more file name]

so cd to where your html file is and write

sudo cp bookmarks.html /etc/mozilla-firefox/profile

you may have to enter your root password to confirm

---

### Post by Sut on 2005-01-05
[QUOTE=tiiim]sudo cp bookmarks.html /etc/mozilla-firefox/profile[/QUOTE]

This worked but the bookmarks do not appear in Firefox. :(

In /etc/mozilla-firefox/profile there is another folder "US" with a bookmarks.html file inside it.

When I copy bookmarks.html into that folder, the bookmarks do NOT appear in Firefox.

What is going wrong?
Where does Ubuntu store the bookmarks.html for Firefox?




*************************
Note: Type 'help' in a terminal screen. There is NO 'cp' option visible!!!!

---

### Post by tiiim on 2005-01-05
[QUOTE=Sut]This worked but the bookmarks do not appear in Firefox. :(

In /etc/mozilla-firefox/profile there is another folder "US" with a bookmarks.html file inside it.

When I copy bookmarks.html into that folder, the bookmarks do NOT appear in Firefox.

What is going wrong?
Where does Ubuntu store the bookmarks.html for Firefox?




*************************
Note: Type 'help' in a terminal screen. There is NO 'cp' option visible!!!![/QUOTE]
 ah just found it!

it be in your home directory.

go into your come click view ->show hidden files.

look for .mozilla go in that folder

then click firefox

then drop bookmarks.html in there! see if that works...

---

### Post by tiiim on 2005-01-05
[QUOTE=tiiim]ah just found it!

it be in your home directory.

go into your come click view ->show hidden files.

look for .mozilla go in that folder

then click firefox

then drop bookmarks.html in there! see if that works...[/QUOTE]
 sorry u may have to go to next folder called default.t9j or something you find a bookmarks.html file in there which you can replace.

---

### Post by wallijonn on 2005-01-05
Why didn't you do a bookmark export under WXP (Start Firefox, Bookmarks -> Manage Bookmarks -> File -> export) then do the same thing unde Linux Firefox but this time do an import of the file you exported?

---

### Post by tiiim on 2005-01-05
[QUOTE=wallijonn]Why didn't you do a bookmark export under WXP (Start Firefox, Bookmarks -> Manage Bookmarks -> File -> export) then do the same thing unde Linux Firefox but this time do an import of the file you exported?[/QUOTE]
 that prob save the hassle there lol

---

