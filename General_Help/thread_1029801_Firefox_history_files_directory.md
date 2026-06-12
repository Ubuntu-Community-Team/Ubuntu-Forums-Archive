---
title: "Firefox history files directory"
date: 2009-01-03
forum: General Help
---

### Post by kokkus on 2009-01-03
Hi. Where can I find the firefox history files?

---

### Post by hansdown on 2009-01-03
Hi kokkus.

The history will be saved if you have certain settings.

[ATTACH]98621[/ATTACH]

If you go to edit> preferances> privacy. check the box for "keep my history...."

Also uncheck the box under private data that says "clear my private data...".

---

### Post by kokkus on 2009-01-03
Thank you but in which direcotry will the be saved in?

---

### Post by hansdown on 2009-01-03
I think it is 

>  ~/.mozilla/firefox/

---

### Post by kokkus on 2009-01-03
no it wasn't

---

### Post by hansdown on 2009-01-03
Sorry KoKKus. It's a hidden file in home.

   1.  (Ubuntu) Click the Places menu on the top left of the screen and select Home Folder. A File Browser window will appear.
   2. Click the View menu and select Show Hidden Files if it isn't already checked.
   3. Double click the folder marked .mozilla.
   4. Double click the folder marked firefox. Your profile folders are within this folder.

---

### Post by kokkus on 2009-01-03
Thank you:) I found it!
But the files there are named something saved-session....
THis is archive files right? Which format are they and how do I get the real history files (htm, gif etc...)?

---

### Post by todak on 2009-01-03
The history is kept in a file called **places.sqlite** in your firefox profile folder. Use this [https://addons.mozilla.org/en-US/firefox/addon/5817](https://addons.mozilla.org/en-US/firefox/addon/5817) to view the database.

---

### Post by kokkus on 2009-01-03
Thanks alot buddy:)
But isn't there a way I can browse the files like I can with IE in windows???

---

### Post by hansdown on 2009-01-04
Are you looking for things that you previously viewed?

I'm a little out of my depth for this one.

What I do when looking at png, etc. is right-click on it, save image as> then I can save it to desktop, pictures,etc.

---

### Post by todak on 2009-01-04
Are you perhaps thinking of the **cache** folder that contains any images or video that you may have viewed on a web page?

---

### Post by -kg- on 2009-01-04
> **kokkus said:**
> Hi. Where can I find the firefox history files?

> But isn't there a way I can browse the files like I can with IE in windows??? 

I have a feeling that you're looking for your Internet Temp files.  That, or your stored off-line pages.  I'm not sure where those would be stored, but maybe someone else will.

Other than that, your actual "History" is a list of URLs that you have viewed in the past and is accessible through the History button in the button bar at the top of the Firefox window.  Clicking on one of these links (kind of like Bookmarks) will take you to the page you were viewing.

---

