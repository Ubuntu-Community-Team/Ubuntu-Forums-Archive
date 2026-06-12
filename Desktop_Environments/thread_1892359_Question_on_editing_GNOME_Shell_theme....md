---
title: "Question on editing GNOME Shell theme..."
date: 2011-12-07
forum: Desktop Environments
---

### Post by moorhead98 on 2011-12-07
I know nothing about CSS, but with a little help, I managed  to make the activites button in Shell to display the ubuntu icon. It's  great, works good with most all themes. 



  [IMG]http://i.stack.imgur.com/44z8r.png[/IMG] 
  

Except for one part. There is a small gap between the Ubuntu Icon and  the icon for the current application (left of the mouse in the second  picture). 



  [IMG]http://i.stack.imgur.com/AJsYU.png[/IMG]
  

I know that it wouldn't bother anyone besides me, but when it comes  to my desktop I have OCD and need to find a way to get that gap smaller.  Is there any way to get the small little area even smaller? Any number I  can edit in the CSS file? I use the icon on Zukiwito-Shell and Faience shell themes, but I believe  my problem would be the same with just stock default theme.
The line I add is the one highlighted in this pic (I manually add image.png in the folder of the theme)


  [IMG]http://i.stack.imgur.com/PARqU.png[/IMG]
  

Any ideas?

---

### Post by cbowman57 on 2011-12-07
Are you trying to learn how to code .css?

Just wondering if there was a reason you don't use the extension that can do this.

---

### Post by moorhead98 on 2011-12-08
I'm not trying to learn how, I'm just trying to edit it so that the little area can be shortened.

---

### Post by cbowman57 on 2011-12-08
Ok, cool, but after the next shell update you might want to use that extension. :)

*just to clarify, I wasn't real quick to understand what moorhead98 was trying to do so this comment is useless.

---

### Post by moorhead98 on 2011-12-08
Let me re-phrase the question to everybody -- where in any gnome shell css file is the code that controls the size of the section listing the current application? I believe that is what I need to edit

---

### Post by cbowman57 on 2011-12-08
> **moorhead98 said:**
> Let me re-phrase the question to everybody -- where in any gnome shell css file is the code that controls the size of the section listing the current application? I believe that is what I need to edit

 The app menu or the active window in the panel?

If you could snap a pic of the thing you want to change I might be able to help.

You're editing the actual shell or the gnome-shell.css for the theme?

---

### Post by moorhead98 on 2011-12-08
> **cbowman57 said:**
> The app menu or the active window in the panel?

If you could snap a pic of the thing you want to change I might be able to help.

You're editing the actual shell or the gnome-shell.css for the theme?

Look at the attached pic.  I believe just editing a theme would work, not the shell

---

### Post by cbowman57 on 2011-12-08
> **moorhead98 said:**
> Look at the attached pic.  I believe just editing a theme would work, not the shell

You would be correct sir. :)

```
#panelLeft, #panelCenter {
    spacing: 2px;  <<-- right there
}
```Oh, default is usually 4px, it's 2px here because I was trying to verify the change.  Not sure if this will cause a shift somewhere else in the panel or not probably not.

If it does it looks like it could be broken into two entries, i.e.

```
#panelLeft {
spacing: 2px;
}

#panelCenter {
    spacing: 4px; 
}
``` but I haven't verified that.  (Might break things)

---

### Post by moorhead98 on 2011-12-08
> **cbowman57 said:**
> You would be correct sir. :)

```
#panelLeft, #panelCenter {
    spacing: 2px;  <<-- right there
}
```Oh, default is usually 4px, it's 2px here because I was trying to verify the change.  Not sure if this will cause a shift somewhere else in the panel or not probably not.

If it does it looks like it could be broken into two entries, i.e.

```
#panelLeft {
spacing: 2px;
}

#panelCenter {
    spacing: 4px; 
}
``` but I haven't verified that.  (Might break things)

Well,  it worked to some extent. It limited the space between the two buttons, but on the right button it didn't remove the padding? Any way to lessen that? or is that going into the shell itself?
But thanks for that little fix, its better than nothing :)

---

### Post by cbowman57 on 2011-12-08
> **moorhead98 said:**
> Well,  it worked to some extent. It limited the space between the two buttons, but on the right button it didn't remove the padding? Any way to lessen that? or is that going into the shell itself?
But thanks for that little fix, its better than nothing :)

I must be extra slow today, please point me exactly to the location of the right button so we're on the same sheet of music.

If it's what I think you mean you want to look here:

```
.panel-button {
    -natural-hpadding: 2px;
    -minimum-hpadding: 2px;
```It looks something  like this:

[ATTACH]208755[/ATTACH]

This example displays the effect along with a few other extensions, each spaced to maintain some consistency.

---

### Post by moorhead98 on 2011-12-08
> **cbowman57 said:**
> I must be extra slow today, please point me exactly to the location of the right button so we're on the same sheet of music.

If it's what I think you mean you want to look here:

```
.panel-button {
    -natural-hpadding: 2px;
    -minimum-hpadding: 2px;
```It looks something  like this:

[ATTACH]208755[/ATTACH]

This example displays the effect along with a few other extensions, each spaced to maintain some consistency.

Here, this should explain. Look at the area circled in the picture. How do I shrink that area so that it is lesser than that?

---

### Post by cbowman57 on 2011-12-08
I'm sure there is a way but I wasn't able to find it.  Mine moved left with the example I used but I use the window list extension.

---

