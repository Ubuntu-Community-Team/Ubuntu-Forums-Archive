---
title: "Compiz transparency question"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by rmcder on 2008-01-12
I'm using ubuntu 7.10, ati restricted driver, xgl-compiz-emerald installed.  I can make windows more or less transparent either directly, or by defining the windows directly.  What I can't do is to set up a situation where the window that has the focus is opaque, but the windows that do not have the focus are transparent.  Is there a way to do that?

---

### Post by lian1238 on 2008-01-13
> **rmcder said:**
> I'm using ubuntu 7.10, ati restricted driver, xgl-compiz-emerald installed.  I can make windows more or less transparent either directly, or by defining the windows directly.  What I can't do is to set up a situation where the window that has the focus is opaque, but the windows that do not have the focus are transparent.  Is there a way to do that?
Yes, there's a way. Enable ADD Helper in compiz. Adjust the values according to your needs.

Edit: The default combination to toggle ADD Helper is <Super>+P. (note: <Super> is the windows key, just in case.)

Cheers.

---

### Post by rmcder on 2008-01-13
Excellent; thank you!!  Why isn't there a decent manual that: (a) covers this stuff, and/or (b) can be found??

---

### Post by lian1238 on 2008-01-13
> **rmcder said:**
> Excellent; thank you!!  Why isn't there a decent manual that: (a) covers this stuff, and/or (b) can be found??
I don't know. But once you've tried all the plugins, you won't need a manual! :D
If you don't want to try them all, you could just ask, like you did here.

Edit: the reason, they say, compiz doesn't have a decent manual is because it is in a constant state of "Development". Go figure.
Edit: Just out of curiousity, what would you expect from a manual? Just in case I feel like making one! ;)

P.S. Could you make that 'thank you' official? ;)

---

### Post by Forlong on 2008-01-13
A nicer plugin for that would be Trailfocus.
Just change the value of *Windows to Start Fading* to 1

---

### Post by rmcder on 2008-01-13
> **lian1238 said:**
> P.S. Could you make that 'thank you' official? ;)
If you would be kind enough to tell me how, I'd be glad to.

---

### Post by rmcder on 2008-01-13
> **Forlong said:**
> A nicer plugin for that would be Trailfocus.
Just change the value of *Windows to Start Fading* to 1
I took a look, and although both solutions work, this is the better of the two solutions since it activates automatically.  Thank you!

---

### Post by lian1238 on 2008-01-14
> **rmcder said:**
> If you would be kind enough to tell me how, I'd be glad to.
It's a new feature of this forum. When you find a useful post, you can give a 'thanks' by clicking on the icon that looks like a medal. It's next to the 'quote' button. ;)

---

### Post by trash on 2008-01-16
Is there anything that could prevent unfocused windows from being faded? I love the ADD helper but can't get it working using compizconfig, also installed is gldesktop and emerald.

---

### Post by lian1238 on 2008-01-17
> **trash said:**
> Is there anything that could prevent unfocused windows from being faded? I love the ADD helper but can't get it working using compizconfig, also installed is gldesktop and emerald.
Have you turned it on? You need to turn it on by pressing <Super>+P. <Super> is the windows key.

---

### Post by trash on 2008-01-17
> **lian1238 said:**
> Have you turned it on? You need to turn it on by pressing <Super>+P. <Super> is the windows key.

yup, lets say i have 4 windows open it will minimize 2 and leave 2 the way they were... no fading what so ever:(

---

### Post by trash on 2008-01-17
After disabling a couple of other plugins add helper is now working but a couple of times now the plugin turns itself off, possibly after stopping and starting desktop effects for gaming. It is possible gldesktop is causing problems, for example after some restarts my menu bars don't function until i restart gldesktop(which always requires starting 2 instances before it actually opens) at which point all windows seem to blink(reset) and whithout changing any setting in gldesktop menubars become functional again.

---

### Post by rmcder on 2008-01-17
> **lian1238 said:**
> Edit: the reason, they say, compiz doesn't have a decent manual is because it is in a constant state of "Development". Go figure.
Edit: Just out of curiousity, what would you expect from a manual? Just in case I feel like making one! ;)

I've found bits and pieces here and there.  I've got a page of common Compiz-Fusion keyboard shortcuts.  There's a Compiz-Fusion wiki that has a lot of what I needed, and includes information on using the Settings Manager.  What I would say is missing is a FAQ for stuff people want to do, but don't know how.  How do I get windows to fade (I saw no mention of Trailfocus anywhere)?  How do I get windows to be transparent/translucent?  How do I see the cube the way it's always pictured? 

I ran into a problem trying to define a key combination to execute a command - I went to the Settings Manager, 'Commands', and put the command in as 'command 0', went to 'Actions' and tried typing in SUPER+1 (turns out it needs to be <SUPER>1), I tried it as a key-capture.  Nothing worked, and there wasn't any documentation on how to do it.  Eventually, I stumbled on the fact that you can click on column under the heading ('key' in this case), and on the same line as the command you want, and it'll do a key-capture.

How do you install themes under Emerald?  Found documentation at Hacktivision Lite finally, and discovered why most of the themes I was downloading from Gnome-Look wouldn't work.  I still don't know why gtk-2 "themes" don't load OR drag and drop as they're supposed to.  It's so frustrating for a newcomer to try to find out how to do anything; you wade through countless threads that give you four ways to do things (and only one of them uses words you've ever heard of - commandline stuff is pretty much incomprehensible).  You get (often) conflicting instructions, or instructions that worked for Edgy two years ago, but don't work now.  Etc, etc.  The great thing is that people are willing to help.

Heck, after about a week, I've gotten most everything working, and I'm kind of used to thrashing around looking for obscure files, drivers, and directions; after all, I was an OS/2 fan/user for years.  :)

---

### Post by ubuntu-freak on 2008-01-20
What do you mean by getting the cube to look as it's always shown?
 
I'm not on Ubuntu right now so bear with me. If you press alt and page up/down or scroll up/down it changes window transparency. To stop windows snapping on edges, you don't just disable the snapping plugin, you have to go into the wobbly windows plugin and untick the invert thing at the top. Um what else..to change aspects of the cube you go into both the cube plugin and rotate cube plugin. Then there is the cube cap plugin near the bottom (extras?).
 
Hope that helps.
 
Nathan

---

### Post by rmcder on 2008-01-20
> **reassuringlyoffensive said:**
> What do you mean by getting the cube to look as it's always shown?
The view you always see in photos is produced with the CNTL-ALT-LEFTBUTTON combination.  Of course if you don't KNOW that, then you never get the cube to look "right".

---

### Post by ubuntu-freak on 2008-01-20
> **rmcder said:**
> The view you always see in photos is produced with the CNTL-ALT-LEFTBUTTON combination.  Of course if you don't KNOW that, then you never get the cube to look "right".

 
Oh! You didn't know how to rotate the desktop? Must have been frustrating! I didn't have a clue what the 'super' button was for a long time. Whenever I googled it I would just find posts that told me to press it, but not explain what the smeg it was. Ah well. (it's the key with the useless Windows logo on it people, incase you're wondering).
 
Nathan

---

### Post by rmcder on 2008-01-21
> **reassuringlyoffensive said:**
> Oh! You didn't know how to rotate the desktop? Must have been frustrating! I didn't have a clue what the 'super' button was for a long time. Whenever I googled it I would just find posts that told me to press it, but not explain what the smeg it was. Ah well. (it's the key with the useless Windows logo on it people, in case you're wondering).
 
Nathan
No, I could rotate the cube just fine - mousewheel or cntl-alt-arrow.  The problem was that the cube was never fully visible and set "back" from the screen the way it is with cntl-alt-left mouse button.  Reading through various threads, I can see that I'm not the only one who didn't realize that you can have the cube working just fine, and it won't look like the pictures unless you know the "magic"  key-mouse combination.

---

