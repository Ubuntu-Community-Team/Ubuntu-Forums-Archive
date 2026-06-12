---
title: "Metacity and Compiz both have trouble with vertical monitors"
date: 2011-08-01
forum: Desktop Environments
---

### Post by skimtneer on 2011-08-01
I have three 24" widescreen digital LCD monitors, each 1920x1200.  I have been running all three in portrait orientation (vertical) standing next to each other to make one big desktop at 3600x1920.

BRIEF SUMMARY:

Neither Metacity nor Compiz are fully able to deal with this configuration.  Under Metacity I get subpixel font smoothing problems.  Under Compiz I get fairly severe display freak-outs, window corruption and mislocation.

FULL DETAILS in following posts.  This was way too long in a single post.  Read any of the following if the headings are of interest, and if not, I'm sorry for filling your screen :)

---

### Post by skimtneer on 2011-08-01
[B]Subpixel font smoothing problem on Metacity
[/B]
On Ubuntu/Gnome Classic (No Effects)... so Metacity is the window  manager... there is trouble with subpixel smoothing.  Under any choice  of subpixel smoothing and hinting type, all browsers and text windows of  any sort show random corruption of characters.  The appearance of the  bad characters is almost correct, but they get shrunk or 'wrinkled'  horizontally by a sub-pixel amount, almost as if one vertical line of  pixels were missing from a character so it is horizontally narrower --  but not by an entire column of pixels.  For example, take the lower case  letter 'd' and render it so that its vertical line is half as thick.

The subpixel smoothing problem comes and goes a little bit... often  seems to be not occurring at all when I first log in but it's always  there again within a few minutes and lasts the full length of any  session.  I have two different brands/models of monitor and two  different video cards (though they are both ATI Radeon HD 4XXX series,  both quite capable of running two monitors at this resolution).

This problem does not appear at all if I run my monitors in  landscape/horizontal orientation.  But I really want to use three  vertically next to each other.  The resulting spanned desktop is a  perfect size, and it lets me use all of the monitors I have without  crowding my physical desk too far in width.

This subpixel smoothing problem under Metacity also seems to be not  completely deterministic, or something.  Highlighting or scrolling any  affected text fixes that text, for the moment, but as soon as new window  contents are drawn, completely different characters are usually showing  the rendering problem.  This includes not only new window contents.  If  new text scrolls into view, old window contents above sometimes is  redrawn with these weird subpixel 'wrinkles' in it again.

The problem shows up worse in some apps than others, perhaps due to CSS  or other window styling, I don't know.  On many common web pages -- any  Google app including Gmail is a major example, as is Facebook -- the  problem is so widespread that the entire window contents appears to  ripple or wiggle when certain things are done, like mousing over or  highlighting certain text.  At worst, sometimes I discover situations  where I'm entering text into a box and every newly entered character  causes the entire contents of a window to wiggle back and forth by  subpixel amounts as long as I continue entering text.  Also in Firefox  or Chromium, mousing over the bookmarks toolbar or parts of other  toolbars causes a tiny bump in window layout which forces the entire  window contents to re-render (at least to re-render all text) which will  bring back 'wrinkles' in characters that formerly had been forced to  render properly by either scrolling or highlighting an area.

Sometimes the wiggles, the jumps between characters being rendered  incorrectly and rendered correctly, will even happen semi-spontaneously.   Just now, a lower case 'o' character in the paragraph above was  unnaturally narrow, horizontally squished, and I barely bumped the mouse  (no clicks, no keyboard action) and the text changed back to correct  rendering.

I'm sorry for so much detail here -- I hope that for anyone reading this  who is actually expert enough to possibly diagnose the source of the  problem, this amount of detail will actually be wished for.

So the Metacity problem is annoying, but I can live with it compared to the others.  On to the Compiz alternative.

---

### Post by skimtneer on 2011-08-01
**Display freak-out, window content corruption, and loss of window locations under Compiz:**

If I log in using Gnome Classic (but not the "No Effects" alternative)  so that Compiz is the window manager instead of Metacity: great, no  subpixel font rendering problems at all!  But there is a much worse  problem.  Compiz ** freaks out ** when I grab and move any window.  It  gets somewhat weird when I move a window my a small amount within one  monitor, but as soon as I move it across monitor boundaries and onto  another monitor, it starts to lose track of window position.  Sometimes  the place it thinks I am grabbing the window is no longer accurate, and  it will have my mouse click/drag grab a window when my mouse pointer was  not even inside of that window's title bar.  Sometimes it will respond  with resizing when I clearly made the motions to move, not resize.

This problem is even worse if I move a window across not just one  monitor boundary, but onto a second monitor and continue on to a third  monitor.  At that point Compiz totally loses itself and the entire  display flickers and gets redrawn.  When that is finished, some windows  are no longer in their former locations.  What's more, the window I was  attempting to drag is no longer located the same relative to my mouse  pointer AND it now has a weird "double" of itself appearing on the wrong  monitor.  The double is like some kind of place holder that has no  content -- only a rectangle of missing background.  This is true  regardless of whether i set a background image or "no background" (just  solid black, which I usually do).

I should add that I was already avoiding Compiz on this workstation even  before I tried putting the monitors in portrait/vertical orientation.   In that configuration, with monitors set horizontal/landscape, it did  not have a problem with window dragging, but it had a very similar  "freak out" every hour or two, where spontaneously the entire desktop  would flicker and get completely redrawn, with window locations changed  and sometimes window contents corrupted or even set to the wrong  resolution, even though my monitor and desktop resolution never changed.   Everything would redraw correctly if I grabbed each window and  manually resized and placed it where I wanted it.  But the occasional  freak-outs were really annoying.  So no Compiz for now.

But I do wish I could either use Compiz without problems, or find a way  to get Metacity to render subpixel font smoothing correctly.  If I turn  off subpixel smoothing entirely the problem is of course gone -- but you  know how poor (and bad for eyes) text is on LCD monitors without  smoothing.  The problem is slightly better if I enable subpixel  smoothing but set hinting to "None", but the problem is still there,  just a bit less severe.

---

### Post by skimtneer on 2011-08-01
**Unity problems, Conclusion, and multiple unsatisfactory alternatives:**

Finally, I'll describe how I have been unable to use Unity at all with  portrait/vertically oriented monitors.  When I try to log in with a  regular Ubuntu (Compiz+Unity) session, I not only have the Compiz  problems as described above, but Unity fails to show up at all -- I get  no application bar and no toolbar at the top of the primary (or any)  monitor.  So there is no icon for settings, nothing.  Only empty  desktop.  The system runs, I am able to open a terminal and cause  various gnome programs to run graphically, etc.  But there's just no  Unity visible.

Last but not least, here's more system data.  I mentioned this is using  the DVI ports of two ATI Radeon HD 4XXX cards.  I believe one is a 4870  and one a 4650 or 4670.  Again all of this works flawlessly with  landscape orientation so I don't believe it's really the cards or the  monitors.  Furthermore, under Windows 7 a single desktop spanning all  three of these monitors in portrait orientation works flawlessly, so  again I know it's not the hardware.  I recently updated to AMD's  catalyst 11.7 drivers (yes, this is the proprietary 'fglrx' driver) but  the problem also existed on the previous 11.6.  Users have suggested  that I try running without the proprietary driver, but in that case as  far as I know I can only cause the desktop to span two monitors, not  three (because it is across two video cards once it's three monitors; I  only have 2 DVI outs per card).  So as far as I can tell I must use the  'fglrx' proprietary driver and enable Xinerama in order to get the  3-across desktop I want.

It has also been suggested that Xinerama is not so great and that I  should just figure out how to set this up with XRandR.  But from what I  can tell so far, Xinerama and/or AMD's Catalyst Control Center are  merely providing a front end to randr?  I could stand to learn a lot  about that but have not been very successful searching and finding any  docs I could easily comprehend as far as getting what I want without a  very involved process of manual edits and experimentation.

To anyone who read this far, thank you for enduring this long post.

In conclusion, I seem to find myself forced to choose between several unsavory alternatives:
* Go back to Windows where this all works fine (but I strongly dislike that OS and won't go back for many many reasons).
* Give up and just ignore the character and window-contents wiggling  under Metacity... accept that when my monitors are rotated to portrait  mode, this window manager drives my monitors in a manner that makes them  look almost as bad as analog or even CRTs with a bad pixel timer.
* Compiz: so far not even a possibility, if it's totally unstable.  I  thought it was the latest greatest window manager -- but maybe no one  has taught it everything it needs to know about rotated monitors  combined with desktop spanning yet?
* Give up my vertical monitors... I would have to sell or just stop  using one of them because only two fit on the desk when they are  horizontal.
* Or, make a wall or desk stand so that I can stack them vertically in  landscape mode, but that's not so great (weird aspect ratio and poor  viewing angles).

---

