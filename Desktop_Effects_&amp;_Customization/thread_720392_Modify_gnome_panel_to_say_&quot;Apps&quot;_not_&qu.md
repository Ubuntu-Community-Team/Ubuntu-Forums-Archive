---
title: "Modify gnome panel to say &quot;Apps&quot; not &quot;Applications&quot;??"
date: 2008-03-10
forum: Desktop Effects &amp; Customization
---

### Post by quixote on 2008-03-10
I'd like more space for launcher buttons and the window buttons in the panel.  I don't need all that space taken up to say "Applications"!  I just want to shorten that to "Apps".  "System" to "Sys".

WHERE CAN I DO THAT?  I've been trying to figure this out literally for years.  I'll poke around for a couple of days, get nowhere, and give up.  Where does gnome hide this?  A reply to an earlier thread ([http://ubuntuforums.org/showthread.php?t=251180](http://ubuntuforums.org/showthread.php?t=251180)) suggested trying gconf-editor.  But that just lists all settings as depending on "schema", and anyway, there's no obvious list saying: panel: Applications, Places, System, and so on.

How can I tweak this one stupid little thing?  :confused:

---

### Post by bcl1713 on 2008-03-10
bump

---

### Post by Sugi on 2008-03-10
This may help, but it's not quite what you want.  Try:
Right on Click Panel
Add to Panel
Scoll down to Utilities
Main Menu
Add

I used that Icons instead of the Menu Bar for the same reason, I wanted more room and that it looks cleaner.

Hope this helps,
Sugi

---

### Post by quixote on 2008-03-10
Sorry to be dense about this, Sugi, but I'm not sure I understand what you're saying.  

The method you list gets me an ubuntu logo with a menu that expands up from that.  So far, so good.  But that doesn't change the way my current default panel has long words in it.

Is this the idea?  Make a new panel, that has the Ubuntu logo - expandable menu, and that I can then put my various launchers on.  Then delete the default panel that I'm unhappy with?

I must admit, I never thought of that.  Seems like a real "duh!" idea, now that you mention it. :oops: :)

---

### Post by Sugi on 2008-03-10
Sorry about that, I didn't explain myself.  The menu will be only one icon on the panel, but it won't change the names of "Appilcations" "Place" "System" but it will be in one drop down menu.  So, you have more space on your panel for launchers.  Hope this helps a little.

Sugi

---

### Post by Sugi on 2008-03-10
But on the other hand, I would also love to know how to edit this options within the Menu bar ("Applications" "Places" "System").  So, if anyone else knows this, please let us know.


Sugi

---

### Post by LeoSolaris on 2008-03-10
Since he already pointed it out, I will not give ya the same advice, I'll just drop in to say that I tend to like the button over the default bar. For a panel that I can slide off the edge of the screen, the little button ends up making it about the same size as my awn-dock, so it has a nice symmetry. I tend to go for the 'clean' look, just because I don't like clutter in my work area. The little Gnome foot is the Menu icon, it changed with the icon set I installed a little while back.


[IMG]http://i97.photobucket.com/albums/l232/Leo_Solaris/Screenshot.png[/IMG]

Leo

---

### Post by quixote on 2008-03-10
Leo!  Don't leave us hanging like this!  Who already said it?  Said what?  You obviously know how to do this, but I still don't get it.  How did you get that gorgeous effect?  What did you do?  I mean, like, <i>exactly</i>?  The answer may be staring me in the face here somewhere, but I'm not getting it.

---

### Post by Sugi on 2008-03-10
quixote, well, if you want to change the Logo of the menu.  That part is easy

Terminal
$ gksudo nautilus
 (opens up the GUI folder manager with the power of the super user)
 -than search for /usr/share/icons/human/22x22/places
(or any size IE 24x24 32x32, depending on what size your panel is.  default is 22x22)
 -make your own custom start menu, label it "start-here.png".
 -BACK UP /usr/share/icons/Human/22x22/places/
Somewhere else
(back up whatever size folder you are tweaking)
 - click and drag the "start-here.ong to the location and press ok for replacing the ico

Now, add a new button to your panel
Right Click on Panel
Add to Panel
Scoll down to Utilities
Main Menu
Add

Bam, new log for your start menu.  Everything ask LeoSolaris. :)

chips24's Theme setup for ubuntu (he changed his start menu to a windows 95 theme,
[http://ubuntuforums.org/attachment.php?attachmentid=61613&d=1204687526]("http://ubuntuforums.org/attachment.php?attachmentid=61613&d=1204687526")

Sugi

---

### Post by quixote on 2008-03-10
There's no place like the ubuntu forums.  I'm learning all sorts of stuff I haven't found out in all the time I've been banging my head against this.

But, my real question isn't really about altering the logo icon.  It's still: how can I create one panel at the bottom without long words in it? :)

---

### Post by quixote on 2008-03-10
Okay, I finally had a chance to try Sugi's(and probably Leo's :) ) solution about making a new panel and deleting the default.

It works, and it's just what I wanted.

You folks are the best!  Thank you, Thank you!

---

### Post by Sugi on 2008-03-10
:)  Well, don't leave us in the dust.  Take a screenshot of your panel buttom that you custom made and attach it here.

Sugi

---

### Post by bcl1713 on 2008-03-10
Just an aside.. > 5 pc setup. all, but one isn't linux. ^.^ shouldn't that read "all but one IS linux" otherwise you are saying none are linux but one....

---

### Post by quixote on 2008-03-10
I didn't actually make a custom icon.  I like the ubuntu icon just fine.  All the little icons are off in the lower left now.  I have an oldish, weakish laptop, so I try to keep the fancy graphics to a minimum.  The thing I actually like the most about my desktop is the background: pictures from the [Astronomy Picture of the Day]("http://antwrp.gsfc.nasa.gov/apod/astropix.html") archive.

---

### Post by CarpKing on 2008-03-11
For future reference, you wouldn't have had to make a new panel.  After you add the single-icon menu to the original panel, simply right click on the "Applications Places System" area and go to "Remove From Panel."  Then you can click an empty area of the panel and drag it to whichever screen edge you want.

---

### Post by quixote on 2008-03-11
Oh.  

That's another dead simple idea that never occurred to me in all the time I've been trying to deal with this. :oops:  Thanks for the tip!

(It reminds me of the High and Far Off Times, after I'd been using Unix and DOS for a few years, and had to run something on one of them new, whizzy Macs.  I couldn't figure out how to open a file!  "Oh.  You * click* it?")

---

### Post by Sugi on 2008-03-20
bcl1713,
Thanks for the English correction. :)

Sugi

---

