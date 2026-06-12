---
title: "need exit command for script file"
date: 2009-04-19
forum: General Help
---

### Post by CalSkeptic on 2009-04-19
I'm trying to write a shell script that will open the appearance/properties window and then close it again.  Here's what I have so far:

#!/bin/sh
gnome-appearance-properties %F

That opens the window.  Now I need to add a command that will close it again.  "Exit" doesn't seem to work.

Can someone please tell me what command I should use to close the window?

---

### Post by snova on 2009-04-19
> **CalSkeptic said:**
> Can someone please tell me what command I should use to close the window?

You could kill the process:

```
killall gnome-appearance-properties
```

But if you just put those two commands in order, it'll appear for a brief second and disappear the next.

Actually, it won't even do that, because the second line of your script won't end until the window closes. You could put it in the background, though, and your script would continue:

```
gnome-appearance-properties %F **&**
```

---

### Post by CalSkeptic on 2009-04-19
Well, snova, I tried your suggestion.  Here's what my script looks like now:

#!/bin/sh
gnome-appearance-properties %F &
killall gnome-appearance-properties

It works the same as before.  The window appears and just stays there.  What am I doing wrong?

---

### Post by codeseer on 2009-04-19
> **CalSkeptic said:**
> I'm trying to write a shell script that will open the appearance/properties window and then close it again.  Here's what I have so far:

#!/bin/sh
gnome-appearance-properties %F

That opens the window.  Now I need to add a command that will close it again.  "Exit" doesn't seem to work.

Can someone please tell me what command I should use to close the window?

Why?

---

### Post by CalSkeptic on 2009-04-19
> **codeseer said:**
> Why?

It's a workaround for a bug, codeseer.  Do you have an answer to my question?

---

### Post by codeseer on 2009-04-19
> **CalSkeptic said:**
> It's a workaround for a bug, codeseer.  Do you have an answer to my question?

Not at the moment. I tried out a few thoughts I had, but none worked so far.

Edit:

Does this work for you?

```
gnome-appearance-properties %F | bash -c "killall gnome-appearance-properties"

```

---

### Post by codeseer on 2009-04-20
Ok, I made this for you. It should come real close to working, but may need some minor modification for whatever you're trying to do.

```

#!/bin/bash

for ((a=0; a <= 1; a++))
do

if [ $a != 0 ]
then
killall gnome-appearance-properties
else
gnome-appearance-properties %F
sleep 1
fi

done

exit 0

```

If you're doing what I think you are and will need to be passing a parameter in, you might need to replace %F with $1.

---

### Post by CalSkeptic on 2009-04-20
Thanks, codeseer.  Full disclosure: For some unknown reason, starting while I was using 8.10 and then continuting when I upgraded to 9.04, Ubuntu started booting Gnome with small system fonts.  I discovered that if I click System/Preferences/Appearance, the fonts revert to normal.  I put out a request for help and the consensus seemed to be that it is a bug.  So I'm trying to make a workaround.

Any of the three files, my original one or either of your two suggestions, will boot to the Appearance screen, causing the fonts to revert to normal.  But I have to close that window manually.  To make a script file do the whole thing I need two things:

1. A way to close that window.
2. A way to make the file execute when Gnome boots up.

This is obviously not a huge problem.  But any further suggestions you can make will be appreciated.  As a newbie without Linux programming experience, I'm really at a loss for what to do.  Thanks again for your help.

---

### Post by codeseer on 2009-04-20
It will probably be fixed when Jaunty is officially released and you run the upgrade again.

That script I gave you should have worked if you put it in the Sessions area. I'll look into it and get back to you.

Edit:

What's the significance of %F?

---

### Post by CalSkeptic on 2009-04-20
> **codeseer said:**
> 
What's the significance of %F?


I have no idea.  I just added a launcher to the desktop and then copied the command from that.  Yes, I know, I know...  But what could you expect from someone raised on DOS and Windoze?  :)

Oh, and ummm...what sessions area?  I know it's supposed to be there, but I can't find it.

---

### Post by codeseer on 2009-04-20
> **CalSkeptic said:**
> I have no idea.  I just added a launcher to the desktop and then copied the command from that.  Yes, I know, I know...  But what could you expect from someone raised on DOS and Windoze?  :)

Oh, and ummm...what sessions area?  I know it's supposed to be there, but I can't find it.

System->Preferences->Sessions

Edit:

I'm still working on it. This reminds me of trying to do crazy stuff in batch files years ago.

---

### Post by codeseer on 2009-04-20
*bump to see if anybody else knows*

You could split the opening and closing into two separate bash scripting files and add a wait to the closing. That would most likely work. I'm not sure if there's a way to specify the load order explicitly.

If we ever do figure this out, it's going to probably be something ridiculously simple. ;)

---

