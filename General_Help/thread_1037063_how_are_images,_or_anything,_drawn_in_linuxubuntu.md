---
title: "how are images, or anything, drawn in linux/ubuntu?"
date: 2009-01-11
forum: General Help
---

### Post by uschxc on 2009-01-11
i know its a terribly vague, broad question, but i'm basically just wondering is anything drawn using an equation instead of specific data ie vector graphics?

---

### Post by mcduck on 2009-01-11
Sure, great bunch of apps and toolkits use vector graphics.

Many GTK engines (GTK is the toolkit used to draw application widgtes like buttos etc. in Gnome) use vector graphics, Screenlets & AWN use vector graphics, font rendering is pretty much vector graphics if you use TrueType (or similiar) fonts, just to give a couple of examples.

Also you can use SVG images for lots of things in Gnome, icons, desktop and panel backgrounds, although they are not always freely scalable.

So the answer is yes, just like any modern OS, Linux and it's desktop environments and applications use vector graphics for some things and bitmap graphics for others.

If you are thinking about something like Quartz on Mac platform, we have Cairo: [http://en.wikipedia.org/wiki/Cairo_(graphics)]("http://en.wikipedia.org/wiki/Cairo_(graphics)").

And, in the end, all 3D graphics are made with vectors. Maybe not what you asked, but since the question is quite broad indeed I though it should be mentioned.. ;)

---

### Post by uschxc on 2009-01-11
i guess i'm wondering would it be possible to base an os's gui around vector graphics since there is an inherent performance advantage

---

### Post by mcduck on 2009-01-11
Sure it is, and that seems to be the way all operating systems are heading now.

The desktop in Amiga OS 4.1 is completely made with Cairo, so there you have a nice example of OS with fully vector-based UI.
[http://en.wikipedia.org/wiki/AmigaOS_4]("http://en.wikipedia.org/wiki/AmigaOS_4")

---

