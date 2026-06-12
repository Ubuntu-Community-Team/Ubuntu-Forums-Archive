---
title: "Trouble in Matlab writing the symbol ^"
date: 2007-05-07
forum: Education &amp; Science
---

### Post by lognok on 2007-05-07
Hi there,
  My Matlab (2006a) has problem with my danish keyboard-layout, as it refuses to write the (hat/power)-sign ^
When I enter the ^ key, it doesn't show (also tried to press space as this seams to bring it forth in gedit or any other command environment), instead it super scripts the next number I enter. So if I enter 9^9, it shows 9&#8313;.

If I change my keyboard-layout to Denmark+eliminate dead keys it works, but then I can't write brünger, it becomes br"unger.

Funny thing is when I write some code in gedit which includes the ^ sign and paste it into Matlab (either editor or command line) then it displays correctly and runs!!??.

Is there a way for me to fix this?

Thanks for any reply.

---

### Post by melissawm on 2007-05-07
Hi! What happens if you try typing ^ and then a space after? It should work... If not, I know there are ways to configure keys separately, i'll take a look for you.

---

### Post by engla on 2007-05-07
Typing the space should work. Otherwise you can also run matlab as "matlab -nojvm" (it now runs from the terminal console), but it is uglier..

---

### Post by lognok on 2007-05-08
Pressing space doesn't do anything.

If I type: 9 ^ 9 it gives: 9&#8313;
If I type: 9 ^ [space] it gives only 9, so pressing space right after the ^ sign doesn't produce anything.

But thanks for your suggestions.

---

### Post by Eric_T on 2007-05-09
I have the same problem on a Norwegian keyboard layout.
I just use ViM for editing my m-files to work around it. There are lots of Matlab-related
scripts out there, and the editing functionality of ViM far surpasses Matlab's editor.

---

### Post by ahmatti on 2007-05-09
There is a bug in Matlabs Java VM that prevents the use of any dead key + space bar combination...
[http://www.mathworks.com/support/bugreports/details.html?rp=100994](http://www.mathworks.com/support/bugreports/details.html?rp=100994) (needs subscription) 

In my finnish keyboard this means that ~ and ^ don't work. 

**You can fix the problem** by remapping the characters to some other keys. I use the following script to map ^ to F11 and ~ to F12.

```

#!/bin/sh
xmodmap -e "keycode 95 = 94"
xmodmap -e "keycode 96 = 126"

```

You have to run the script every time after restart (manually or automatically)

---

### Post by lognok on 2007-05-10
Thanks ahmatti, I'll use your script until the jvm problem is solved.

---

### Post by ppm on 2008-03-26
Cheers ahmatti,

In case anyone is wondering where to put that script I created a user-specific config file i.e. ~/.xmodmap with the contents posted by ahmatti.

---

