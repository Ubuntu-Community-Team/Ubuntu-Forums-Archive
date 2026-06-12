---
title: "[SOLVED] clicking on FF icon gives me blank page"
date: 2009-01-08
forum: General Help
---

### Post by gilloz on 2009-01-08
This morning there were a couple of updates ready for me to download.  I went ahead and downloaded.  It said to Restart computer.  I did.  Now, when I click on my Firefox icon, I only get a blank page.  My tool bars work OK, I have no access to my Bookmarks and the address bar is blank.  How would I go back to check those two updates or uninstall them?  I have to manually enter any address for access, as I did to get here.  Any help would be appreciated.  Thanks.  Using 8.04 LTS.

---

### Post by drdenim on 2009-01-08
Were these updates to add-ons/extensions or were they to firefox itself?  Also, does the bookmark menu still drop down and just shows the default bookmarks or does it not work at all?  I'd suggest looking for the bookmark file in the firefox folder (probably .firefox or .mozilla or some combination of the sort in your home folder).  Unfortunately my computer isn't working at the moment so I can't check where my file is.

(Also, as a side note, what's LTS stand for?)

---

### Post by linux6994 on 2009-01-08
Sounds like FF got updated and did not bring along the important stuff. The stuff is not lost as it would appear. 

Look in your /home/gilloz directory via Places > Home Folder then do a crtl+H you will then see your hidden files. 

One of those files is .mozilla/firefox which contains all of your FF goodies.

For this particular issue it sounds like the profile.ini is not pointing to the correct correct directory such as gilloz.default. 

Edit the profile.ini accordingly and restart FF.

LTS = Long Term Support

Good Luck

---

### Post by gilloz on 2009-01-08
Thanks drdenim and linux6994 for your responses.  All of my toolbars function when I click on them.  My bookmarks opens, but none of my bookmarks are listed.  All that you see is Organize Bookmarks, and thats it.  I managed to find out what the two updates were:

libss0.9.8 (0.9.8g-4ubuntu3.3) to 0.9.8g-4unbuntu3.4

openssl (0.9.8g-4ubuntu3.3) to 0.9.8g-4ubuntu3.4

I somehow found this information haphazardly going through the Synaptic Package Manager. "Edit the profile.ini accordingly"  How would I do that and what information would I edit?  Not sure I understand what you mean.

---

### Post by drdenim on 2009-01-08
> **gilloz said:**
> Thanks drdenim and linux6994 for your responses.  All of my toolbars function when I click on them.  My bookmarks opens, but none of my bookmarks are listed.  All that you see is Organize Bookmarks, and thats it.  I managed to find out what the two updates were:

libss0.9.8 (0.9.8g-4ubuntu3.3) to 0.9.8g-4unbuntu3.4

openssl (0.9.8g-4ubuntu3.3) to 0.9.8g-4ubuntu3.4

I somehow found this information haphazardly going through the Synaptic Package Manager. "Edit the profile.ini accordingly"  How would I do that and what information would I edit?  Not sure I understand what you mean.
profiles.ini is located at .mozilla/firefox/profiles.ini

more profiles.ini gives me:
```

[GENERAL]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=q1id1sur.default


```
(I can't swear everything is spelled correctly in there as I'm not connected to the internet on my linux computer)

Assuming you have this file, is this what it says?  I'm not sure if they would be exactly the same or not.

---

### Post by gilloz on 2009-01-09
OK drdenim.  My profile.ini looks like yours except for the last line.  Mine says:  Path=ox3ouv0f.default.  No clue what that means.  All of my items in the tool bar remain blank, except for the Home and Print icons.  No address is shown as to the website I am in and I have to type the address to get anywhere because all of my bookmarks are missing.  I'm on the verge of doing a complete clean reinstall of Hardy, as much as I hate to do this.  Thanks for your response.

---

### Post by kiisu on 2009-01-09
I don't really think it's worth your while to do a complete OS reinstall. Worse case scenario you can just reinstall Firefox and see if the problem persists.

For the moment, why not use an alternative browser (I keep epiphany on my computer as a backup) while you work through the problem?

---

### Post by drdenim on 2009-01-09
In the same folder as progfile.ini there should be a folder with a name that matches the path name.  It should contain some files and folders that are related to addons/extensions and some other things.

I think the following is a list of the default contents (yours will probably have more than just these)
```

blocklist.xml	  compatibility.ini  history.dat     secmod.db
bookmarkbackups/  compreg.dat	     key3.db	     urlclassifier2.sqlite
bookmarks.bak	  cookies.txt	     localstore.rdf  XPC.mfasl
bookmarks.html	  extensions/	     mimeTypes.rdf   xpti.dat
Cache/		  extensions.cache   prefs.js	     XUL.mfasl
cert8.db	  extensions.ini     search.rdf
chrome/		  extensions.rdf     search.sqlite

```

Are you missing any of these files?

And yea, I'd say a complete reinstall isn't needed.  At the worst you would have to reinstall firefox.

Another thought just occurred to me.  Are you using the default firefox theme?  If not try changing it back to the default theme and see if that fixes the problem.

---

### Post by gilloz on 2009-01-10
Well, after reinstalling Firefox, that didn't help.  I even tried to change the command line for the Icon, still nothing.  So, I just did a clean re-install of Hardy and I am back where I started only everything is working fine now.  I am curious about one thing.  When I finished installing using the CD, there were 385 updates waiting for me to download.  Don't they have a separate ISO file with only the updates to burn myself a copy so as not to go through this download anymore in the future?  I really appreciate you guys staying with my post and your suggestions, honest.  I made copies of your responses for future reference.  Have a good day, all of you.  Thanks again.

---

