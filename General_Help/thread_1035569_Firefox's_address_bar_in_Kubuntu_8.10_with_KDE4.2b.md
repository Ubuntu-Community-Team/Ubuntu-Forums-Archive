---
title: "Firefox's address bar in Kubuntu 8.10 with KDE4.2beta2 acts funny."
date: 2009-01-09
forum: General Help
---

### Post by Armagguedes on 2009-01-09
Hello.

I have just installed Kubuntu 8.04 (KDE3) and then copied my backed up /home into the new partition. Then i updated the thing to 8.10 Intrepid (which converted my KDE3 settings to KDE4) and even then to KDE 4.1.85 (aka 4.2 beta2).

Now when i'm using firefox (3.0.5) - which doesn't even look good because the KDE theme is not in the repos - i can't type anything in the address bar; whenever i want to go to any link i either have to click on my bookmarks (assuming it's there) or punch something into the Google search box and take it from there.

Anyway, whenever i type anything into the address bar this is the error i get in an error message box:[INDENT]Assertion failed:
[INDENT] ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(openoffice.org)
7:getEngineByAlias(openoffice.org)
8:getShortcutOrURI(openoffice.org,[object Object])
9:([object KeyboardEvent])
10:anonymous(textentered,[object KeyboardEvent])
11:fireEvent(textentered,[object KeyboardEvent])
12:onTextEntered()
13:handleEnter(false)
14:onKeyPress([object KeyboardEvent])
15:onxblkeypress([object KeyboardEvent])
[/INDENT] [/INDENT]Any idea?

---

### Post by Armagguedes on 2009-01-09
So i've decided to look for something on Amazon.co.uk.. so i went over to the little bit where you can pick which search engine you want to use and selected Amazon (UK) (which i had previously installed and that got dragged along with my ~ folder backup).

When i actually select it (ie, the droplist disappears and the icon gets replaced), i get this error box some 5 times in a row (new instance shows up every time i press OK):[INDENT]Assertion failed[INDENT]ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:([object Object],85,[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object])
7:SRCH_SVC_getSorted(false)
8:SRCH_SVC_getVisible([object Object])
9:getVisibleEngines([object Object])
10:get_engines()
11:rebuildPopup()
12:observe([xpconnect wrapped nsISupports],browser-search-engine-modified,engine-current)
13:notifyObservers([object Object],browser-search-engine-modified,engine-current)
14:notifyAction([object Object],engine-current)
15:([xpconnect wrapped nsISearchEngine])
16:currentEngine([xpconnect wrapped nsISearchEngine])
17:set_currentEngine([xpconnect wrapped nsISearchEngine])
18:onxblcommand([object XULCommandEvent])
[/INDENT][/INDENT]Also, the new search engine is not actually selected, so i go back to the box... but all the engines are gone! Only the default icon (Google) is left. But when i use it... it returns results in eBay (which i added to the list as well).
Wtf is going on?

---

