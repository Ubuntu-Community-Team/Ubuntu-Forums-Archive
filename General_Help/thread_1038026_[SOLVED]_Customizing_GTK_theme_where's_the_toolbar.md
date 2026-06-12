---
title: "[SOLVED] Customizing GTK theme: where's the toolbar style?"
date: 2009-01-12
forum: General Help
---

### Post by ChrisBookwood on 2009-01-12
Hi,

I'm and customizing a gtk theme for my like, and I was wondering where in the gtkrc file I can find the definition for the toolbar-borders?

[IMG]http://dl.getdropbox.com/u/168187/scrndumb.jpg[/IMG]


I have been looking through the gtkrc file a whole lot of times, searching for 'toolbar', but I can't seem to find it, so I hope some of you guys can!

---

### Post by ChrisBookwood on 2009-01-12
Nobody knows?

---

### Post by ChrisBookwood on 2009-01-12
I'm wondering if the reason that I can't find anything in the gtkrc file, is because it's a standard not defined in the gtkrc file, and I will have to specify something extra in the file, to be able to define the "stripes"...
Any ideas, clues or answers?

---

### Post by IceReaver75 on 2009-01-12
what theme are you trying to customize if I may ask.  I could try to look at the theme contents for you and see what is going on in there if you would like.

---

### Post by ChrisBookwood on 2009-01-12
> **IceReaver75 said:**
> what theme are you trying to customize if I may ask.  I could try to look at the theme contents for you and see what is going on in there if you would like.

I'm customizing the Human theme.
I've found out, that if I make a new style,
```
style "murrina-pixmap-toolbar" = "murrine-dark-toolbar"
{
    engine "pixmap"{
        image {
              function = BOX
              file = "toolbar_o.png"
              border = {1,1,1,1}
          }
    }
}
```
Where toolbar_o.png is a picture I've made to look like the toolbar I want,
And append that style to the toolbar,
```
class "GtkToolbar" style "murrina-pixmap-toolbar" 
```
It actually works!

Now I just need to find out how to not use a picture, but make gtk draw it. I have figured out how to specify the bg color, but I can't get the stripes to go away. If I use a picture, though, they disappears by them self, so that will work for now.

---

### Post by ChrisBookwood on 2009-01-12
Do you know a reference I can use, cause it takes to much time when I have to look through theme-code to figure out how to do what I want to do... ?

---

