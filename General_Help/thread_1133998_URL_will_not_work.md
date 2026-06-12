---
title: "URL will not work"
date: 2009-04-23
forum: General Help
---

### Post by TurtleKush on 2009-04-23
all of a sudden for some reason every time i enter an address into my url i get this 

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(youtube.com)
7:getEngineByAlias(youtube.com)
8:getShortcutOrURI(youtube.com,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])


anyone know why?

---

### Post by kanikilu on 2009-04-23
If you put that error in code tags, it will be a lot easier to read ;)

Also, what browser are you using? If Firefox, do you have any extensions? Try Firefox in safe mode, from a terminal run the following: ```
firefox -safe-mode
```

---

