---
title: "How can I add images to a Community Help wiki page?"
date: 2017-03-14
forum: Documentation and Community Wiki Discussions
---

### Post by Paddy Landau on 2017-03-14
I'm writing a how-to on the [Community Help wiki]("https://help.ubuntu.com/community").

The Wiki help on [Moin syntax]("https://wiki.ubuntu.com/HelpOnMoinWikiSyntax") mentions drawings, and points to [help on drawings]("https://wiki.ubuntu.com/HelpOnDrawings").

Unfortunately, the help is obscure. It gives the syntax for including an image, but absolutely no instructions as to how to get the drawing into the page in the first place.
[LIST]
[*]I know that I need a tar of the drawing, which somehow must get onto the Wiki — but how?
[*][s]It recommends AnyWikiDraw as a drawing tool, but apparently it has been discontinued. Anyway, the installation instructions are non-existent and, as far as I can tell, I need to install it on a server with a wiki, not on my computer! The only alternatives to AnyWikiDraw that I've found are also for wiki servers.[/s]
[/LIST]
Are you able to help me to (1) understand how to create a drawing in the right format [s]and (2) how to put the drawing onto the Wiki[/s]?

**EDIT:** I've managed to figure out how to add the drawings. I just need to understand the format of the file.

**EDIT:** It's absolutely bizarre. I have created a [FONT=lucida console]tar[/FONT] file, with the extension [FONT=lucida console].adraw[/FONT], containing a sample PNG image. If I name the file [FONT=lucida console]testdraw.adraw[/FONT], it works. But if I rename the file to either [FONT=lucida console]testdraw.tar[/FONT] or [FONT=lucida console]silver.adraw[/FONT], it doesn't work. I am flummoxed. It also seems to be a requirement that the contained file is called "drawing", e.g. [FONT=lucida console]drawing.png[/FONT].

Thank you.

---

### Post by Paddy Landau on 2017-03-14
Phew! I finally figured out a way.

It doesn't have the advertised functionality of *adraw*, but that's OK, because I don't need fancy image functions.

Method:
[LIST=1]
[*]Create an image however you require.
[*]Name the image "drawing", e.g. [FONT=lucida console]drawing.png[/FONT].
[*]Create a tar (any name) containing just the image.
[*]Give the tar the extension "tdraw", e.g. [FONT=lucida console]explanation.tdraw[/FONT].
[/LIST]

---

### Post by sudodus on 2017-03-14
Am I understanding your question correctly?

This is how I add an image to an Ubuntu help or wiki page:

1. Upload the image as an attached file.

2. Refer to the file with the following syntax (modified according to the relative location). Notice that '/artwork' corresponds to 'artwork' or './artwork' in bash (for subpages / directories) but not for the images / files themselves.

```
{{attachment:/artwork/mkusb128.png}}
```

as you can see at the beginning of [this link](https://help.ubuntu.com/community/mkusb) if you look at the raw text.

It is a good idea to 'borrow' syntax from another wiki page that does something that you want to do (if you are lucky enough to find one, otherwise, just ask us ...).

---

### Post by Paddy Landau on 2017-03-14
> **sudodus said:**
> ```
{{attachment:/artwork/mkusb128.png}}
```
Oh my goodness, that is so much easier than the documented method!

Thank you!

---

