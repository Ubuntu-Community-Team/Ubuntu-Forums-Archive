---
title: "Text Based RPG Maker?"
date: 2010-03-17
forum: Gaming &amp; Leisure
---

### Post by Stigmata13 on 2010-03-17
Does anyone know a good one? I don't know any programming, but something simple would be fine with me. I tried Google but really didn't have any luck.

---

### Post by _h_ on 2010-03-17
Not sure if there is any. Most text based RPGs are scripted mostly in PHP/MySQL by a single person or a group of developers.

---

### Post by superarthur on 2010-03-17
If it's a simple adventure game, I suppose it's easy to program it with if and else statements.
If you want to add character's status, you can just store things into strings and arrays.

---

### Post by Noraphalem on 2010-03-19
I recommend to use [Python]("http://en.wikipedia.org/wiki/Python_%28programming_language%29"). It should be simple to learn.

Ok some basics:

1. **Save** your plain text **code** into a **.py** file.
2. Run it with following terminal command:

Example:
```
cd </home/<username>/python-example>
python <example.py>
```And an code example:
```
'''
*
* My first python text advanture
*
'''

import readline

def main():
        while (command != "quit"):
                command = raw_input()
                if ( command == "test" ):
                        print "Command test was entered!"
                elif (command == "test2"):
                        print "Command test2 was entered!"
                else:
                        print "Something else was entered!"

main()
```Explanation:

name = "Peter"
Sets the variable "name" to "Peter"
IS

name == "Peter"
Compares the variable "name" with the string "Peter"
IS EQUAL

name != "Peter"
Compares the variable "name" with the string "Peter"
IS NOT EQUAL

Use raw_input() instead of input()! Input() reads a line given back from the player and parse that with the Python interpreter.

I hope I have nothing fogotten. :D

---

### Post by Nevon on 2010-03-19
I'd agree with the person above me. Python would work quite well for what you want to do, and it would be a fairly easy and fun introduction to programming as well. 

If you want something more complete, a friend of mine actually wrote a relatively simple game engine for making text based adventure games. It's written in Python, and you can get it from [Github](http://github.com/kallepersson/stuganengine).

---

### Post by sw40c on 2010-03-19
At one time The Underdogs (Google it) had several resources before the mod couldn't devote more time to the site and it split into three or four separate resources.  They did have links to projects with linux ports and DOS apps which ran well in wine that would fit your bill.  Of course Python would be the way to go, especially if you're aiming for an ASCII RPG like Net Hack, but if you don't want to learn a language check out these resources:

[http://en.wikipedia.org/wiki/Interactive_fiction#Development_systems](http://en.wikipedia.org/wiki/Interactive_fiction#Development_systems)
[http://www.duke.edu/~srg3/IFAuthorship.html](http://www.duke.edu/~srg3/IFAuthorship.html)

---

### Post by Stigmata13 on 2010-03-20
Thanks guys. I've been thinking about giving python a try, I'll be sure to check that out :D

---

### Post by _h_ on 2010-03-20
> **Stigmata13 said:**
> Thanks guys. I've been thinking about giving python a try, I'll be sure to check that out :D

Good luck. :D

---

