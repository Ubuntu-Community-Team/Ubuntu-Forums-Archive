---
title: "[SOLVED] No text in firefox"
date: 2008-12-11
forum: General Help
---

### Post by JoyousDeath on 2008-12-11
I've seen this problem in other threads, but as of yet none have helped.

I'm pretty sure this problem occurred after I installed some new text into my text folder (though this didn't work anyway :/ ).

I'm on ubuntu 8.10 Hardy Harry.

Assume I know nothing about ubuntu (easier to just say this than state the few things I do know...).

---

### Post by mdurham on 2008-12-11
> I'm pretty sure this problem occurred after I installed some new text into my text folder (though this didn't work anyway :/ ).
 Can you explain exactly what this means?
What is 'installed new text'?
What (where) is 'text folder'?
What was the 'installed text' supposed to do?
Cheers, Mike

---

### Post by JoyousDeath on 2008-12-11
> **mdurham said:**
> Can you explain exactly what this means?
What is 'installed new text'?
What (where) is 'text folder'?
What was the 'installed text' supposed to do?
Cheers, Mike

I followed a tutorial, can't remember which, and tried to install fonts (.ttf files) to a system folder. This was a failure.

Here is the location of the installation... 
/usr/share/fonts/truetype/font-install

---

### Post by ajcham on 2008-12-12
I assume [thread=275202]this[/thread] is the tute you followed?

If so, this is overly complicated.  Installing new fonts is actually far easier.  All you need to do is create a .fonts directory in your home.  You can do this in nautilus or with the command: ```
mkdir ~/.fonts
```

Just place any fonts you want to use in that directory.

Try removing the fonts that the script installed, to see if that solves your firefox issue.

---

### Post by JoyousDeath on 2008-12-14
Yes, that is the script I used. However, I cannot simply remove the fonts installed and hope to have it better (for two reasons).

1: I installed so many I wouldn't know which ones to uninstall in the first place.
2: The script replaced many of the fonts with other fonts with similar names...

---

### Post by JoyousDeath on 2008-12-21
Just wondering if anyone has an answer...

Or if someone could give me a download location to the default folder of: > /usr/share/fonts/truetype/font-install

---

### Post by JoyousDeath on 2009-01-09
Does anyone have an answer?

I'm still stuck.:(

---

### Post by paddy2706 on 2009-01-10
this folder does not exist on any of my ubuntu machines.

---

### Post by JoyousDeath on 2009-01-12
> **paddy2706 said:**
> this folder does not exist on any of my ubuntu machines.

That's okay, though. I fixed it.
Forgot how though...:confused:

---

### Post by DukeBoxer on 2009-12-11
I think I know how to fix this because I had the same problem. I made the .fonts directory and imported all the fonts from microsoft office, but in the .fonts directory somehow there was another directory "Fonts" (I may have just moved that folder into the .fonts) 

I logged in as root, went into the .fonts/Fonts directory and removed all the .ttf files, leaving all the .fon ones alone.  This seemed to do the trick.

---

### Post by jeff betts on 2010-11-17
Thanks all - I've had two desktops and a laptop suffer with this problem and I can now fix it - Hurrah!

---

