---
title: "Progess Bar"
date: 2008-12-21
forum: General Help
---

### Post by Ghoztrider on 2008-12-21
So I currently have the candy cane type progress bar. How do I set it to something else? I tried System > Preferences > QT 4 settings, but that doesn't seem to work.

---

### Post by Wartender on 2008-12-21
ummm... i'm not sure what progress bar you are referring to... screenshot maybe?

---

### Post by Ghoztrider on 2008-12-22
Any progress bar that shows up really. here's an example.

---

### Post by Wartender on 2008-12-23
ooooooh i see... huh... never tried to change that, sorry, don't know

---

### Post by Ivo Moelans on 2008-12-23
In Gnome the progress bar is defined by the theme you're using. At first sight this candy progress bar is the standard of the theme engine. The progress bar *can* be made to look different, but it is very difficult to say something about it without knowing which theme you are using and into what you want to change it.
I suggest you try out a few themes from [http://www.gnome-look.org/]("http://www.gnome-look.org/"). When (if) you find a progress bar you like maybe you will like the whole theme. If not:
a combination of a certain theme and a progress bar of another theme is possible, but in that case it is better if you could give the names of the themes.

---

### Post by Ghoztrider on 2008-12-26
I am using the moomex theme and I love everything about this theme except the progress bar. I have been messing around with the themes a bit and was hoping I could just change the style of the progress bars and keep the rest intact.

---

### Post by Ivo Moelans on 2008-12-26
1) Open the file */home/<username>/.themes/Moomex/gtk-2.0/gtkrc* with Text Editor. Go to line 520, where it says *style "clearlooks-progressbar"* followed by two lines with on each a curly bracket. Replace these three lines with:

```
style "clearlooks-progressbar"
{
engine "nodoka"
  {
  }
}
```

This only works if you have the *nodoka* engine installed. You can check which engines you have in */usr/share/gtk-engines*. If you don't have nodoka, download it with *Synaptic Package Manager*.
Of course you can try other engines by typing their name between the "" on the third line.

2) It is also possible to 'borrow' the progress bar (or other widgets) from another theme, although this is a little bit more complicated.

Hope this helps.

---

