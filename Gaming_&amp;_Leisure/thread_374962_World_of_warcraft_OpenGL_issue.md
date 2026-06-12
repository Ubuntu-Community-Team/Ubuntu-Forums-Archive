---
title: "World of warcraft OpenGL issue"
date: 2007-03-03
forum: Gaming &amp; Leisure
---

### Post by reazn on 2007-03-03
I'm mucking around trying to get world of warcraft working on my laptop.. Why on my laptop? Because my PC now sits in another room and has basically turned into a file server. I use my laptop for work & at home. 

I've been playing around with cedega and wine. I'm able to load warcraft, get in game etc, but I've found i'm having an issue with what appears to be tearing and colours.. 

check out the screenshot:

[img]http://www.reazn.net/pics/opengl.png[/img]

any ideas?

---

### Post by Sammi on 2007-03-03
You should try the panel icon fix found in the [Ubuntu community WoW/Wine howto's]("https://help.ubuntu.com/community/WorldofWarcraft") troubleshooting section: 
```
If you experience corrupt icons on your panel then you then you may need to set the SET UIFaster parameter in wtf/Config.wtf 
Use it like this: 
   Set UIFaster &#8220;x&#8221;  
Where x equals:
   0 &#8211; This turns off all UI acceleration
   1 &#8211; For Internal Use Only - DO NOT USE!
   2 &#8211; Enables partial UI acceleration only.
   3 &#8211; Enables all UI acceleration.
Example:
   Set UIFaster &#8220;2&#8221;
The value 2 usually corrects this problem.
```

---

### Post by reazn on 2007-03-03
> **Sammi said:**
> You should try the panel icon fix found in the [Ubuntu community WoW/Wine howto's]("https://help.ubuntu.com/community/WorldofWarcraft") troubleshooting section: 
```
If you experience corrupt icons on your panel then you then you may need to set the SET UIFaster parameter in wtf/Config.wtf 
Use it like this: 
   Set UIFaster “x”  
Where x equals:
   0 – This turns off all UI acceleration
   1 – For Internal Use Only - DO NOT USE!
   2 – Enables partial UI acceleration only.
   3 – Enables all UI acceleration.
Example:
   Set UIFaster “2”
The value 2 usually corrects this problem.
```


Thanks, works fine now :)
kudos 4 u

---

