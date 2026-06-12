---
title: "help compiz no edges!!"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by XxPoseidoNxX on 2007-08-04
Hi
I just installed compiz-fusion,and I have a window edge problem.:(

---

### Post by Deco_21 on 2007-08-04
First try this .
Find the Beryl part. 
Install it 
[HTML]http://ubuntuforums.org/showthread.php?t=488385[/HTML]
 And then in the beryl-manager Chose Windows Decoration > Metacity


And then try ALT+F2

"compiz --replace" 
its double - -

"emerald --replace"

Tell me if you have any problem.

In order to get compiz fusion working , you must install beryl , its the easiest way . ok . 
It will work.

---

### Post by sprinkles on 2007-08-04
Install Emerald:

```

sudo apt-get install emerald
```

Then try this:
```

compiz --replace -c emerald &
```

Hope this helps, it worked for me.

---

### Post by Vozmozno on 2007-08-06
you may also want to do this:

```

sudo apt-get install libemeraldengine0
```

If you haven't updated your system recently then that line could do the trick for you, it did for me =)

---

