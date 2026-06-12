---
title: "usplash help"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Kanaric on 2005-11-01
Was reading a guide on how to replace the usplash with another image. My question is how do I change the color pallette and reduce colors to 16 so that the image will work?

---

### Post by poofyhairguy on 2005-11-01
Not the forum for questions so I moved it to the right one.

---

### Post by SilentCacophony on 2005-11-01
Hi. I used an old copy of Paint Shop Pro to do that. It's commercial Windows software, though. It was a matter of manually changing the palette entries, saving the resulting *palette*, then reloading the original image and loading the modified palette into it. The program automatically remaps to the nearest colors available.

The Gimp can reduce images to a limited palette (Image->Mode->Indexed, then select the number of colors,) but it doesn't seem to have some of the tools necessary for effectively manipulating limited palettes.

I've recently looked into the **imagemagick** package a bit, and I think that *may* be able to do palette changing, but I haven't used it yet. It consists of commandline programs, so it's not ideal for people who are more used to GUIs.

---

