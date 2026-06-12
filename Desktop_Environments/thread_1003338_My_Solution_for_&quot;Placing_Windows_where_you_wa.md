---
title: "My Solution for &quot;Placing Windows where you want them&quot;"
date: 2008-12-06
forum: Desktop Environments
---

### Post by keithld on 2008-12-06
A few of us have been trying to "Position Windows (Apps)" that are on top of other Apps and maybe "mini-mized & on top" (Songbird seems to be the only one that will stay on top) so they are available for us to get to them quickly... This may be a bit long so bare with me... :D

I like to have Firefox open "Full Screen" and my Media Player, like Songbird opened in the upper right hand corner "Mini-mized" so it doesn't interfere with any of the buttons since I am using "Mac4Lin" as my Desktop Theme...

Welllllllllll!!! it was not working and no matter where I placed it the next time I opened Songbird or any other player they always went back to their "Default" place to open...

Well after asking the "God of Search Google" and Posting on various tech sites with no help on this subject & surfing tons of websites I decided to take a closer look at the "CompizConfig Settings Manager"...

What did I do you ask?... Well after a few frustrating hours of messing around that I think led me to this, this is what I did under **Ubuntu 8.10**:

1. Open CompizConfig Settings Manager via "**System > Preferences**" or "**Alt-F2 ccsm**".

2. Go to the "**Windows Management**" Category and choose "**Place Windows**".

3. Click the TAB "**Fixed Windows Placement**".

4. Click "**NEW**" and under the 1st item: "**Positioned Windows**". Type in the field: "**title=program name**" (program name = whatever app/program you want to place in a fixed position that will open there all the time, i.e. songbird or whatever).

5. Notice the default X Position and Y Position Values and write them down, this is the default position of the window you want to place. If I remember correctly these pertain to the very upper left corner of the screen since the begining days of computers that's where the Text based/Dos systems started to display the text when a system started up and went down from there. So that's your Starting Point, which maybe be a "Negative Number and could be or maybe not something like this: -3267 & -3267.

6. Now you can play with the X & Y numbers, I wanted Songbird to be in the Upper Right hand corner and it's "X-Position was: -3267 (upper left hand corner) so I changed that to: 3267" which I figured would put it on the right hand side of the screen.  

Yep it did...

7. Now play with the "Y-Value" to set the window lower on the screen if you want it there. Play with the values until you get it where you want it. Test it out a few times by closing the App/Program and reloading and also by Shutting down completely and then trying again after a starting up again.

Remember your initial Values are negative numbers so to move Windows to the "Right or Down" you need to make them "Less" and more towards the "Positive Side". Kinda like a "Slider"

-3256_______0______+3267

     <----Minus  |   Plus---->

Hope this helps and makes sense. :) and I have yet to figure out how to make all/other Apps/Programs "Always Stay on Top" but I sure someday there may be a solution...

---

