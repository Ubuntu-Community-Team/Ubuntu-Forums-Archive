---
title: "&quot;Squished&quot; Pages in Acrobat Reader"
date: 2006-01-12
forum: General Help
---

### Post by gmcauley on 2006-01-12
When I open a pdf in Acrobat 7 (stand-alone or Firefox plugin) the aspect ratio of the pages is wrong: it is squished short and stretched wide.  It prints correctly, and when I use the 'snapshot' tool and copy-and-paste a section into  OO Writer, it pastes with the correct ratio.  So, only the display seems to be wrong.

Any ideas?:confused:

---

### Post by az on 2006-01-12
[QUOTE=gmcauley]When I open a pdf in Acrobat 7 (stand-alone or Firefox plugin) the aspect ratio of the pages is wrong: it is squished short and stretched wide.  It prints correctly, and when I use the 'snapshot' tool and copy-and-paste a section into  OO Writer, it pastes with the correct ratio.  So, only the display seems to be wrong.

Any ideas?:confused:[/QUOTE]
Does it render properly in the native linux pdf viewers?

---

### Post by gmcauley on 2006-01-12
Thank you for your reply.

In KPDF it displays fine.

---

### Post by az on 2006-01-12
Does Adobe accept bug reports for their unix version?

---

### Post by gmcauley on 2006-01-12
Yes, [http://www.adobe.com/misc/bugreport.html](http://www.adobe.com/misc/bugreport.html) (I just submitted one).

Has any one else seen this?

---

### Post by johanseland on 2006-05-10
[QUOTE=gmcauley]Yes, [http://www.adobe.com/misc/bugreport.html](http://www.adobe.com/misc/bugreport.html) (I just submitted one).

Has any one else seen this?[/QUOTE]

I got this problem after a fresh install of Dapper Beta 2. 
Wierd. Did you get any respone to your bugreport?

---

### Post by gmcauley on 2006-05-10
[QUOTE=johanseland]I got this problem after a fresh install of Dapper Beta 2. 
Wierd. Did you get any respone to your bugreport?[/QUOTE]

If I remember right, when I submitted the bug the web site said that they do not  respond to the reports.

B/c of lack of time, I have just been 'living with it' (using another computer on my desk for reading PDFs).

Do you see the same problem in other PDF viewers (eg, KPDF) like I do?

---

### Post by mkenigson on 2006-05-25
I use debian and I'm having the same issue.  PDFs display just fine in the standalone Acrobat Reader, but in the firefox plugin they're squished.

---

### Post by mkenigson on 2006-05-25
Okay.  I fixed it.  Here's how, along with how if figured it out:

First, I found this in /usr/share/doc/acroread-plugin/README.gz:

Stretching/Skewing of Page Text on some systems
You may face some stretching/skewing effect on the page display on certain
systems.  This problem can be resolved by going to Edit > Preference > Page
Display tab, and setting the "Custom Resolution" to the currently displayed
System setting.

So I changed the default behavior to open pdfs with acroread rather than use the plugin (so I could access the menus) and clicked on the pdf link I'd been having trouble with.  I discovered that it was set to use the system default, which in my case seemed to be 181 pixes/inch!  I changed it to use 72 px/in.  It worked great.  In the course of doing this, I discovered that on my box, the prefs file is found in ~/.adobe/Acrobat/7.0/Preferences/reader_prefs.  I had copied the original reader_prefs file so I could see what it changed and found it changed this section:

/Originals [/c <<       /DefaultSplitterPos [/i 150]
        /ProofingSpace [/s (U.S. Web Coated \(SWOP\) v2)]
>>]

to this:

/Originals [/c <<       /DefaultSplitterPos [/i 150]
        /DefaultZoomScale [/i 0]
        /ProofingSpace [/s (U.S. Web Coated \(SWOP\) v2)]
        /UseSysSetting [/b false]
>>]

I also discovered that if I changed the pixels per inch setting to anything other than 72, it added this:

        /PixelsPerInch [/i 70]

in between DefaultZoomScale and ProofingSpace (where 70 is the setting I put in).  After all the tests I did, I ended up going ahead and adding it in with 72 pixels, just in case, but you may not need that.  It seems to me the most important thing is the having the UseSysSetting value set to false.

I then changed it back to use the plugin and, alas, the display was still squished, so I restarted firefox thinking the plugin may only read the conf once during firefox startup.  To my surprise, it didn't work and the conf file had been changed back!  It would appear that the plugin overwrites the conf with the state it was in when it was read in.

I then made the changes to the conf manually and restarted ffox and it worked just fine.  I'm guessing if I'd closed firefox, made the changes in acroread, and then reopened firefox it would have worked fine too.

Hope this helps!

Now, I have a question for you guys:  Where do I find that default setting of 181 pixels per inch?  I don't know where that is set.  I've looked through environment variables and KDE settings, but haven't found it yet.  Maybe I'm not looking in the right place or I've overlooked it somehow.  

You can reach me at mkenigson <([at])> franklinamerican <{dot}> com

Thanks in advance,

Matt

---

### Post by mkenigson on 2006-05-25
I found this excellent article:  [http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html) that explains my issue with the system default resolution setting.  

It turns out that in my case, since I am using a dual head (two monitors) setup, it effectively gave me these dimensions and resolution:

xdpyinfo | grep dimensions
  dimensions:    2560x1024 pixels (361x292 millimeters)
xdpyinfo | grep resolution
  resolution:    180x89 dots per inch

Thus, the 181 pixels per inch (not sure where it got the extra dot, but it's close enough that I'm satisfied this is the right answer).

---

### Post by gmcauley on 2006-05-25
Great! This solves the problem.  I also use two monitors.

Not sure why, but after the (easy) fix in Adobe Reader, my other PDF viewers work correctly.

Thank you for passing on what you have found!

---

