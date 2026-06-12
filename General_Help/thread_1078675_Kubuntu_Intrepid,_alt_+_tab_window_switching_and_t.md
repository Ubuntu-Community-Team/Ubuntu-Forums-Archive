---
title: "Kubuntu Intrepid, alt + tab window switching and text input in OpenOffice."
date: 2009-02-23
forum: General Help
---

### Post by TWO on 2009-02-23
It might seem like a strange title, but it describes an unusual problem I'm experiencing at the moment.

I'm currently doing some typing, and occasionally, I need to refer to webpage for information. To make the process of switching between windows quicker, I'm using the *alt + tab *keyboard combination, however after doing this, I'm finding that I stop being able to enter text into OpenOffice Word Processor for some reason. 

To resolve it, I have to click outside of the word processor window onto either the desktop background or onto the Notes plasmoid that I have running, then back within the window.

Just this second, the problem has also occured when I swtiched back to Firefox to continue typing this post. 

The last time I experienced this problem was back with Hardy Heron, and it occured in aMSN and Skype, and again with OpenOffice Word. 

I have a hunch that it might have something to do with SCIM, but I don't have any tangible evidence to prove this. Also, I'm not willing to uninstall and reinstall the program since it takes a heck of a long time to configure correctly.

Does anyone know what the source of the problem is? Has anyone else experienced this?

TWO

---

### Post by TWO on 2009-02-24
OK, so this problem just occured whilst I was browsing with Konqueror. 

(And I hadn't switched windows with *alt + tab *shortcut either.) 

Only this time, clicking outside of its window, onto the notes plasmoid, and even within OpenOffice Word and Firefox did not resolve it. I was able to type in the other programs and just not Konqueror.

For what it's worth, I'm going to uninstall SCIM to see if it might be a factor in all of this. 

TWO

---

### Post by Koterpillar on 2009-04-03
Since this is similar to what I was seeing, can you try following this: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252144/comments/5](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252144/comments/5)
(Also see [this thread](http://ubuntuforums.org/showthread.php?t=836370).)

---

### Post by TWO on 2009-04-07
> **Koterpillar said:**
> Since this is similar to what I was seeing, can you try following this: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252144/comments/5](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252144/comments/5)
(Also see [this thread]("http://ubuntuforums.org/showthread.php?t=836370").)

I did find that SCIM was indeed the problem and my resolution was to completely remove SCIM and use UIM input method instead, as demonstrated on the following page by Ryukent:

[http://www.ryukent.co.uk/show.php?id=28](http://www.ryukent.co.uk/show.php?id=28)

Since I only need Japanese input, this solution works fine for me when I'm using Kubuntu. Incidental, I've reverted back to Kubuntu Hardy, but it should work regardless of the version of Kubuntu.

---

