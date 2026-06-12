---
title: "Automatic selection problem with Firefox in Jaunty"
date: 2009-04-27
forum: General Help
---

### Post by mb_webguy on 2009-04-27
Is anyone else having a problem with Firefox where words in the Search or Address bars are being automatically selected as you type, making it nearly impossible to type anything over a few letters?

---

### Post by codeseer on 2009-04-27
Too vague of a description for me to envision exactly what is happening.

Have you tried with another profile?

```
firefox -profilemanager -no-remote
```

You might also try giving your Tab, both Enter and all Arrow keys a few taps to make sure they're not half-stuck.

---

### Post by mb_webguy on 2009-04-27
Well, it's an odd problem to describe.  Let's say I want to search for "foobar".  So I click in the Search bar and start typing.  I'll get about two or three letters in, depending on how fast I'm typing, and everything I've typed so far will automatically become selected.  So let's say I've made it to the second "o", for "foo".  That's now selected.  And because it's selected, if I type another character, the new character will overwrite the selected text.  So instead of typing "foobar", I end up with just "bar".  I can type a whole sentence, and only end up with the last few characters.  This happens in the Search box and the Address bar, but nowhere else.

And it's hard to diagnose, since restarting Firefox will fix the problem temporarily.  Yes, I have tried a different profile, and no, the problem didn't show up.  But when I switched back to my normal profile, the problem didn't recur until I'd been using it for 5 minutes or so.  I use my browser to work, and so I don't have the luxury to switch to a different profile for an extended period of time just to see if a problem might show up...

---

### Post by codeseer on 2009-04-27
Oh yeah. I had that happen a while back. Switching to a new profile worked for me. I figured it was a profile corruption. Must be more like a bug though. But switching profiles should fix it for you.

I also had one where I would be typing and the point would jump to the front of the line over and over. So, I ended up with a word that looked like this: ginthmeSo

---

### Post by mb_webguy on 2009-04-27
*sigh*  Yeah, I guess that was it.  I backed up my bookmarks and passwords and created a new profile.  So far, it seems to be working fine.  Of course, it's only been about 15 minutes, so...  who knows?

I was halfway hoping it wasn't a corrupted profile, because-- well, as far as I know, I didn't do anything to cause it.  And if you don't know why something's happening, it's hard to fix.  Since it started right after I'd installed a bunch of updates, I thought it might be a more widespread problem which would mean a fix would also be in the works.

Anyway, thanks...

---

### Post by prconnor@gmail.com on 2011-09-15
This issue keeps recurring for me also.  It is quite a hassle to keep making new profiles; and as you mention, I have no idea what I am doing to make it so.

I would prefer know how to fix it without deleting the profile.  I have largely stopped using the search bar in preference to starting over again with a new profile.

---

### Post by Wim Sturkenboom on 2011-09-15
You might be able to compare two profiles. I'm not familiar with the concept of profiles and I usually also do not look in hidden directories, but you should be able to find the profiles in one of the hidden directories in your home directory; either as separate files or as one file that you can copy, split and run a diff on.

That way you might find what has changed which might be a pointer to why it changes. And it might give you an 'easy' way to restore.

PS
I've never had the issue on 6.06, 8.04 or 10.04

---

