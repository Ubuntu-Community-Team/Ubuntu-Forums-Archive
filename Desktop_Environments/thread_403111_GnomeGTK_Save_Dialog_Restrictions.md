---
title: "Gnome/GTK Save Dialog Restrictions"
date: 2007-04-06
forum: Desktop Environments
---

### Post by Surkow on 2007-04-06
After using Ubuntu for some time I encountered some usability problems. [This]("http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00769.html") page from the gnome-devel-list describes my problems very well (be sure to read the responses).

My problem with the save dialog is that it's too restricted. Comparing it to the dialogs from Windows and MacOSX it has the following restrictions:

- Renaming is not possible;
- Moving is not possible;
- Copying is not possible;
- Pasting is not possible;
- Removing is not possible;
- Save dialogs are not expanded by default (i.e. you can't browse directories immediately).
- When using Beryl the save dialog becomes very short as described in [this]("http://ubuntuforums.org/showthread.php?t=389154&highlight=save+dialog") topic.

So my biggest problem is that it doesn't behave like simplified version of a file manager. I also want to be able to use a location bar instead of the so called "bread crums". After reading some more it seems that the save dialog is a part of GTK.

The GTK save dialog needs to be adapted or GTK needs to implement a function where the (simplified) file manager of your choice can be used instead of the standard save dialog. What would be the best solution?

---

### Post by Surkow on 2007-04-07
Bump...

---

### Post by Surkow on 2007-04-07
A visual interpretation of what could be altered:

[IMG]http://img255.imageshack.us/img255/8369/savedialogxb0.png[/IMG]
Standard save dialog


[IMG]http://img408.imageshack.us/img408/441/savedialogwithlocationbmo3.png[/IMG]
Added menu and location bar

It should be clear that you are able to switch back to using the breadcrums instead of the location bar. Only one thing that won't be possible with this solution...You can't save a file by typing the complete path and the file name directly after it (like in Windows).

---

### Post by Surkow on 2007-04-12
Nobody thinks the save dialog needs to be altered? Or did I just post this in a quiet place...

---

### Post by robbert on 2007-04-13
> **Surkow said:**
> Nobody thinks the save dialog needs to be altered? Or did I just post this in a quiet place...
I think as well the save dialog need to be altered. Your mockup looks great.

---

### Post by Surkow on 2007-04-14
> **robbert said:**
> I think as well the save dialog need to be altered. Your mockup looks great.

Thanks. :D  I just noticed I forgot to add a delete button to the menu. What kind of actions do you think are really needed in the save dialog?

I mentioned that you can't save a file by typing the complete path and the file name directly after it. But maybe with the help of the location bar this will be possible.

---

### Post by robbert on 2007-04-16
Another useful thing would be the ability to drag files and drop them in another directory.

I doubt we get any reactions here, maybe you should post your idea on a place where the Gnome or Ubuntu devs read it?

---

### Post by oomingmak on 2007-04-16
> **Surkow said:**
> Nobody thinks the save dialog needs to be altered? Or did I just post this in a quiet place...
Please ........ don't even get me started on the sorry state of the functionality in Save / Open dialogs!

You can read my comments on the subject using the link following link:

**[http://ubuntuforums.org/showthread.php?p=2404246#post2404246](http://ubuntuforums.org/showthread.php?p=2404246#post2404246)**



](*,)

---

### Post by oomingmak on 2007-04-16
> **Surkow said:**
> After using Ubuntu for some time I encountered some usability problems. [This]("http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00769.html") page from the gnome-devel-list describes my problems very well (be sure to read the responses).

My problem with the save dialog is that it's too restricted. Comparing it to the dialogs from Windows and MacOSX it has the following restrictions:

- Renaming is not possible;
- Moving is not possible;
- Copying is not possible;
- Pasting is not possible;
- Removing is not possible;
- Save dialogs are not expanded by default (i.e. you can't browse directories immediately).
- When using Beryl the save dialog becomes very short as described in [this]("http://ubuntuforums.org/showthread.php?t=389154&highlight=save+dialog") topic.

So my biggest problem is that it doesn't behave like simplified version of a file manager. I also want to be able to use a location bar instead of the so called "bread crums". After reading some more it seems that the save dialog is a part of GTK.

The GTK save dialog needs to be adapted or GTK needs to implement a function where the (simplified) file manager of your choice can be used instead of the standard save dialog. What would be the best solution?

There also needs to be the facility to work with folders in Save / Open dialogs (e.g  to be able to Create them, Copy them, Move, Rename or Delete them and access their standard context menus and Properties just like you can in Windows Explorer).

I've said it before and I'll say it again, there is absolutely **no** reason whatsoever why File Open and Save As dialogs should not be **exact **replicas of the main file management window (but simply with a file filter applied to it, in order to exclude certain unwanted file types from being visible).

However, my biggest pet hate with Nautilus is ..... totally ignoring the users click preference. :x 

People keep going on about Gnome's HIG and their "consistency", but yet this is the most flagrant disregard for the user's preference and a serious impediment to providing a consistent user experience. Making me click one way to open "folder ABC" in Nautilus, but then forcing me to open the exact *same *folder a different way (still using Nautilus) just because it happens to be in an Open / Save window, is simply infuriating (not to mention problematic for people with RSI or mobility issues for whom double-clicking is a major difficulty).

To be honest, I don't know why *any *OS uses double-click as a default action. It's idiotic because it will _never_ provide consistency across the interface (unless users are forced to start double-clicking on menus and on web links in order to match other double click actions). Seeing as that's never going to happen, then why not just standardise on one click, thereby making every object activate in exactly the same way?

Now I'm all for giving the user the choice of how they work, so if people want to engage in a bizarre mish-mash of single and double clicking then that is of course entirely up to them, but I resent such an ill-conceived method of activation being foisted on to me (and other people who prefer a more streamlined and intuitive approach to object activation).

Another major irritant with Nautilus is this:  Even when you *are *allowed to use single click (e.g. in a main Nautilus window) this action _STILL_ has not been implemented properly (in that you can't select any files because there is no 'mouse-over / hover selection' available). If you try to click the file in order to select it, then you end up launching it instead. So you have to hold down control or shift and *then *perform the click. All of that just to select a bleedin' file! I can't believe that choosing a setting specifically to _reduce_ the number of redundant clicks that I have to make, results in me having to not only click an item to select it, but also having to use two hands to do it (one on the keyboard and one on the mouse). 

Perhaps GNOME will add a footswitch as a 3rd requirement for file selection in the next release (seeing as they obviously hate to see limbs going unused)  :rolleyes:   

In Windows Explorer, if I want to select a file, I just point to it. No click, no keyboard presses, no nothing. Just point ..... and job done. 

If I want to make multiple selections in Explorer, then I can the use Ctrl or Shift keys and simply hover my mouse pointer over each file (no click necessary). However, if I *do* want to click, then I can do that as well (as the modifier key prevents the files from being launched). So _either_ method can be used.

I find myself constantly pointing at files and folders on Ubuntu and then wondering why nothing is happening. And before anyone starts bleating on about 'Linux is not Windows' I'm talking about consistency within Ubuntu's own interface and I'm simply giving Explorer as an example of a much better implementation (which is quite an indictment, seeing as not only is Explorer coded by Microsoft, but it's pretty crap even by their lame standards).

---

### Post by oomingmak on 2007-04-16
> **Surkow said:**
> After using Ubuntu for some time I encountered some usability problems. [**_[COLOR="Orange"]This[/COLOR]_**]("http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00769.html") page from the gnome-devel-list describes my problems very well (be sure to read the responses).

Interesting link that you provided there :D 

I particularly agree with this point:
> 
[I]> Users expect all the file manager functionality from the dialog, so
> no, "users" don't expect this. and nautilus is a file *manager*, that is
> an application to move, copy and generally view the file system; at
> best, it could replace an *open* dialog.[/I]

Oh yes, they do.
Don't you want to be able to create a directory to place the file you're
saving in? Or rename/or move away a file to make place for the file
you're saving? Most users do want at least these two functionalities.
And they want it to behave the same way as in their file manager.

And when these works, they expect all the other functionality of file
manager to be there. "[B]It looks like Nautilus, it works like Nautilus,
but copying is broken... Why?[/B]"

---

### Post by oomingmak on 2007-04-16
> **robbert said:**
> Another useful thing would be the ability to drag files and drop them in another directory.
I absolutely agree with your suggestion robbert.

> **robbert said:**
> 
I doubt we get any reactions here, maybe you should post your idea on a place where the Gnome or Ubuntu devs read it?
Well I doubt that it would get much attention posted elsewhere either. 

Changes like this are not just about coding, it's about adopting a different (and more open) mind set, and from what I've seen with my brief experience with Linux, GNOME appears to be a law unto itself with regards to what it thinks constitutes good interface design and usability.

I don't hold out any hope for change, but it's great to see like-minded posts and have a little rant now and then. I feel so much better for it. :)

---

### Post by oomingmak on 2007-04-16
Dare I even mention Nautilus' Alzheimer like approach to window placement and column sizing?

I've spent time sizing a window and setting the column widths to just how I wanted it. I closed the window and then immediately re-opened it only to find that all of the adjustments that I'd made had been scrapped, and the window had returned to a default position. I have not experienced this kind of errant application behaviour since the days of Windows 98.

Now it wouldn't be quite so bad if the default layout that the Nautilus window returned to was even half-way sane, but what you actually get is a column width that cuts off half the file name (because the available column width for file names is so small that it severely truncates them). Meanwhile, in the same window, you get an absolutely huge column for the modified date, with a massive blank space after each entry (because none of the date entries are anywhere near long enough to fill the width of the column space that has been provided). Why does Nautilus not size the column width to fit the dates? (seeing as they never vary in width) and then use all of the remaining space in the window to maximise the width of the File Name column (which *will *have variable length entries, many of which may be quite long).

And what's the deal with the available column selection? Where is the column for file path? The Unix filing system is chaotic and arcane enough (from the end user's perspective) without making things worse by hiding the actual location of files.

I'll often see a file in a search pane (or whatever) and have no clue where that file actually resides. I tried looking for extra columns to add (that would provide file path information) but astonishingly **none **of extra columns available were for the location path of the file. How can a "file manager" not bother to tell the user where a file is located?

Another classic example of Nautilus' ineptitude is with regards to the Wastebasket / Bin folder. How are you meant to restore a deleted file if you later want to retrieve it from the Bin? In Windows you just open your Bin, right-click on the file (or files) and then select "Restore" and the files go back to exactly where they came from (even if the various chosen files were all from totally different locations). In Nautilus you have to remember where every single file in the Wastebasket originally came from (which is quite a challenge, seeing as Nautilus doesn't even provide any file path information as standard). Then you have to manually browse back to each folder and put each individual file back there yourself. Is this really Gnome's idea of good usability?

Additionally, if you've deleted several files with the same name from different locations, in Nautilus there is no way whatsoever of differentiating one file from the other. In Explorer (details view) **every **object has a path column which shows the exact location in which it currently resides, and (in the case of the Recycle Bin) it shows the exact location where the file *used *to reside before it was moved to the Bin. So even if you have loads of files with absolutely identical names, in Explorer you can still easily differentiate them based on their origin. Good luck trying that with Nautilus.

Let me just say that I in no way expected Ubuntu to behave like Windows (it is after all a totally separate and unrelated OS). However, when something is described as a "Desktop OS", you do expect a certain amount of basic functionality (even if that functionality is accessed in a way that is different to what you are used to). However in Ubuntu it's not just a case of the method of file management being "different" or "unfamiliar", in many cases fundamental and essential functionality is simply non-existent. (For example, how any file manager could be designed without pervasive inclusion of visible file paths is beyond me).

---

### Post by oomingmak on 2007-04-16
Hmmm ....... I've just read this thread back and realised that I have made 5 posts in a row!

I did warn you not to get me started on this topic - lol  


:D

---

### Post by yabbadabbadont on 2007-04-16
Can't have six in a row though.  :D

I believe that you are preaching to the choir here.  This "dumbing down" of the interface is my main gripe with Gnome.  I we could get the file dialogs from KDE, as well as a little more control over settings, then Gnome would be wonderful to work with.

---

### Post by oomingmak on 2007-04-16
> **yabbadabbadont said:**
> Can't have six in a row though.  :D
Grrrr!



lol :mrgreen: 


> **yabbadabbadont said:**
> 
I believe that you are preaching to the choir here.
Do you think so? That's not been my experience. 

What I *usually *see are posts like these:
> 
[quote=MrKlean]I hate to disagree, but most of the stuff in windows stinks !! I never used explorer window.
[**> Link**]("http://ubuntuforums.org/showpost.php?p=2389276&postcount=89")

[quote=clash]Windows Explorer and Visual Studio? Why in gods name would you want either of those?

Especially windows explorer, whats wrong with nautilus or thunar or even konqueror?
[**>Link**]("http://ubuntuforums.org/showpost.php?p=2015612&postcount=27")[/QUOTE]
[/quote]


The kind of question that I see over and over is: *"Why use Windows Explorer when <insert Linux file manager> is so excellent?" *

And my answer would be: 
Well, apart from the litany of problems that I've already mentioned above, how about ....

**1.** Explorer has easily modifiable and accessible meta data (that is fully exposed in the UI). Sure, I can write 'notes' in Nautilus, but that's all. There are no other categories readily available to the end user. 

Also, if I want to actually *read *the notes that I have made in Nautilus, then I have to right click the file, go the properties menu and then switch to the notes tab (3 separate actions). Now imagine that you want to scan the notes of 50 files in one folder. You will have to repeat those actions 50 times over, and if you decided that you wanted to re-read one of the previous notes, then good luck remembering which file it was located in! 

In Explorer on the other hand, you have the choice to add a comment, a subject, an alternative title, author name etc. and these additions all pop up in a tooltip which is accessed simply by passing your mouse over the file or folder. So you can 'swipe' your mouse over a list of files in a folder and see at a glance all the various comments associated with each one. Not only that, but if you switch to 'Details' view in Explorer, your meta data is then permanently visible in the extra columns at the end of the window (for easy comparison). Nautilus is simply no contest in this regard (same goes for Thunar, Konqueror, Dolphin and every other Linux file manager that I have looked into (and believe me I have really searched for alternatives).

**2. **Explorer has an extensive shell extension architecture. You can easily plug in extra file types for new thumbnail previews, you can add context menus (globally or based on file type) add property sheets (i.e. tabs), icon handlers, column handlers etc. My Explorer is heavily customised to suit my needs. I even got a programmer friend of mine to knock up a couple of custom shell extensions for me based on my own specification. It was a fairly trivial affair for him and it doesn't take much time or effort (once you've find the right programming documentation for extensions, such as Code Project's Shell Extension Guide).

**3.** Still not convinced? How about Undo? I accidentally renamed a file in Nautilus and I was stunned when pressing ctrl+z on my keyboard did absolutely nothing. In Explorer, if you rename a file wrongly, you just press ctrl+z and and you get the original file name back. Move a file by mistake? press ctrl+z and the file is moved back to it's original location. Copy a file by accident? pressing ctrl+z deletes the extra copy. Delete the wrong file? ctrl+z to not only takes it out of the Bin, but also place it back where it was originally. 

At first I thought that maybe Nautilus just didn't have that particular hot key combination. "*No problem"* I thought to myself, *"I'll just do it from the menu option instead"* but when I checked, there was no Undo menu to be found anywhere. So basically it seems that your file management actions in Ubuntu are a one way street.

Perhaps there is a lack of any Undo option in Nautilus because providing a menu that allowed users to recover from catastrophic accidental actions might 'confuse' them too much. Better to have them just lose the data instead.

I could go on, but I'm even starting to bore myself now :tongue:

---

### Post by Surkow on 2007-04-17
> **oomingmak said:**
> There also needs to be the facility to work with folders in Save / Open dialogs (e.g to be able to Create them, Copy them, Move, Rename or Delete them and access their standard context menus and Properties just like you can in Windows Explorer).

I've said it before and I'll say it again, there is absolutely no reason whatsoever why File Open and Save As dialogs should not be exact replicas of the main file management window (but simply with a file filter applied to it, in order to exclude certain unwanted file types from being visible).
The things I proposed were meant for both folders and files. So I agree with the things you propose.

> However, my biggest pet hate with Nautilus is ..... totally ignoring the users click preference.

People keep going on about Gnome's HIG and their "consistency", but yet this is the most flagrant disregard for the user's preference and a serious impediment to providing a consistent user experience. Making me click one way to open "folder ABC" in Nautilus, but then forcing me to open the exact same folder a different way (still using Nautilus) just because it happens to be in an Open / Save window, is simply infuriating (not to mention problematic for people with RSI or mobility issues for whom double-clicking is a major difficulty).

To be honest, I don't know why any OS uses double-click as a default action. It's idiotic because it will never provide consistency across the interface (unless users are forced to start double-clicking on menus and on web links in order to match other double click actions). Seeing as that's never going to happen, then why not just standardise on one click, thereby making every object activate in exactly the same way?

Now I'm all for giving the user the choice of how they work, so if people want to engage in a bizarre mish-mash of single and double clicking then that is of course entirely up to them, but I resent such an ill-conceived method of activation being foisted on to me (and other people who prefer a more streamlined and intuitive approach to object activation).

Another major irritant with Nautilus is this: Even when you are allowed to use single click (e.g. in a main Nautilus window) this action STILL has not been implemented properly (in that you can't select any files because there is no 'mouse-over / hover selection' available). If you try to click the file in order to select it, then you end up launching it instead. So you have to hold down control or shift and then perform the click. All of that just to select a bleedin' file! I can't believe that choosing a setting specifically to reduce the number of redundant clicks that I have to make, results in me having to not only click an item to select it, but also having to use two hands to do it (one on the keyboard and one on the mouse).

Perhaps GNOME will add a footswitch as a 3rd requirement for file selection in the next release (seeing as they obviously hate to see limbs going unused)

In Windows Explorer, if I want to select a file, I just point to it. No click, no keyboard presses, no nothing. Just point ..... and job done.

If I want to make multiple selections in Explorer, then I can the use Ctrl or Shift keys and simply hover my mouse pointer over each file (no click necessary). However, if I do want to click, then I can do that as well (as the modifier key prevents the files from being launched). So either method can be used.

I find myself constantly pointing at files and folders on Ubuntu and then wondering why nothing is happening. And before anyone starts bleating on about 'Linux is not Windows' I'm talking about consistency within Ubuntu's own interface and I'm simply giving Explorer as an example of a much better implementation (which is quite an indictment, seeing as not only is Explorer coded by Microsoft, but it's pretty crap
I can understand the problems with Nautilus and the save dialog. But...the save dialog is not a part of Nautilus, but a part of GTK. So to be able to change the behavior the GTK save dialog needs to be altered or you should be able to choose which file manager handles the save dialog.

The other problems you are referring to are file manager specific. I have a problem with both Konqueror and Nautlius. I don't like the interface from Konqueror because it's very crowded. Nautilus on the other hand should be a simple file manager without internet browsing capabilities like Konqueror. But I feel it's too limited when doing standard file operations (most of which you already mentioned). After some searching on the web I found a small file manager called [pcman]("http://pcmanfm.sourceforge.net/") which has some added features compared to Nautlius (but no smb).

---

### Post by oomingmak on 2007-04-17
> **Surkow said:**
> The things I proposed were meant for both folders and files. So I agree with the things you propose.

I can understand the problems with Nautilus and the save dialog. But...the save dialog is not a part of Nautilus, but a part of GTK. So to be able to change the behavior the GTK save dialog needs to be altered or you should be able to choose which file manager handles the save dialog.

The other problems you are referring to are file manager specific. I have a problem with both Konqueror and Nautlius. I don't like the interface from Konqueror because it's very crowded. Nautilus on the other hand should be a simple file manager without internet browsing capabilities like Konqueror. But I feel it's too limited when doing standard file operations (most of which you already mentioned). After some searching on the web I found a small file manager called [pcman]("http://pcmanfm.sourceforge.net/") which has some added features compared to Nautlius (but no smb).
Yes, I share your feelings about Konqueror. I prefer a file manager to be just a file manager and nothing else. The problem with Nautilus is that many standard and essential features expected of a file manager are either very poorly implemented or missing altogether.

I am a total Linux newbie, so I have yet to get to grips with the underlying structure of Ubuntu (and Linux based distros in general). I was therefore unaware of issues such as Save dialogs not being part of Nautilus but rather being part of GTK. However, I am in total agreement with Tomasz Sterna on this matter (as discussed by him in **[[COLOR="DarkOrange"]this[/COLOR]]("http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00771.html")** thread that you previously linked to). To expect the user to forgo much needed functionality, simply because of the manner in which Save dialogs have been coded, is (in my opinion) user-hostile and unacceptable. Users should not have to learn the underlying structure and coding of an operating system just so that they can figure out what tasks can be carried out in one part of the operating system but yet not in another. 

File Open and Save As dialogs **_are_** file management, because that's exactly what you are doing; i.e. naming, locating, storing and arranging the files that you have created in a particular application. So the distinction between Nautilus and applications dialogs is a completely artificial one that's been created by the technical limitations of the underlying code and manner in which Gnome have chosen to implement it. To me this is about as acceptable as forcing users to use 8 letter file names because the filing system can't cope with any more that that. 

If a solution provided for a specific job is not up to the task, then that is a failing of the solution, not a failing of the user for being unaware of the particular technical limitations responsible for such a constraint. The system should be made to accommodate the user, not the other way round.

By people continuing to 'make allowances'  for the fact that the Save dialog and Nautilus proper are not the same thing, then this unnecessary and illogical separation of identical functionality is justified and encouraged to continue.

I imagine that were Ubuntu application dialogs implemented in the manner that Windows has done (i.e. using filtered views of a standard fully-functioning file manager) then this entire thread would be redundant, because you'd already have all of the extra functionality that you've proposed in your mock up.

In any event, I really liked your excellent mockup, and I hope that someone somewhere pays attention to it. But as I've said before, I won't be holding my breath.

---

### Post by Surkow on 2007-04-17
> **oomingmak said:**
> Yes, I share your feelings about Konqueror. I prefer a file manager to be just a file manager and nothing else. The problem with Nautilus is that many standard and essential features expected of a file manager are either very poorly implemented or missing altogether.

I am a total Linux newbie, so I have yet to get to grips with the underlying structure of Ubuntu (and Linux based distros in general). I was therefore unaware of issues such as Save dialogs not being part of Nautilus but rather being part of GTK. However, I am in total agreement with Tomasz Sterna on this matter (as discussed by him in **[[COLOR="DarkOrange"]this[/COLOR]]("http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00771.html")** thread that you previously linked to). To expect the user to forgo much needed functionality, simply because of the manner in which Save dialogs have been coded, is (in my opinion) user-hostile and unacceptable. Users should not have to learn the underlying structure and coding of an operating system just so that they can figure out what tasks can be carried out in one part of the operating system but yet not in another. 

File Open and Save As dialogs **_are_** file management, because that's exactly what you are doing; i.e. naming, locating, storing and arranging the files that you have created in a particular application. So the distinction between Nautilus and applications dialogs is a completely artificial one that's been created by the technical limitations of the underlying code and manner in which Gnome have chosen to implement it. To me this is about as acceptable as forcing users to use 8 letter file names because the filing system can't cope with any more that that. 

If a solution provided for a specific job is not up to the task, then that is a failing of the solution, not a failing of the user for being unaware of the particular technical limitations responsible for such a constraint. The system should be made to accommodate the user, not the other way round.

By people continuing to 'make allowances'  for the fact that the Save dialog and Nautilus proper are not the same thing, then this unnecessary and illogical separation of identical functionality is justified and encouraged to continue.

I imagine that were Ubuntu application dialogs implemented in the manner that Windows has done (i.e. using filtered views of a standard fully-functioning file manager) then this entire thread would be redundant, because you'd already have all of the extra functionality that you've proposed in your mock up.

In any event, I really liked your excellent mockup, and I hope that someone somewhere pays attention to it. But as I've said before, I won't be holding my breath.

I have been using Linux for some time next to Windows and I forced myself to learn to use certain programs. After a while I switched completely to Ubuntu and now I'm able to do things I couldn't do before.

A file manager is the main component of a GUI. Besides being simple it should be powerfull as well. The problem is that the developers think you need to be limited in your movements because the interface could become too crowded (what happened to Konqueror). But instead of making it easier...they made it more difficult for me to store and manage files with the save dialog. Today I got the advice to post a feature request in the Gnome mailing list about this problem because they are most likely to be able to work on a solution.

Compared to the GTK save dialog, the KDE save dialog works a lot better. It behaves more or less like a combination of the GTK save dialog and the Windows save dialog. There will be a new file manager called Dolphin for KDE (it won't replace Konqueror). See [this](http://enzosworld.gmxhome.de/screenshots.html) website for more information. It's just like Nautilus (without the browsing functionality) but with more powerfull features.

---

### Post by oomingmak on 2007-04-17
> **Surkow said:**
> I have been using Linux for some time next to Windows and I forced myself to learn to use certain programs. After a while I switched completely to Ubuntu and now I'm able to do things I couldn't do before.
I admire your bravery for making the switch. I'm just not at that point yet where I'm prepared to take such a huge step backwards in functionality, I'm just too dependent on my heavily customised Win2k unofficial SP5.1 setup (which I still use because I really dislike so many elements of XP).




> **Surkow said:**
> 
A file manager is the main component of a GUI. Besides being simple it should be powerfull as well. The problem is that the developers think you need to be limited in your movements because the interface could become too crowded (what happened to Konqueror). But instead of making it easier...they made it more difficult for me to store and manage files with the save dialog.
I absolutely agree with you. I spend more time in the File manager than I do anywhere else. The file manager almost **_is_** the operating system for me. The strange thing is that anyone who knows me will tell you that I've spent many years endlessly bitching about Windows Explorer. I couldn't believe that Microsoft would allow such a key piece of the OS to be so neglected and badly implemented. I could easily rattle off a list of deficiencies and problems with Windows Explorer longer than the one I've made here for Nautilus. So it's a shock to me (and very amusing to my friends) to hear me using Windows Explorer as a good example of how things should be done! To me that's an indication of just how terrible Nautilus (and most other Linux file managers) really are.




> **Surkow said:**
> 
Today I got the advice to post a feature request in the Gnome mailing list about this problem because they are most likely to be able to work on a solution.
Well if Gnome are prepared to listen (which I'm not sure they would be) then I think that promoting to them the idea stated at the end of your first post in this thread (namely; "*GTK needs to implement a function where the (simplified) file manager of your choice can be used instead of the standard save dialog*.") would be the best proposal to make. Futzing around with GTK dialogs may well be fine as an interim solution, but the more effort that is placed into creating additional functionality in the existing GTK method, the greater the reluctance will be to discard those efforts and re-do the job properly (as it should have been done in the first place). Anything else is just papering over the cracks.




> **Surkow said:**
> 
Compared to the GTK save dialog, the KDE save dialog works a lot better. It behaves more or less like a combination of the GTK save dialog and the Windows save dialog.
Yes, I noticed this when I tried out Kubuntu (in sheer desperation). But the additonal features it has in the dialogs are minimal (i think one or maybe 2 extra context menus, if my memory serves me correctly) but it was apparent to (me within seconds of using it) that it was also an entirely unsatisfactory solution.




> **Surkow said:**
> 
There will be a new file manager called Dolphin for KDE (it won't replace Konqueror). See [this](http://enzosworld.gmxhome.de/screenshots.html) website for more information. It's just like Nautilus (without the browsing functionality) but with more powerfull features.
Yep, been there, done that, tried the beta. I tested Dolphin some time ago (as I mentioned [[COLOR="DarkOrange"]**in a previous thread**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2408344&postcount=96") that I linked to) and basically I thought it was rubbish.

I also went through everything on this list (> [**[COLOR="DarkOrange"]Link[/COLOR]**]("http://www.linux.org/apps/all/System/File_Managers-1.html?sort=updated") <), and this one (>[**[COLOR="DarkOrange"]Link[/COLOR]**]("http://en.wikipedia.org/wiki/List_of_file_managers#For_Unix_variants")<) and didn't find anything remotely suitable for my needs. 

I did think that PC man was interesting, but the lack of SMB (as you pointed out) was also an issue for me. I find Nautilus' handling of network browsing bad enough as it is, so I wouldn't want to take a step backwards and have none at all.

---

### Post by oomingmak on 2007-04-17
[**[COLOR="DarkOrange"]X File Explorer[/COLOR]**]("http://www.icewalkers.com/scrshot/2845/") did catch my attention, but I've not yet tried it.

Now that you have explained to me that the File Manager and application Open / Save dialogs are not based on the same thing, I have somewhat less incentive to investigate file manager alternatives (as presumably this will in no way address the dialog problem).

Maybe I'll just have to wait and see what options are available after KDE 4 comes out.

---

### Post by oomingmak on 2007-04-18
I just found this thread in the new Gusty Gibbon development section:

[http://ubuntuforums.org/showthread.php?t=409817](http://ubuntuforums.org/showthread.php?t=409817)


:lolflag:

---

### Post by Surkow on 2007-04-18
> **oomingmak said:**
> I admire your bravery for making the switch. I'm just not at that point yet where I'm prepared to take such a huge step backwards in functionality, I'm just too dependent on my heavily customised Win2k unofficial SP5.1 setup (which I still use because I really dislike so many elements of XP).

[...]

I absolutely agree with you. I spend more time in the File manager than I do anywhere else. The file manager almost is the operating system for me. The strange thing is that anyone who knows me will tell you that I've spent many years endlessly bitching about Windows Explorer. I couldn't believe that Microsoft would allow such a key piece of the OS to be so neglected and badly implemented. I could easily rattle off a list of deficiencies and problems with Windows Explorer longer than the one I've made here for Nautilus. So it's a shock to me (and very amusing to my friends) to hear me using Windows Explorer as a good example of how things should be done! To me that's an indication of just how terrible Nautilus (and most other Linux file managers) really are.


Indeed...Windows Explorer does have badly implemented things. I don't really like the interface and when opening directories with around 10.000+ files it becomes very unstable. What exactly did you change from the behavior from the Windows Explorer? One thing that seems an interesting option from Nautilus is when renaming a file it only selects the filename and not the extention. But they should add an option to disable this behavior (since I don't like the behavior).

> Well if Gnome are prepared to listen (which I'm not sure they would be) then I think that promoting to them the idea stated at the end of your first post in this thread (namely; "GTK needs to implement a function where the (simplified) file manager of your choice can be used instead of the standard save dialog.") would be the best proposal to make. Futzing around with GTK dialogs may well be fine as an interim solution, but the more effort that is placed into creating additional functionality in the existing GTK method, the greater the reluctance will be to discard those efforts and re-do the job properly (as it should have been done in the first place). Anything else is just papering over the cracks.
When they implement such a thing, GTK (the toolkit) needs to be modified. I wonder how old applications could be able to use a file manager since they are linked with the old GTK save dialog. For example a program called XSane. This program is a fantastic program for scanning. But when I try to save anything it directly asks for a very old save dialog instead of the most updated version from GTK.

> **oomingmak said:**
> I just found this thread in the new Gusty Gibbon development section:

[http://ubuntuforums.org/showthread.php?t=409817](http://ubuntuforums.org/showthread.php?t=409817)


:lolflag:
I have exactly the same problem with the trash. When I accidentally throw something away I want to be able to restore it. In Feisty the trash has been improved a little.

---

### Post by oomingmak on 2007-04-18
Well, the developers (who ever they are) are now apparently quite keen to elicit user feedback for the next version of Ubuntu (as stated in the Gusty Gibbon section of these forums). So maybe you should submit your suggestion about having a function where the user's file manager of choice is used instead of the standard application file dialogs.

You'd have to follow the correct [IDEA] submission procedure (as outlined in the sticky thread) in order to make sure that your thread does not get locked by the mods, but it's got to be worth a shot, seeing as they are actively seeking user suggestions for new features and improvements of existing ones. 

Such a contribution would not be that much different to what you've done in this thread already, and you'd be able to provide screenshots (unlike most of the other [IDEA] suggestions in the Gusty feature thread).

:D 

P.S. Have you ever tried X File Explorer?

---

### Post by Surkow on 2007-04-19
> **oomingmak said:**
> Well, the developers (who ever they are) are now apparently quite keen to elicit user feedback for the next version of Ubuntu (as stated in the Gusty Gibbon section of these forums). So maybe you should submit your suggestion about having a function where the user's file manager of choice is used instead of the standard application file dialogs.

You'd have to follow the correct [IDEA] submission procedure (as outlined in the sticky thread) in order to make sure that your thread does not get locked by the mods, but it's got to be worth a shot, seeing as they are actively seeking user suggestions for new features and improvements of existing ones. 

Such a contribution would not be that much different to what you've done in this thread already, and you'd be able to provide screenshots (unlike most of the other [IDEA] suggestions in the Gusty feature thread).

:D 

I finally created an [IDEA] submission about the save dialog problems. But suddenly I can't add or change any tags.

[http://ubuntuforums.org/showthread.php?t=413457](http://ubuntuforums.org/showthread.php?t=413457)

> P.S. Have you ever tried X File Explorer?
I didn't have time to test it. But some of my friends were able to test it and don't recommend it. It does't really fit in the Ubuntu interface and has trouble with loading large directories.

---

### Post by Horizon on 2007-04-24
> **Surkow said:**
> Indeed...Windows Explorer does have badly implemented things. I don't really like the interface and when opening directories with around 10.000+ files it becomes very unstable. What exactly did you change from the behavior from the Windows Explorer? One thing that seems an interesting option from Nautilus is when renaming a file it only selects the filename and not the extention. But they should add an option to disable this behavior (since I don't like the behavior).
I don't know if you already do this, but when selecting rename with the mouse a quick hit to ctrl+a with your left hand takes literally no extra time and from there you can simply type and it'll replace the whole thing. When you think about how often you don't actually want to change the file extension that extra .5 of a second in the off chance you do I think this is a universally good setting. Could you provide some insight into why you do not like this behaviour?

---

### Post by Jhongy on 2007-04-24
Following on form this, is there any way to allow renaming by simply clicking on the name? I miss this functionality, and right-clicking-slecting from-a-menu is cumbersome.

---

### Post by Horizon on 2007-04-24
> **Jhongy said:**
> Following on form this, is there any way to allow renaming by simply clicking on the name? I miss this functionality, and right-clicking-slecting from-a-menu is cumbersome.
It's F2. F2 taking just as long to press as right-click>rename :P

---

### Post by oomingmak on 2007-04-27
> **Horizon said:**
> It's F2. F2 taking just as long to press and right-click>rename :P
I'm surprised that they chose F2 as they key for 'Rename' seeing as that is the same key that is used for rename on Windows.

---

### Post by NTolerance on 2007-04-27
Another problem is that you can't show hidden folders in the dialog.  Whenever I download a configuration file I always have to use the 2-step process of saving to a temp directory and then moving to a hidden directory.

---

### Post by oomingmak on 2007-04-27
I just read the [**[COLOR="DarkOrange"]Gnome HIG[/COLOR]**]("http://developer.gnome.org/projects/gup/hig/2.0/"). 

I haven't laughed so much in a long time.

:lolflag:

---

### Post by Horizon on 2007-04-27
> **oomingmak said:**
> I just read the [**[COLOR="DarkOrange"]Gnome HIG[/COLOR]**]("http://developer.gnome.org/projects/gup/hig/2.0/"). 

I haven't laughed so much in a long time.

:lolflag:

The Gnome HIG is actually very good. Some good points to take in. I've pointed a few interface design/graphics design friends/acquaintances there myself. All said it was a pretty good guideline. Of course it's just a guideline, so how to follow them and when they apply as common sense would indicate depends on your specific situation.

Maybe you didn't read it properly/all of it.

---

### Post by oomingmak on 2007-04-27
> **Horizon said:**
> Maybe you didn't read it properly/all of it.
And maybe you didn't read this thread from the beginning, otherwise you'd understand why I was laughing.

I **have** read the HIG properly, but I'm not sure that the same can be said of Gnome themselves (even though they wrote it). 

Gnome seem totally incapable of following *their own* guidelines (that's what I found so funny).  Almost every single thing that I was saying I feel is wrong with Nautilus (earlier in this thread), has turned out to be a flagrant breach of Gnome's own guidelines according to their HIG.

---

### Post by oomingmak on 2007-04-28
> **Surkow said:**
> One thing that seems an interesting option from Nautilus is when renaming a file it only selects the filename and not the extention. But they should add an option to disable this behavior (since I don't like the behavior).
Actually, that is one of the very few (if not the only) things that I think Nautilus does properly (and better than Windows Explorer).

I'm still not quite acclimatised to it yet, but that's only because I'm used to Explorer's way of doing it. 

In my view, the Nautilus way (i.e. _not_ automatically selecting the file extension) makes far more sense, and I consider it to be a good design decision. 

However, given that Gnome have thrown everything else into gconf, then I don't see why they couldn't have included this as an option as well (for people like yourself who don't like it).

---

### Post by yabbadabbadont on 2007-04-28
> **oomingmak said:**
> Actually, that is one of the very few (if not the only) things that I think Nautilus does properly (and better than Windows Explorer).

I'm still not quite acclimatised to it yet, but that's only because I'm used to Explorer's way of doing it. 

In my view, the Nautilus way (i.e. _not_ automatically selecting the file extension) makes far more sense, and I consider it to be a good design decision. 

However, given that Gnome have thrown everything else into gconf, then I don't see why they couldn't have included this as an option as well (for people like yourself who don't like it).

Actually, since with native Unix and Linux filesystems, there really isn't any such thing as a file extension (except by common usage), Nautilus should probably do it the way that Exporer does.  Explorer clearly gets it wrong, since extensions are a part of the filesystem in Windows (at least they used to be), but so does Nautilus for the opposite reason.  :)

---

### Post by oomingmak on 2007-04-28
> **yabbadabbadont said:**
> Actually, since with native Unix and Linux filesystems, there really isn't any such thing as a file extension (except by common usage), Nautilus should probably do it the way that Exporer does.  Explorer clearly gets it wrong, since extensions are a part of the filesystem in Windows (at least they used to be), but so does Nautilus for the opposite reason.  :)
Yes, you make a very good point.

Changing extensions in Linux has nothing like the effect that it has in Windows. So it does make you wonder why this particular file-naming features was implemented in this way for Linux but not in Windows.

:-k

Reminds of the fact that here in the UK, our "post" gets sent by "Royal Mail" while in the US their "mail" gets sent by the "US Postal Service". 

Never did understand why that was - lol.

---

### Post by elf@whoever.com on 2007-05-01
> **oomingmak said:**
> Dare I even mention Nautilus' Alzheimer like approach to window placement and column sizing?

I've spent time sizing a window and setting the column widths to just how I wanted it. I closed the window and then immediately re-opened it only to find that all of the adjustments that I'd made had been scrapped, and the window had returned to a default position. I have not experienced this kind of errant application behaviour since the days of Windows 98.

Just found this thread today, and Yes that is a MAJOR annoyance to many users that I know as well as myself. A fellow in a user-group IRL suggested, "Don't use Nautilus. Use Thunar" Not as functional in some ways, but if you tell it to do something with the columns, Thunar does not change back 1 second after you close the window. Only annoying thing that I have run into so far was the min/max window size thing: always seems to default to minimized. Other then that, unless I see a compelling reason to switch back, I am happy with what I have now.

---

### Post by oomingmak on 2007-05-20
> **elf@whoever.com said:**
> Just found this thread today, and Yes that is a MAJOR annoyance to many users that I know as well as myself. A fellow in a user-group IRL suggested, "Don't use Nautilus. Use Thunar" Not as functional in some ways, but if you tell it to do something with the columns, Thunar does not change back 1 second after you close the window.
I've tried Thunar and it does show considerably more promise than Nautilus, but it is still in the very early stages of development and lacking many features, so it's not what I would consider 'usable'. 

However, at least Thunar devs have a clue about how to implement single-click properly. The same can not be said for whoever worked on Nautilus.

---

### Post by davescafe on 2007-07-03
Oomingmak, I appreciate your input on this thread. You have articulated many problems that have been bothering me in Nautilus and with GTK+ over the past year. The way it is currently implemented, Nautilus and GTK+ seem to be designed for novice and part-time Linux desktop users who only deal with a small number of files. There is no reason (that I am aware of) why Nautilus and the underpinning GTK+ couldn't be enhanced to support power users while still being friendly and simple for the newbies.

I strongly agree with the idea posted earlier in this thread, that the "Open" and "Save" dialogs should have all the functionality of Nautilus, and not be restricted from renaming files, etc. This is something that is a common annoyance for me.

Perhaps more annoying is the inability of Nautilus and "Open" and "Save" dialogs to remember custom sizing, etc. Every day I open and save a lot of documents using OpenOffice.org, which means that every day, I have to struggle with the tiny, non-customizable "Save" window provided by OpenOffice.org via GTK+. I am aware that I can switch the dialogs for native OO.o versions, but these are fraught with their own problems.

These are both things that Windows Explorer does well, and Gnome would do well to emulate. I am not suggesting that Gnome try to emulate Windows, merely that Gnome adopt features that will help power users by solving some of the problems that are already solved in Windows Explorer.

---

### Post by oomingmak on 2007-07-03
Hi davescafe, thank you for the positive comments that you made regarding my personal take on the limitations and annoyances in Nautilus and in GTK dialogs. :)  

I could have gone on to describe many more Nautilus / GTK problems (and breaches of their own HIG), but there was really no point, because even if I had gone to the trouble of  formally submitting them as bugs or enhancement requests, they would either be ignored or just get dismissed. If even  [**a bounty and significant community support**]("http://ubuntuforums.org/showthread.php?t=409817") can't get the most basic features developed, then there is not much hope for anything else submitted by a single user as a bug. 

As I mentioned earlier in this thread, I thought the problems with Nautilus were not insurmountable, but I had assumed that the reason why they weren't getting fixed was because of difficulties related to coding the necessary changes. However, I soon learned that it's not programming difficulty that is necessarily the problem, but rather the attitude and mindset of the developers (and some of the people who support them). Many people just don't see the need to "fix" these issues, because as far as they're concerned they are not a problem. They claim that things are fine just as they are, and that it is disrespectful to say otherwise.

I was absolutely stunned to see some of the dev comments on their bug / enhancement reporting site, as they clearly showed a total ignorance about even the most basic UI concepts (such as object persistence, consistent interaction / usage methods and user forgiveness). I am nothing at all to do with UI development (other than just having an interest in it) and I am certainly no programmer, but even I am familiar with such concepts and how they impact upon read world usage. I therefore find it strange that people who have such little understanding about usability and UI design are none the less contributing to very high profile projects which impact upon so many users.

I have now resigned myself to the fact that nothing much is going to change, because among certain key figures there seems to be a culture of "the user is always wrong". A classic example is when you hear devs say things like 'a File dialog is not for managing files', or 'a window manager is not meant to manage window positions'. What they are saying is undoubtedly true (at least in the particular implementation that they are describing) but the adverse effects on the end user are still present for all to see (not that such things matter when dogma is the order of the day).

The single-click anomaly in Nautilus was reported 4 years ago and it still hasn't been fixed (and that's despite the change having already been coded and ready to go) so I find it hard to be enthusiastic or optimistic about any of these issues being addressed.

[**http://ubuntuforums.org/showthread.php?t=465866**]("http://ubuntuforums.org/showthread.php?t=465866")

I am currently keeping an eye on Thunar, as they seem more promising (particularly due to their Thunar Extensions Framework). I'll have to see what they come up with for v 1.0 when it's released in August. I just hope that they have managed to put in Network support by then. In the mean time, all I can say is thank goodness for Windows.

---

### Post by Horizon on 2007-07-03
> **oomingmak said:**
> 
I could have gone on to describe many more Nautilus / GTK problems (and breaches of their own HIG), but there was really no point, because even if I had gone to the trouble of  formally submitting them as bugs or enhancement requests, they would either be ignored or just get dismissed. If even  [**a bounty and significant community support**]("http://ubuntuforums.org/showthread.php?t=409817") can't get the most basic features developed, then there is not much hope for anything else submitted by a single user as a bug. 
At the end of the day this is their project and they can do whatever the hell they want. You're not a customer and they don't owe you anything. If there's something you don't like about their project and they don't agree then fork...or make your own. Make a patch even, or find (or pay) someone to make one for you. Frankly all this attempted browbeating is just misdirected and a waste of time.

If indeed they do breach their own HIG I'm pretty sure they would be interested in the bug being filed. You can't berate people for things they haven't done but you "think they would do". FIle a bug; they'll either accept it or give you a reason why they deviated. If you don't like the reason or they don't agree with your assesment then that's a completely different issue, and it's dishonest of you to disregard the reason and present something as fact without also fully representing the reason they gave.

It's also dishonest to take a bunch of issues with their own specific issues and reasons and bundle them into a single percieved problem, disregarding the individual reasons given because you don't agree with them and then presenting this as some kind of bigger issue.

Frankly when I read all this "Gnome don't listen" talk all I see is a bunch of people saying "they don't agree with me". They don't? well it's their project, so when there's a disagreement who do you think they'll go with? big deal. Fork and make your own project, then everything will go by your will regardless of any technical or quality issues the Gnome devs may or may not see.

Infact, if you really wanted an answer to your rhetoric you would be discussing this someplace specifically gnome related instead of somewhere where it's easier to get incomplete answers to further your rhetoric.

---

### Post by janberk on 2007-09-27
Well, I also had many problems with Ubuntu file management. I used to use Total Commander in windows, and I was looking for something similar in Linux, I used Konquerer for a while but it had the bug in Ubuntu not sending the files to Trash when deleting, but delete forever. So I tried many other double pane managers, but none satisfied me at all. I couldn't find a double pane manager that has "tabbed file exploring", which I think is very useful.

Anyway at the end I decided that I should use Nautilus just like any other Ubuntu user, it was hard to get use at first. But now I find its "button based location bar" innovative. 

The only think that frustrates me is the Save As dialog.

In conclusion, I think Ubuntu is a great OS and don't get frustrated with some little inconvenience :). 

Cheers,
Janberk

---

### Post by yabbadabbadont on 2007-09-27
> **janberk said:**
> Well, I also had many problems with Ubuntu file management. I used to use Total Commander in windows, and I was looking for something similar in Linux, I used Konquerer for a while but it had the bug in Ubuntu not sending the files to Trash when deleting, but delete forever. So I tried many other double pane managers, but none satisfied me at all. I couldn't find a double pane manager that has "tabbed file exploring", which I think is very useful.

Anyway at the end I decided that I should use Nautilus just like any other Ubuntu user, it was hard to get use at first. But now I find its "button based location bar" innovative. 

The only think that frustrates me is the Save As dialog.

In conclusion, I think Ubuntu is a great OS and don't get frustrated with some little inconvenience :). 

Cheers,
Janberk
Did you ever try pcmanfm?

---

### Post by oomingmak on 2007-09-28
> **janberk said:**
> The only think that frustrates me is the Save As dialog.

In conclusion, I think Ubuntu is a great OS and don't get frustrated with some little inconvenience
I wish I could say the same.

Unfortunately for me, file management is such a fundamental part of how I work on any OS, that I can not overlook such significant (not to mention numerous) shortcomings.

---

