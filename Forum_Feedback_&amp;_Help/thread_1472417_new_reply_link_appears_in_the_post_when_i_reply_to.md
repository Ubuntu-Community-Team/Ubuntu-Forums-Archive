---
title: "new reply link appears in the post when i reply to a thread"
date: 2010-05-04
forum: Forum Feedback &amp; Help
---

### Post by nitstorm on 2010-05-04
ubuntuforums.orgubuntuforums.org/showthread.php
> ubuntuforums.orgubuntuforums.org/newthread.php This thing just showed up once i started up this thread and hence the edit.

> ubuntuforums.orgubuntuforums.org/newreply.php

this is the line that gets added to every post i make as a reply to a thread. Can this be stopped? Started just two days back I think. Getting pretty annoying that thing... Please do help.  Thanks and Cheers!

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
Can someone please move this to the "forum feedback and help" i posted this in General Help accidentally...

---

### Post by lisati on 2010-05-05
Moved to FF&H

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
Thanks lisati and also if i could have a way of solving this, it would be great.. Thanks..

---

### Post by lisati on 2010-05-05
Looking through some of your posts, I see what you mean. It almost looks as if links you've recently clicked on are somehow being "dragged" into the text editor.

No flashes of inspiration come to mind on fixing it. Anyone else got any ideas?

---

### Post by cariboo on 2010-05-05
I would suggest you clear your cache, to see if it makes a difference.

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
I keep clearing out my cache( by clearing i mean FF->Tools-> Clear Recent History->Everything ) will that be enough or are there some separate files in folders (like in windows) that i'll have to clear out?

---

### Post by ubunterooster on 2010-05-05
Is it only on this forum?

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
yes it's only on ubuntuforums.org

---

### Post by Elfy on 2010-05-05
You could have a look in the Error Console see if there is anything there.

Try backing up bookmarks/passwords and starting the profilemanager and make a new profile 

```
firefox -ProfileManager
```

---

### Post by jpeddicord on 2010-05-05
Also try disabling (all of) your extensions.

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
Whole bunch of errors in the error console. This is the most recent one and there's a bunch of this same one repeatedly:
> 
Warning: Error in parsing value for 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-b1f0a663-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-b1f0a663-00098.css)
Line: 484


Will create a New Profile and post back if that solves it.

---

### Post by Elfy on 2010-05-05
Try jpeddicord's suggestion first.

---

### Post by nitstorm on 2010-05-05
> jpeddicord              **Re: new reply link appears in the post when i reply to a thread**
         Also try disabling (all of) your extensions.     So here is a test post..

And wow!!! it did it !!! Great!!! Never thought about disabling the extensions. Thanks for the help guys. Cheers!

---

### Post by Elfy on 2010-05-05
I bet you're glad that's sorted :)

Have you worked out which one it was?

---

### Post by nitstorm on 2010-05-05
> **forestpiskie said:**
> I bet you're glad that's sorted :)

Have you worked out which one it was?


Of course I am :D this post is going to be used for testing and detecting the extension that gave me a hard time.


And I found it . A user-script enabled by greasemonkey to embed the site into a google search. Helps with searching the forums easily but guess it's going to be disabled :(

Anyhoo thanks for putting up with this guys . Cheers again!

---

### Post by Elfy on 2010-05-05
I use a couple of search engines for here one is googlbuntu the other I think is a crunchbang search engine. I did use uboontu but that appears to have gone :(

---

### Post by nitstorm on 2010-05-05
googlubuntu seems pretty good :) thanks forestpiskie :)

---

### Post by Elfy on 2010-05-05
I preferred uboontu - but it's been down for a while now :(

---

