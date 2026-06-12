---
title: "What command would paste the current date into the currently focused window?"
date: 2007-04-16
forum: Desktop Environments
---

### Post by motin on 2007-04-16
I wonder how to make a keyboard shortcut that would paste the current date into the currently focused window. Like a cli-version of Sendkeys of VBScript or similar...

It seemed to be a hard issue with Linux as of 2003 at least ([http://twiki.org/cgi-bin/view/Wikilearn/KeyboardMacrosInLinux](http://twiki.org/cgi-bin/view/Wikilearn/KeyboardMacrosInLinux)) but is it still?

---

### Post by hackerssidekick on 2007-04-17
You can assign commands to be run on keypresses in metacity using gconf-editor. You need to tie this to a command that somehow pastes the current date. The latter is the hard part.

Another (similar) approach is to use a program called **xvkbd**, in combination with **xbindkeys**. You can use it to pass keystrokes to the focused window, e.g:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
        release + c:234
```

That code is from my .xbindkeysrc, it sends <Left Alt>-<Left> to the window when I press the back key on my keyboard.

You could use either xbindkeys or metacity to run a script which will grab the current date (using the date command) and then send the text to the window via xvkbd.

Good luck!

---

### Post by motin on 2007-04-17
Thanks! That looks like the most viable solution of all!

However, I cannot get it to work. I have verified that a certain keyboard combination works and assigned the following command to it:

```
#Paste current date
"/usr/bin/xvkbd -xsendevent -text 'test'"
    m:0x14 + c:49
    Control+Mod2 + section 
```

Using this in for example firefox or similar however works only spartially. Cannot figure out why it doesn't work most of the time. 

Have you had any better experiences?

---

### Post by motin on 2007-04-17
It works in Tomboy at least - and that's enough for now. I cannot get it to print a space however...

/usr/bin/xvkbd -xsendevent -text `date +%d-%b-%Y\ %H:%M`
yields "17-apr-2007" only

/usr/bin/xvkbd -xsendevent -text `date +%d-%b-%Y\[SPACE]%H:%M`
yields "17-apr-2007PACE11:25"

/usr/bin/xvkbd -xsendevent -text `date +%d-%b-%Y %H:%M`
just opens xvkbd

No special space-character is defined according to man xvkbd

The closest I can get - and what I use atm - is:
/usr/bin/xvkbd -xsendevent -text `date +%d-%b-%Y\|%H:%M`

---

### Post by hackerssidekick on 2007-04-17
Ok, the problem is that xvkbd is executing the command between the two `. The date command takes in a format string, but if you want spaces in the output you have to pass the string in between two '.

Basically you want this:
```
"/usr/bin/xvkbd -xsendevent -text "`date '+%d-%b-%Y %H:%M'`""
```

Also, I found that some things would only work if I added in the word release, like the example I gave above. YMMV

---

### Post by motin on 2007-04-17
> **hackerssidekick said:**
> Ok, the problem is that xvkbd is executing the command between the two `. The date command takes in a format string, but if you want spaces in the output you have to pass the string in between two '.

Basically you want this:
```
"/usr/bin/xvkbd -xsendevent -text "`date '+%d-%b-%Y %H:%M'`""
```

Also, I found that some things would only work if I added in the word release, like the example I gave above. YMMV

I added the release portion and now it seems to work in Firefox as well and won't bug out in wine apps (albeit not paste it in wine apps yet). 

Still - the space solution with ' doesn't work as nothing after the space is printed out just like before.

---

### Post by hackerssidekick on 2007-04-17
interesting...you copied in the line that I posted exactly? Because it works perfectly for me, in firefox and the terminal.

---

### Post by motin on 2007-04-17
> **hackerssidekick said:**
> interesting...you copied in the line that I posted exactly? Because it works perfectly for me, in firefox and the terminal.

I didn't copy it exactly since I wanted a different key assignment. Now I see the missing quotation marks! Thanks! The space now works. Look: 

Hmmm... no text came up there. I find I can only perform the inclusion of text once for every firefox or thunderbird window... Very strange.

---

