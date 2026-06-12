---
title: "font failure in Emacs"
date: 2011-12-17
forum: Desktop Environments
---

### Post by bkline on 2011-12-17
I just installed a fresh Xubuntu on my laptop, and I have run into a problem that has me puzzled.  When I connect to the servers of one of my customers with this laptop and try to run emacs I get the following error message:```
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

```When the emacs window comes up all of the characters are represented by square boxes instead of recognizable character glyphs.

Let me start by acknowledging that my understanding of X Windows, and in particular fonts under X Windows, is pretty thin.  From a little Wikipedia reading, I get the picture that although the design of X Windows allows the rendering of fonts to happen on either the X client or the X server, "The use of server-side fonts is currently considered deprecated in favour of client-side fonts." [1]  So I would think that the problem is on my customer's servers, not my laptop.  But here's the puzzling part: I don't have this problem using emacs on those servers from any other machine, including X in Cygwin on Windows machines.  And I can use emacs without this problem when connected to my own servers (running Debian).  (The customer's servers are RHEL 5.5 boxes.)

Any X Windows gurus out there who can tell me where to start looking to track down and solve this problem?  Is it possible that in spite of what I've quoted above from Wikipedia (about the X client handling the font rendering) that it's the X server on my laptop which is missing something (this is the only machine on which I've installed xfce without already having gnome in place).  If so, why wouldn't I run into the problem when connected to my Debian servers?

Thanks for any enlightenment you can shed!

[1] [http://en.wikipedia.org/wiki/X_Font_Server](http://en.wikipedia.org/wiki/X_Font_Server)

---

### Post by bkline on 2011-12-17
Well, in spite of that line from Wikipedia I quoted in the previous message, it looks like it's the X server (that is, my laptop) which renders the fonts (at least in Xubuntu).  After further digging, I came up with a solution which involved creating the file ~/.Xdefaults with the line ```
emacs*font: 7x14
``` and then running ```
xrdb -merge ~/.Xdefaults
```.  Problem gone!

So I guess Xubuntu/xfce leaves out fonts that the rest of the world assumes will be there.  Hope this is useful to someone else who might run into the same problem.

---

### Post by screaqy on 2012-06-06
Brilliant!!! I'm new to Ubuntu and I've been looking for the solution for a long time and it's now solved! Thanks!!!

---

### Post by bkline on 2012-06-06
I'm amused at how my brain works (or doesn't) as I get older.  So yesterday I had a hardware failure and I needed to rebuild my workstation.  Didn't take too long, and I get back to work and notice that as I start editing source code I've got nothing but square blocks in emacs.  So I start googling and what do I find but my own post.  Apply my own solution and I'm back on the road.  A couple of minutes later screaqy's message hits my inbox.  Gotta love the internet (and this forum)!

@screaqy: glad it helped you, too. :-)

---

### Post by johnsg on 2012-07-24
Thanks for the fix - worked perfectly for me after a fresh install of emacs on 12.04!

---

### Post by econrad on 2012-09-19
Thanks this worked for me too!

---

### Post by mguycooper on 2013-04-07
Wow thanks a bunch, this worked for me as well.

---

### Post by mguycooper on 2013-04-09
Hi,

This works for me but everytime I close down Ubuntu and then reopen I have to use the command -xrdb -merge ~/.Xdefaults over again. Does the .Xdefaults file have to be in a particular directory?

---

### Post by mguycooper on 2013-04-23
bump^

Anyone know how I can avoid having to type 'xrdb -merge ~/.XDefaults' every time I reboot?

---

### Post by mguycooper on 2013-04-23
Nevermind! I think i just needed to add a new line to the end of the .Xdefaults file. Thanks again for the great solution!

---

### Post by mguycooper on 2013-04-24
I have a follow up question to this thread. 

Despite what I indicated above, I still have to execute the [COLOR=#000000]'xrdb -merge ~/.XDefaults' command each time I start a new shell. I would like to figure out a way to not have to do this! I created a file called 'fonstruct' that contains the line: [/COLOR][COLOR=#000000]'xrdb -merge ~/.XDefaults'. I was thinking that everytime I ssh into the shell I could simply type:

./fonstruct

and the file I created with the line [/COLOR][COLOR=#000000]'xrdb -merge ~/.XDefaults' would execute on the command line and I could use emacs. But, when I type

./fonstruct

I get error "Command not found"

Anyone know why I get the "Command not found" error? Or how I could simply have the .Xdefaults file execute automatically so emacs just works everytime I start a new shell?  

Thanks![/COLOR]

---

### Post by Tortoise_74 on 2013-05-24
Just a note to say I tried emacs*font: 7x14 and not only did it not work it broke emacs with "No fonts match '7x14'"

The trick is to run "xlsfonts" which lists the available fonts and pick one of those.

---

### Post by bkline on 2013-05-25
> **mguycooper said:**
> I have a follow up question to this thread. 

Despite what I indicated above, I still have to execute the [COLOR=#000000]'xrdb -merge ~/.XDefaults' command each time I start a new shell. I would like to figure out a way to not have to do this! I created a file called 'fonstruct' that contains the line: [/COLOR][COLOR=#000000]'xrdb -merge ~/.XDefaults'. I was thinking that everytime I ssh into the shell I could simply type:

./fonstruct

and the file I created with the line [/COLOR][COLOR=#000000]'xrdb -merge ~/.XDefaults' would execute on the command line and I could use emacs. But, when I type

./fonstruct

I get error "Command not found"

Anyone know why I get the "Command not found" error? Or how I could simply have the .Xdefaults file execute automatically so emacs just works everytime I start a new shell?  

Thanks![/COLOR]

Try "chmod +x fonstruct" to solve your first problem.  For the second you might want to look into creating an .xinitrc file.

---

### Post by bkline on 2013-05-25
@myguycooper: Also, apologies for the delayed reply to your questions.  I am subscribed to the thread, but for some reason I hadn't received notification from the forum for any of your posts.  I did get a notification when Tortoise_74 posted, and when I followed the link in the notification to the thread that was the first time I realized there had been other posts recently.  Perhaps the forum software is experiencing some hiccups.

---

### Post by bkline on 2013-05-25
> **Tortoise_74 said:**
> Just a note to say I tried emacs*font: 7x14 and not only did it not work it broke emacs with "No fonts match '7x14'"

The trick is to run "xlsfonts" which lists the available fonts and pick one of those.

Yes, sorry I didn't mention that step in my original posts.

---

