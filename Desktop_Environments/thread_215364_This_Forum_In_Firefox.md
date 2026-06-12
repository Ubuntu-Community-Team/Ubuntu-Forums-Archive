---
title: "This Forum In Firefox"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Sonofmoog on 2006-07-13
Somehow I have messed up my Firefox configuration.  The attached screenshot is how the forum displays presently.  I've checked every configuration setting I can find.  I have a no Javascript extension loaded, and when I check the javascript console, it reports some errors parsing the page stylesheet, but that is all that I can find that might explain what is happening here, but I have no clue how to fix it.  This does not happen in Epiphany.  My Firefox version is 1.5.0.4

TIA

---

### Post by T700 on 2006-07-13
I'm seeing basically the same thing in the same version of Firefox.  I just assumed it was due to the on going tweaks to the code as the admins upgrade the board.

Paul

---

### Post by x64Jimbo on 2006-07-13
Confirmed. I am seeing this problem as well. I want the old forum back! :(

---

### Post by jjross on 2006-07-13
yeah, it looks like someone has been messing with the forum setting again

---

### Post by Sonofmoog on 2006-07-13
> **jjross said:**
> try clicking the box to the left of the X in the upper right hand corner of the browser page and see what that does

It just maximized, then restored my page ..

---

### Post by art on 2006-07-13
I was just about to start a thread on this...
Anyway, disabling adblock on Ubuntuforums brings it back to normal.

---

### Post by jjross on 2006-07-13
oops, my mistake I did not read your post well enough:D

---

### Post by aysiu on 2006-07-13
Mine is Firefox 1.5.0.4, and I'm using the one from Mozilla.

---

### Post by superm1 on 2006-07-13
What is adblock filtering from the forums exactly?

---

### Post by Sonofmoog on 2006-07-13
> **art said:**
> I was just about to start a thread on this...
Anyway, disabling adblock on Ubuntuforums brings it back to normal.

I checked my adblock dialog and ubuntuforums is not in there.  I've checked every setting I can find, and all I see is a dialog for adding sites to be blocked, and nothing like a white list of sites to allow.  So, if adblock is my culprit, it appears to be all or none.  Bummer.

I've managed to create a half-way decent looking page by playing around in the text size dialog, so I may live with this for awhile.  

Thanks for the response.

---

### Post by jjross on 2006-07-13
I just disabled adblock and then the forum displays properly,just need to figure out how to reset adblock to not do this

---

### Post by Sonofmoog on 2006-07-13
> **jjross said:**
> I just disabled adblock and then the forum displays properly,just need to figure out how to reset adblock to not do this

Well, pretty close.  Finally figured out how to disable adblock:  Tools, Extensions, Right click on Adblock and choose Disable.  With all the mods the Ops have been doing here, I'm no longer completely sure what a default display should look like, but I've got one I can live with for awhile.  I'll just have to remember to turn adblock off when I join the forum, and turn it on when I leave.

Thanks for your help.

---

### Post by art on 2006-07-13
I have Adblock Plus installed, and there is a little bug icon on the right bottom, which on the right click has an option to disable on website, so I can disable it on ubuntuforums.org. Maybe you can installed this instead of Adblock.

---

### Post by jjross on 2006-07-13
I just tried this, it appears to be in filter set G
open adblock,under filters reset the hit statistics, reload the browser page then look in adblock and see which entry shows a hit, the rest should say 0, click on the little green dot on the right side of that entry and it should disable that one filter, it worked for me . give it a try

---

### Post by userundefine on 2006-07-13
Here's mine... I don't have adblock installed, but I don't see why that would affect it anyway.

I like the new forum style.  Very clean.

---

### Post by Sonofmoog on 2006-07-13
> **jjross said:**
> I just tried this, it appears to be in filter set G
open adblock,under filters reset the hit statistics, reload the browser page then look in adblock and see which entry shows a hit, the rest should say 0, click on the little green dot on the right side of that entry and it should disable that one filter, it worked for me . give it a try

This tip is golden!  I found the filter, but rather than disabling it, I chose to suspend adblock on this forum.  My display is fixed.  Thanks again for your help.

Now, what do you know about gDesklets?

---

### Post by jjross on 2006-07-13
dont know much about gdesklets but just start another thread and someone will know about it , good luck and glad i could help

---

### Post by HAARP on 2006-07-14
Just a tip: When you use the "blockable items" window, you can easily see what's being blocked and what not.
Blocked items become red

---

### Post by visvak on 2006-07-14
just a quick fix for those who dont wanna mess with thier adblock settings, just get the stylish extension for firefox. it displays a small icon in the status bar, use it to search for more styles for this URL, use one of the styles listed in the resulting page.

now you'll have a constant display, whatever adblock (plus) or any other extension does. i have adblock plus enabled with a stylish page style installed. here's what it looks like - 

[IMG]http://img291.imageshack.us/img291/7856/screenshot8ub.png[/IMG]

---

### Post by T700 on 2006-07-14
[Here's]("http://www.ubuntuforums.org/showthread.php?p=1254722") another thread discussing this issue.

Paul

---

### Post by MrSmith on 2006-07-14
I'm not sure why Adblock started doing this to the forums but it is blocking the CSS stylesheet. A simple fix if you are using Adblock Plus is to add a whitelist entry that looks like this: @@.ubuntu

That will allow all content to be display from any url with the letters ubuntu in it.

Hope this helps,
MrSmith

---

### Post by bruce89 on 2006-07-14
Prehaps a bug report should be created - [http://forum.pierceive.com/]("http://forum.pierceive.com/")?
This is the stylesheet line in the HTML:
[HTML]<link rel="stylesheet" type="text/css" href="clientscript/vbulletin_css/style-0ad36814-00032.css" id="vbulletin_css" />[/HTML]
Filterset.G changelog - [http://www.pierceive.com/filtersetg/changelog.txt](http://www.pierceive.com/filtersetg/changelog.txt)

---

### Post by Technoviking on 2006-07-14
Yeah, is it affecting other vBB boards also.

---

### Post by manicka on 2006-07-14
> **visvak said:**
> just a quick fix for those who dont wanna mess with thier adblock settings, just get the stylish extension for firefox. it displays a small icon in the status bar, use it to search for more styles for this URL, use one of the styles listed in the resulting page.


I wouldn't recommend using the stylish extension for the forums. The css and theme is complicated enough with out letting this extension mix it up. I think it will only cause you grief in the long run

---

### Post by elamericano on 2006-07-14
> **bruce89 said:**
> Prehaps a bug report should be created - [http://forum.pierceive.com/]("http://forum.pierceive.com/")?


A "False Positive" has been reported to Filterset.G.

---

### Post by foofightrs777 on 2006-07-14
> **MrSmith said:**
> I'm not sure why Adblock started doing this to the forums but it is blocking the CSS stylesheet. A simple fix if you are using Adblock Plus is to add a whitelist entry that looks like this: @@.ubuntu

That will allow all content to be display from any url with the letters ubuntu in it.

Hope this helps,
MrSmith


I was just about to post this.  It works like a charm :)

---

### Post by Cable on 2006-07-15
You need to have access to the adblock toolbar button.  Open its dropdown menu, and check "Disable on ubuntuforums.org" then refresh the page.  Doing this worked perfectly for me.

The above suggestion will work as well.

---

### Post by elamericano on 2006-07-17
This problem should be gone for a while, because the css file no longer matches the filter. In other words, it will display right without needing an exception rule. I'd keep those however, because the odds of it reoccurring are about 1/250. Hopefully Filterset.G will fix their filter. It was never ubuntuforum's fault.

---

