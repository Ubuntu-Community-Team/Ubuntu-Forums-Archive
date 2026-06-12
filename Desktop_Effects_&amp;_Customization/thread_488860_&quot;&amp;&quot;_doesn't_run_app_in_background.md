---
title: "&quot;&amp;&quot; doesn't run app in background"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by LouisvilleLIP on 2007-06-30
I'm a noob, I'm using feisty/gnome, and there are a multitude of things I don't know, just to get that out of the way.

If I run "conky &" or "compiz --replace &", then close the terminal window, it closes the app.  How can I run these from terminal (not alt-f2) and get them to stay running if I close the terminal?

Bonus points:  I updated compiz fusion 2 or 3 days ago.  It broke my cube, and just about everything else related to compiz.  I've removed and re-installed everything, but still no cube?  Any thoughts?

---

### Post by mannheim on 2007-06-30
One way to do this is to type, e.g, 
```
(exec conky &)
```
You need those parentheses. This will run conky in the background and allow you to close the terminal. You can also make a script: create a file called "run-conky", make it executable with "chmod +x run-conky" and put it somewhere on your path. The script could contain just:

```

#!/bin/sh
exec conky &

```

Then you can launch conky from the terminal by typing run-conky and it will keep running when the terminal is closed.

---

### Post by hyperair on 2007-07-01
You don't need all that fancy stuff. Just run the command as you have done before:
```

conky &

```

Then to close it, don't press the X button. Type "exit" without quotes, and press enter.

---

