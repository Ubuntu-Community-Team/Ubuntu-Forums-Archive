---
title: "Can't search files and folders simultaniously in Unity?"
date: 2011-05-18
forum: Desktop Environments
---

### Post by cdysthe on 2011-05-18
Hi,

When using the "Files & Folders" search from the Unity launcher I can set what to search for. There are several options like "All files", "Folders" etc. I would prefer to be able to search files /and/ folders at the same time (The unity label is after all "Files & Folders, not Files or Folders). Is there a way I can get it to work like that which to me would be much more efficient? 

If I'm missing something obvious forgive me, Unity is still new to me. But if it's not possible to search both at once I will file a feature request.

---

### Post by mc4man on 2011-05-18
It looks like it has separated files and folders, probably intentionally 
So I'd guess you're looking for an additional option

---

### Post by mcduck on 2011-05-18
All the options search for both files and folders (apart from the "Folders"-option which only searches folders)

---

### Post by mc4man on 2011-05-18
> **mcduck said:**
> All the options search for both files and folders (apart from the "Folders"-option which only searches folders)
Interesting - have never seen that here, when searching in the 'Files & Folders' lens using "All Files" it only returns files, not folders

Edit: -it seems it does, but not consistently, sometimes I can get both, many times not.

---

### Post by mcduck on 2011-05-18
Could that be because it doesn't search from everything, but only from *recently accessed* files & folders? (That's how Zeitgeist works.)

---

### Post by mc4man on 2011-05-18
What I'm seeing on 2 different installs, 1 beta2 > updated, the other release > updated
Folders, when opened, are no longer being added to the 'Recent' list when "All Files" is chosen

Though on  both installs that list, (Recent:All Files) does show a couple of folders, only those folders will show along with files with an appropriate search (in All Files

Why newly opened folders are no longer being added to the Recent:All Files list not sure.

---

### Post by mc4man on 2011-05-18
> **mcduck said:**
> Could that be because it doesn't search from everything, but only from *recently accessed* files & folders? (That's how Zeitgeist works.)
Myself do know about that - did file a bug on how the description could confuse new users - though aren't expecting much play on that (eventually people do figure it out.

[https://bugs.launchpad.net/ubuntu/+source/unity-place-files/+bug/782362](https://bugs.launchpad.net/ubuntu/+source/unity-place-files/+bug/782362)

(now if folders really aren't being added to the Recent:All files list then a better SearchHint= might be
Search Previously Opened Files or Folders

---

### Post by Frogs Hair on 2011-05-18
I ran across this yesterday ; however , did not install it because the current unity options combined with a keyboard search key give me more than  I need for daily use.[http://www.webupd8.org/2011/05/real-files-folders-search-unity-lens.html](http://www.webupd8.org/2011/05/real-files-folders-search-unity-lens.html)

---

### Post by mc4man on 2011-05-18
> **Frogs Hair said:**
> I ran across this yesterday ; however , did not install it because the current unity options combined with a keyboard search key give me more than  I need for daily use.[http://www.webupd8.org/2011/05/real-files-folders-search-unity-lens.html](http://www.webupd8.org/2011/05/real-files-folders-search-unity-lens.html)

That does sound like it may be more useful to some - will have to test it to see (I generally don't use the places much - 
Locations and apps, ect. I've made available from launcher menus - on main install have gone ahead and  removed the 2 places icons from the launcher, not needed because always in dash anyway.

(plus the gnome-search-tool is still available and useful to the degree it has been,

Anyway - testing on another machine, folders aren't added to to the Recent:All Files list either - so it has changed from when it did, whether intentionally or not don't know yet.
So again an All Files search will only return files that have been opened, no folders.

---

### Post by cdysthe on 2011-05-18
> **mc4man said:**
> Myself do know about that - did file a bug on how the description could confuse new users - though aren't expecting much play on that (eventually people do figure it out.

[https://bugs.launchpad.net/ubuntu/+source/unity-place-files/+bug/782362](https://bugs.launchpad.net/ubuntu/+source/unity-place-files/+bug/782362)

(now if folders really aren't being added to the Recent:All files list then a better SearchHint= might be
Search Previously Opened Files or Folders

Thanks! That's exactly what I need. I have removed the default files & folders search.

---

### Post by parsim on 2011-05-18
It is really odd. If I hit Super+F, the cursor sits in a box labeled "Search Files & Folders", beneath which are a scattering of a few folders in "Downloads" and "Favorites".

Once I start typing, however, NO folders are ever found, except for Favorites -- not even the ones that initially showed up under "Downloads". 

Sometimes it will actually suggest files that sit inside a matching folder, but not the folder itself.

The only way to get folders from this search, apparently, is to click and change "All Files" to "Folders" (every single time), or else mark every folder you might ever wish to search for as a Favorite.

---

### Post by mc4man on 2011-05-18
> The only way to get folders from this search, apparently, is to click and change "All Files" to "Folders" (every single time), or else mark every folder you might ever wish to search for as a Favorite.

That does seem to be the way it is even though mcduck indicated otherwise and I do have few folders available, (search-able) in the All Files:Recent list
(the search on the default "All Files" only searches that list, or at least that's how it is here
How those folders got in there remains a bit of a mystery..

As far as searching using "folders" - only folders where you've directly opened a file in will show up.
ie.  - if folder A has a file and folder B inside - if you open folder B, folder A will not be listed.
If you open the file in folder A then folder A will show up (or should.
Same thing for folder B, it won't be listed till you open a file in it (if it has one) ect.

Edit: finally did figure how you get folders into the "All File" search list (Recent
You have to open a folder with an app other than nautilus, it will then be added, sorta makes sense

---

