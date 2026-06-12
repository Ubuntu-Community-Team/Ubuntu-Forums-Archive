---
title: "shell font changed...!!!"
date: 2008-05-17
forum: Desktop Environments
---

### Post by vikyrulz on 2008-05-17
hi guys,

I am a newbie in linux... I came across extremely astounding situation..
I ran a command

> cat /usr/bin/totem


This changed the font of my shell... Dunno whats the bug... U guys might wanna try dis.. I am still trying to restore my "ENGLISH" font...:(

---

### Post by scxtt on 2008-05-17
> U guys might wanna try dis
why would you (suggest to others to) cat a binary (i.e. non-text) file?
there's no sense in doing it ... and what it does to the terminal isn't permanent ...

---

### Post by vikyrulz on 2008-05-17
yes its not permanent... Juz wanted u guys to have a look at it... when i said font changed.. i meant about the shell itself.. So, I guess there is some bug in it.. i dunno wats happening :-D

---

### Post by scxtt on 2008-05-17
it's not a "bug", there's no reason to cat a binary file via the shell ...

---

### Post by vikyrulz on 2008-05-17
hmm... fine.. I know there is no reason to do this...

But, why is shell's font changing??? Why isn't it plain english language :D.. According to my knowledge cat should have no effect on it...

can sum1 please explain the reason behind it... 

P.S.: I completely understand there is no need to cat a Binary file...

---

### Post by 16777216 on 2008-05-17
cat is just trying to interprit the binary code of the file to ascii and/or unicode ( or what ever encoding you are using ) thus showing the international and extended charters.

---

### Post by scxtt on 2008-05-17
use **strings** if you want to see if there's any ascii text in a binary file ...

---

### Post by edammy on 2011-03-21
Run the following command on shell:
 echo -e '\017'

That should fix it

---

### Post by edammy on 2011-03-22
The binary file had a shift-out (016) character. Pushing 
a shift-in character resets the character set.

---

