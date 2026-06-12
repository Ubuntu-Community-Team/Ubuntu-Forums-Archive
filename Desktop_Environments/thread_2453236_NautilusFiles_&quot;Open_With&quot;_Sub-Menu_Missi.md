---
title: "Nautilus/Files &quot;Open With&quot; Sub-Menu Missing After 20.04.1 Upgrade - How to Re-Enable?"
date: 2020-11-05
forum: Desktop Environments
---

### Post by OzzyFrank on 2020-11-05
OK, I give up - I've looked everywhere, but cannot find an answer to this, so request your help. I upgraded 2 LTS releases from 16.04 to 20.04.1, and one of the things I noticed was missing or disabled was the "Open With" sub-menu in the right-click context-menu in Nautilus/Files. Now, I've been using Ubuntu since 2006, so have seen this happen before after upgrades, and either it would reappear once I used "Open With Other Application", or the next big update to Nautilus would see it back. However, I can't get it back, and since this LTS is now 20.04.1, I'm guessing this won't be resolved without a hack of sorts. Now I am used to tinkering with config files and whatnot, so if you have a way to re-enable this useful feature, please let me know.

I know clicking "Open With Other Application" and then an app in the popup isn't a huge deal, but it is slower, and annoying considering for 14 years I've used "Open With" several times a day. So your help would be greatly appreciated. But please: do not mention Nautilus Actions (now FileManager-Actions) - I am aware of this, have used it before (only to have "Open With" come back not long after I made a bunch of actions), and have installed it again (all my previous actions have been discarded, unfortunately, and I'd rather not go to the time and effort if I don't need to). Many thanks in advance, and stay safe, guys!

---

### Post by vanadium on 2020-11-08
Not sure if I understand correctly, but for files that have their association correctly set, the first entry in the right-click menu should be the "Open with <associated application>". Then there is an "Open with other application" menu item, that allows you to open that file with other selected applications.

To set /check the association, select "Properties" in the right-click menu. The "Open with" tab allows you to set the "Default application" and the "Recommended applications". You can remove a "Recommended application" when you right-click. With the button, you can set another application as "Default". The changes here will reflect in the right-click menu of each file of the same file type.

---

### Post by OzzyFrank on 2020-11-10
> **vanadium said:**
> Not sure if I understand correctly, but for files that have their association correctly set, the first entry in the right-click menu should be the "Open with <associated application>". Then there is an "Open with other application" menu item, that allows you to open that file with other selected applications.

Hi, and thanks - but as I said, I am aware of the "Open With Other Application" option in the context menu. What I am referring to is the "[COLOR=#0000ff]**Open With >**[/COLOR]" [COLOR=#ff0000]**_SUB-MENU_**[/COLOR] that used to be in that context menu along with "Open With Other Application". I mean, this has been a feature of Nautilus for aeons - at least since 2006 when I first switched to Ubuntu, and pretty sure Windows still has it too. I'm surprised you don't know what I am talking about, as that feature has been around since forever. With it you could quickly choose something other than the default app - every program you'd ever used to open that filetype with would be listed there. In other words, straight after using "Open With Other Application" to open a filetype in a program, it would appear there. For example. for .jpg images the default is Image Viewer, but you could right-click it and Open With > Gimp. Now you have to click "Open With Other Application", find Gimp in the list in the dialogue box, select it and click OK.

Just so there's no confusion about what I mean about the sub-menu, while I don't have a screenshot of that former feature, here is one of the FileManager-Actions one I've created (while basically the same thing, I had to create these, and all entries are static, while the Open With sub-menu would have completely different apps in it depending on what type of file you clicked):

[ATTACH=CONFIG]287328[/ATTACH]

---

### Post by vanadium on 2020-11-10
There is an image of what you are referring to here: [https://askubuntu.com/questions/115591/how-can-i-remove-change-the-open-with-list](https://askubuntu.com/questions/115591/how-can-i-remove-change-the-open-with-list). That submenu was replaced by the "Select Application" dialog ("Open with other application") quite a few versions ago. You can have that dialog permanently populated with alternative applications, like Gimp for a jpeg, as I indicated before.

---

### Post by OzzyFrank on 2020-11-10
Yet another useful feature Gnome and/or Nautilus developers got rid of? Well, I can't pretend to understand their logic. And yes, I understand you can get to all those other options via "Open With Other Application", but my point is I shouldn't need to be opening a dialogue box and scrolling and clicking multiple times. Right-click, move mouse into **Open With** sub-menu, and one click to open that file with desired program. Simple. I truly can't fathom why they would remove it. Since that is still a feature of other file managers like Nemo, if anyone knows a hack or whatever for Nautilus, let me know.

---

