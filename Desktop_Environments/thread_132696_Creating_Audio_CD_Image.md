---
title: "Creating Audio CD Image"
date: 2006-02-18
forum: Desktop Environments
---

### Post by schnarff on 2006-02-18
Hello,

I'd like to create a CD image (ISO or whatever other format is appropriate) from a collection of .wav files. I'm not looking to burn directly to a local CD player, but to instead create an image that someone on a remoted Windows system could burn. I've seen comments on the forums that simply using mkisofs to create an image from the .wav files won't help, and that seems to make logical sense; however, all of the solutions involve just burning straight to a disc.

Any help would be much appreciated.

Thank You,
Alex Kirk

---

### Post by Jose Catre-Vandis on 2006-04-13
Bump :-)

I want to do the same thing?

Also the proggie to load this image and allow files to be ripped to mp3?

---

### Post by Ramses de Norre on 2006-04-13
k3b can do that, the problem with using mkisofs is that the files remain .wav and for a cd to be readable by a cd player it must be .cda files.
In k3b make a project, click the burn dialog and uncheck all the boxes under options in the writing tab, you can then select a location in the image tab and click on burn.

---

