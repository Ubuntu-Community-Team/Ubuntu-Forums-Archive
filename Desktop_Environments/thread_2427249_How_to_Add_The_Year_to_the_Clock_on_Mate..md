---
title: "How to Add The Year to the Clock on Mate."
date: 2019-09-19
forum: Desktop Environments
---

### Post by #&amp;thj^% on 2019-09-19
Finally I got the year added to the clock with Mate DE.
Good Grief this was a difficult one to figure:
```
sudo apt install dconf-editor
```
Now open it, and navigate to "**org/mate/panel/objects/clock/prefs/format**"
Now change that from "24" or "12" to "**custom**"
Now back in /prefs/ you'll see "custom-format"
There you will need to add your desired layout, example below:
**"%Y-%m-%d, %I:%M"** Now hit apply. And Done.
I've not yet found a good one-liner for the terminal yet.
BTW: Dconf will complain about the key not found, just ignore that.
This has been tested by myself for a week now.

---

### Post by kesetyan on 2019-10-01
Hi  1fallen,

Hopefully you are just the person to help me.

I have posted about my problem in the 'General' forum but seeing your post here, it seems more appropriate to ask you.  I was trying to do a similar reformat of my panel clock, I also wanted to show the year.  However I think I have made a big mistake with the Dconf Editor and can no longer see the clock in **'org/mate/panel/objects/'. ** Dconf had earlier complained about the key not being found and being somewhat naive about dconf, I used the reset option - I presume that's why the clock is no longer listed.  If I undertake a complete removal of Dconf Editor and then install it anew, will it rebuild its files and then be able to show the clock.  I know the relevant 
'**org.mate.panel.applet.clock.gschema.xml**' file exists in **/usr/share/glib-2.0/schemas** and the clock is running normally in the panel so my error only appears to affect the Dconf Editor.

I'd be grateful for any advice you can give.

---

### Post by #&amp;thj^% on 2019-10-01
Why sure I can try to help you. But to be sure this is "Mate" only.
Now open dconf with:
```
dconf-editor
```
navigate to "**org/mate/panel/objects/clock/prefs**/.
First you have to select "format" and change the value to "**custom**".
Next click on the "custom-format" and add the changes you want.
Example of mine:
```
%Y-%m-%d, %I:%M
```
Or a bit more readable:
```
%a %I:%M %m/%d/%Y
```
Apply the change and instantly your Clock should change.
This is what Dconf complains about:
```
** (dconf-editor:412192): WARNING **: 13:45:06.199: night-light-monitor.vala:149: Impossible to get cached property from proxy, night-light mode disabled.

```

---

### Post by kesetyan on 2019-10-02
Hi 1fallen,

Thanks for getting back so quickly.

I do have the Mate desktop.  The problem is I think I've messed up the Dconf Editor so I can no longer navigate to '**org/mate/panel/objects/clock/prefs**/' in the editor.  The first time I tried, Dconf did recognize the file but generated an error message claiming it could not find the key.  I thought I needed to clear the search box and used the 'Reset' facility.  Since then when I undertake a search, as soon as I type in 'org/mate', Dconf generates a message 'not found' or similar.

I wonder if I uninstall and purge Dconf Editor, getting rid of everything associated with it, would it reset itself after reinstallation?

---

### Post by #&amp;thj^% on 2019-10-02
There are a few tools that you'll want to becareful with, and Dconf is one of those. :(
Give this a try: **[COLOR="#FF0000"]Caution! Purged config/data can not be restored by reinstalling the package.[/COLOR]**
```
sudo apt purge --auto-remove dconf-editor
```
and 
```
sudo apt clean
```
Now try to reinstall dconf-editor.
I'm not sure if this will help, but i never type to search in dconf, I use the mouse to navigate to the paths I need.

---

### Post by kesetyan on 2019-10-03
Hi ifallen,

Sorry for the delay getting back.  Since my last post, as I had an image backup of my Lubuntu partition created before I installed the Mate desktop, I decided to revert Lubuntu back to that time.  I then installed the Mate desktop and the Dconf-Editor.  After updating the software, data files and personal settings I checked Dconf-Editot and found it was safely back to its situation before I encountered the problem. However, I still cannot get it to change the panel clock format.

This is what happens when I run Dconf Editor:
It opens normally and I navigate to the panel clock preferences and choose the 'custom' option.  A message appears 'No Schema Found'.  
Clicking the question mark gives this more detailed message: 'No schema available. A schema is what describes the use of a key. If the application that was using the key has been uninstalled, or this key is obsolete, you may want to erase it'.  
Underneath this message is the phrase 'Defined by DConf backend' and underneath that '
Type String' followed by 'Current value  '%a %d %d %Y - %H:%M' ' *(which is the value I require and the one that I used previously with the LXDE desktop panel)*.  
Next the custom value I entered is shown: 
Custom Value '%a %d %b %Y - %H:%M'.
There is no 'Apply' showing for me to try to apply my custom settings.
The clock format actually operating in the panel is '%a %c %b, %H:%M'.

This time, regarding your comments, I have not attempted to reset Dconf-Editor nor erased the key.

I hope you can make sense of all this, I am very grateful for your patience and help.

Cheers.

---

### Post by #&amp;thj^% on 2019-10-03
First you have to select the "format"** (12Hr or 24Hr)** and change the value to "_custom_".
Then add your date this should work with your format. (%a %d %b %Y - %H:%M)

---

### Post by kesetyan on 2019-10-04
Hi ifallen,

Thanks for your continued help.  I understand what you have posted but I still get past the ' No schema found' message that Dconf-Editor generates.  I'm trying to add a png screenshot image attachment which shows what I get after following your instructions.

Cheers.

---

### Post by #&amp;thj^% on 2019-10-04
This really should not be this difficult. And I don't see where you changed the format from <24 hr/12 hr> to **"custom"**. You have to type "_custom_" in place of the 12/24 hr format first then add your Time format.
Then the Apply button is in the bottom right hand corner. Screenshots should be in order below. ;)

---

### Post by kesetyan on 2019-10-04
Hi ifallen,

Your considerable patience with me has at last paid off - the clock format I required is now operating on the panel. Sorry I was such a pain.  DConf-Editor is not the most user-friendly program for a novice - its interface is not exactly intuitive (unless I'm just an elderly thick so and so).  Your use of the series of images was extremely useful and explained things very clearly.  (My Dconf-Editor does not have an 'Apply' button but a tick instead but I soon realized its function).

Thanks so much for your help, you've been a great teacher.

Cheers and regards.

---

### Post by #&amp;thj^% on 2019-10-04
You was no pain at all, your right though DConf-Editor is not the most user-friendly program for a novice. (And at times for Advanced users)
Thanks for the kind words,  happy to hear all is well...Enjoy.

---

