---
title: "Sickening out-of-the-box features"
date: 2012-10-28
forum: Desktop Environments
---

### Post by PPamaterasu on 2012-10-28
More than Kubuntu, this is a KDE statement. These two things are greatly anyoning:


**First**: Grey text of minimized windows. No matter what theme I use, no matter the colors I change, no matter what I do. It remains furiously grey. The text is almost unviewable
[IMG]http://img441.imageshack.us/img441/6533/textogris.png[/IMG]


**Second:** The panel taskbars are incredibly large
[IMG]http://img210.imageshack.us/img210/7613/largebar.png[/IMG]

Upper one: Xfce4-panel
Down: the panel of KDE

If there is no way the change this graphically, there must be a way to change this the hard way: Edit text configuration files.

**Please, help me. I need to change this. I don't want to sacrifice KDE and Kubuntu for those uncomfortable statements.**

---

### Post by vasa1 on 2012-10-28
> **PPamaterasu said:**
> ...
**First**: Grey text of minimized windows. No matter what theme I use, no matter the colors I change, no matter what I do. It remains furiously grey. The text is almost unviewable
[IMG]http://img441.imageshack.us/img441/6533/textogris.png[/IMG]
...
Are you referring to the tab on the right? The tab that has "acelerar kde"?
I'm assuming that's the "selected="true"" tab, the one in "focus".

In any case, rather than wait for people to fix things, you could do so yourself by making a "style" using the Stylish extension or by modifying userChrome.css.

The relevant code is this (IMO, because it worked for me for past versions of Firefox and works for Fx 17):
```
.tabbrowser-tab[selected="true"] {color: #a2e5fb !important; font-weight: bold !important }
.tabbrowser-tab:not([selected="true"]) { color: #444 !important }

```

Note that you can also fix the background color to anything you want.

If you are interested in such an approach but don't know how to proceed just ask and someone or I will provide details.

Just to give you an example, here are two Firefox tabs, the Ubuntu Forums one is inactive:

---

### Post by TenPlus1 on 2012-10-29
So basically the only problems you have with Kubuntu is that the unfocused window text on your taskbar is grey and that the tastbar buttons are too long ???

Your first problem can be easily fixed by going into Kcontrol -> Appearance & Themes -> Colours and changing the theme palette to suit yourself (Inactive Task Text Colour)...

As for the width of the task buttons on the taskbar, those will shrink to fit any amount of programs you run so the width isn't really an issue but an asthetic preference that I'm not sure how to change...

---

### Post by bra|10n on 2012-10-29
> **PPamaterasu said:**
> More than Kubuntu, this is a KDE statement. These two things are greatly anyoning:


**First**: Grey text of minimized windows. No matter what theme I use, no matter the colors I change, no matter what I do. It remains furiously grey. The text is almost unviewable
[IMG]http://img441.imageshack.us/img441/6533/textogris.png[/IMG]

If you are changing plasma themes then the elements of these themes must also be changing. 
You might expand on what colours you've tried changing as I doubt you are changing the right ones...

> **PPamaterasu said:**
>  The panel taskbars are incredibly large
[IMG]http://img210.imageshack.us/img210/7613/largebar.png[/IMG]

Upper one: Xfce4-panel
Down: the panel of KDE

If there is no way the change this graphically, there must be a way to change this the hard way: Edit text configuration files.

The plasma desktop is based on widgets which in most cases resize themselves accordingly. 
To change the panel height, right click and unlock widgets, right click on the panel and choose panel options > panel settings. 
The height adjustment will show in the middle of the panel-options widget.

[B]> **PPamaterasu said:**
> Please, help me. I need to change this. I don't want to sacrifice KDE and Kubuntu for those uncomfortable statements.

[/B]If this is all that's wrong with KDE then I think they're doing very well. If only...

---

### Post by drmrgd on 2012-10-29
Not sure if this is a direction you want to go in, but you could switch to the Icon Only Task Manager instead.  You'll just need to add the widget to your task manager and then configure it as you like.  It looks and works very similarly to the Windows 7 task manager, and I really like it as it's very easy to see what's going on, you don't have to deal with the poor text rendering (which I agree is pretty bad!), and you don't have to worry about the whole task manager being mashed up when there's a lot of open windows.  

See the attached screenshot for an example of what it looks like.  I use this exclusively now on all my KDE boxes, and I love it!

EDIT: added a better screenshot...realized that I didn't have any windows open to show it off!

---

### Post by PPamaterasu on 2012-10-29
> **drmrgd said:**
> Not sure if this is a direction you want to go in, but you could switch to the Icon Only Task Manager instead.  You'll just need to add the widget to your task manager and then configure it as you like.  It looks and works very similarly to the Windows 7 task manager, and I really like it as it's very easy to see what's going on, you don't have to deal with the poor text rendering (which I agree is pretty bad!), and you don't have to worry about the whole task manager being mashed up when there's a lot of open windows.  

See the attached screenshot for an example of what it looks like.  I use this exclusively now on all my KDE boxes, and I love it!

EDIT: added a better screenshot...realized that I didn't have any windows open to show it off!

God Bless You! (even if I don't believe in superheros). I still prefer text, but this is a good, beautiful and uncomplicated way of managing windows.
 
It seems the other solutions can't be resolved, but I will keep trying.

Thank You guys for the help!

---

