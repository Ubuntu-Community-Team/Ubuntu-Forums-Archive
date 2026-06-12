---
title: "firefox update messed firefox up"
date: 2009-03-06
forum: General Help
---

### Post by nolsen01 on 2009-03-06
I just did an update, a couple of which were updates to firefox.

Now, when I open up firefox or type in a URL directly, it gives me the following error:


> ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0: ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1: ()
2: ()
3: ()
4: epsGetAttr([object Object],alias)
5: ()
6: SRCH_SVC_getEngineByAlias(google.com)
7: getEngineByAlias(google.com)
8: getShortcutOrURI(google.com,[object Object])
9: canonizeUrl([object KeyboardEvent],[object Object])
10: handleURLBarCommand([object KeyboardEvent])
11: anonymous(textentered,[object KeyboardEvent])
12: fireEvent(textentered,[object KeyboardEvent])
13: onTextEntered()


has anybody else had this problem?

---

### Post by gjtoth on 2009-03-06
Not that problem but, it covers my panels (the whole desktop, actually) and the only way I can navigate to another desktop is to right-click on the menu, and go to customize.  This allows the panels to be displayed so I can close it.

---

### Post by JurgenB on 2009-03-06
Yes, this is the exact problem I have. No idea how to fix it yet, removing the profile does not help...:(

---

### Post by undoIT on 2009-03-06
Are you running System > Appearance > Visual Effects with Extra turned on? I have found that when Firefox takes over the whole screen and I can't access the close / minimize buttons, I can fix it by turning Visual Effects to none. Then the top border reappears. Not sure if this is the same issue...

---

### Post by JurgenB on 2009-03-06
Nope, I'm running with visual effects off. (Set to None)
Just did a full re-install of firefox, this seems to fix it. (for now)

---

### Post by nbo10 on 2009-03-06
I had the same problem. A reboot cured the problem. I don't think Firrefox shut down fully the first time

---

### Post by gjtoth on 2009-03-06
> **nbo10 said:**
> I had the same problem. A reboot cured the problem. I don't think Firrefox shut down fully the first time

Reboot did nothing for me. Nor, did setting the visual effects to none.

---

### Post by fooman on 2009-03-06
> **gjtoth said:**
> Not that problem but, it covers my panels (the whole desktop, actually) and the only way I can navigate to another desktop is to right-click on the menu, and go to customize.  This allows the panels to be displayed so I can close it.

try this:

open firefox and press f11 *twice*.  that should get you to a normal size screen.

click the unmaximize button.

close firefox and then reopen firefox.

click the maximize button.

see if that fixes the problem.

---

### Post by gjtoth on 2009-03-06
> **fooman said:**
> try this:

open firefox and press f11 *twice*.  that should get you to a normal size screen.

click the unmaximize button.

close firefox and then reopen firefox.

click the maximize button.

see if that fixes the problem.

Just reinstalled.  THAT fixed the problem.  Thanks for your suggestion.  If it reoccurs, I'll give it a shot.

---

