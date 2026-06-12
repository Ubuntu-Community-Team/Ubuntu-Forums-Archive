---
title: "Really large font only on UF in Firefox."
date: 2009-10-05
forum: Forum Feedback &amp; Help
---

### Post by Ms_Angel_D on 2009-10-05
I'm going out of my mind with this, I've disabled all firefox plugins, tried a new empty profile with no extensions, and still I get really large font here on the forums. Once I hit refresh it's back to normal, but then I have to do it on every page. This is the only website I have these issues on.

before refresh:
[[img]http://www.ubuntu-pics.de/thumb/26615/screenshot_002_7NgvZf.png[/img]](http://www.ubuntu-pics.de/bild/26615/screenshot_002_7NgvZf.png)

after refresh:
[[img]http://www.ubuntu-pics.de/thumb/26616/screenshot_003_N0Qg81.png[/img]](http://www.ubuntu-pics.de/bild/26616/screenshot_003_N0Qg81.png)


looking at my firefox error console shows errors in the css

```
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 68
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 73
Warning: Expected end of value for property but found '/'.  Error in parsing value for property 'font-size'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 112
Warning: Expected end of value for property but found '/'.  Error in parsing value for property 'font-size'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 122
Warning: Expected end of value for property but found '/'.  Error in parsing value for property 'font-size'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 128
Warning: Expected end of value for property but found '/'.  Error in parsing value for property 'font-size'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 138
Warning: Expected end of value for property but found '/'.  Error in parsing value for property 'font-size'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 146
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 479
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 484
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 501
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 506
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 793
Warning: Error in parsing value for property 'text-decoration'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 798
Warning: Expected color but found '#'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 1023
Warning: Expected color but found '#'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: http://ubuntuforums.org/clientscript/vbulletin_css/style-6a8e21d1-00098.css
Line: 1052
```

Any idea what's going on here?

Angel

---

### Post by Tipped OuT on 2009-10-05
Try CTRL + 0.

---

### Post by Ms_Angel_D on 2009-10-06
Hi tipped thanks, but that does nothing on this end.

---

### Post by LookTJ on 2009-10-06
What addons do you have installed, if any?

---

### Post by Ms_Angel_D on 2009-10-06
Umm I have a ton installed, but as I said in my previous post I tried disabling them and even tried a new blank firefox profile. I'll list them for you though.

[LIST]
[*]Adblock Plus
[*]Add Bookmark Here 2
[*]Add To Search Bar
[*]All-in-One Sidebar
[*]Autopager
[*]Cooliris
[*]Custom Buttons 2
[*]Dom Inspector
[*]Download Statusbar
[*]DownThemAll!
[*]DragnDrop Toolbars
[*]FEBE
[*]FirefoxMenuButtons
[*]Fireman
[*]Firetray
[*]Flashgot
[*]Forecastbar Enhanced
[*]Google Gears
[*]GooglePreview
[*]Grasemonkey
[*]Image Zoom
[*]Novell Moonlight
[*]Old Add Bookmark Behavior
[*]Page Zoom
[*]Prism For Firefox
[*]QuickRestart
[*]Save Image In Folder
[*]ScribeFire
[*]Session Manager
[*]Shareaholic
[*]Show Go!
[*]ShowIP
[*]Splash
[*]Sxipper
[*]Tab Mix Plus
[*]Tab Scope
[*]TinyURL Generator
[*]Tomfox
[*]Toolbar Buttons
[*]Ubuntu Firefox Modifications
[*]United States English Dictionary
[*]User Agent Switcher
[*]Wappalyzer
[*]WOT
[*]Xmarks
[/LIST]

lol I told you it was a lot.

---

### Post by LookTJ on 2009-10-06
Very interesting, that it applies to this site only. Have you tried to see it persists in other browsers?

---

### Post by Viva on 2009-10-06
Are you using firefox 3.5?

---

### Post by Ms_Angel_D on 2009-10-06
Yes actually I'm using chromium at the moment and the site appears fine. I wonder if it has something to do with Kubuntu...:confused:

---

### Post by Ms_Angel_D on 2009-10-06
Well I just created a new profile in firefox and began installing extensions one by one to see which if any were the cause of the issue, it appears Wappalyzer makes the forum appear this way, so I suppose I no longer be using it. I will contact the extension developers and let them know of this problem.

---

### Post by Tipped OuT on 2009-10-06
> **Ms_Angel_D said:**
> Well I just created a new profile in firefox and began installing extensions one by one to see which if any were the cause of the issue, it appears Wappalyzer makes the forum appear this way, so I suppose I no longer be using it. I will contact the extension developers and let them know of this problem.

Glad you fixed your problem (or at least found out the what was causing it).

---

