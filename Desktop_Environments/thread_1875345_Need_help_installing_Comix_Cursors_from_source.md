---
title: "Need help installing Comix Cursors from source"
date: 2011-11-04
forum: Desktop Environments
---

### Post by MountainX on 2011-11-04
I'm using Ubuntu 10.10 and I want to install [Comix Cursors]("http://gnome-look.org/content/show.php/ComixCursors?content=32627").
The repo has version 0.6.1. I want the latest version 0.7.3.

I have both ImageMagick and librsvg installed.

The next step in the install process is to run ./bin/build-cursors. When I do that, I get a bunch of output like this. At first I thought it was an imagemagick problem, so I used synaptic to reinstall that. But I still get the same errors. Here's a random sample:

```
mogrify: unable to open image `build/s-resize.RightHanded.48.#000000.0.7.shadow.png':  @ error/blob.c/OpenBlob/2498.
mogrify: unable to open file `build/s-resize.RightHanded.48.#000000.0.7.shadow.png' @ error/png.c/ReadPNGImage/3072.
mogrify: unable to open image `build/s-resize.RightHanded.48.#000000.0.7.shadow.png':  @ error/blob.c/OpenBlob/2498.
mogrify: unable to open file `build/s-resize.RightHanded.48.#000000.0.7.shadow.png' @ error/png.c/ReadPNGImage/3072.
convert: unable to open image `build/s-resize.bare.png':  @ error/blob.c/OpenBlob/2498.
convert: unable to open file `build/s-resize.bare.png' @ error/png.c/ReadPNGImage/3072.
convert: missing an image filename `build/s-resize.bare.png' @ error/convert.c/ConvertImageCommand/2970.
composite: unable to open image `build/s-resize.bare.png':  @ error/blob.c/OpenBlob/2498.
composite: unable to open file `build/s-resize.bare.png' @ error/png.c/ReadPNGImage/3072.
composite: unable to open image `build/s-resize.RightHanded.48.#000000.0.7.shadow.png':  @ error/blob.c/OpenBlob/2498.
composite: unable to open file `build/s-resize.RightHanded.48.#000000.0.7.shadow.png' @ error/png.c/ReadPNGImage/3072.
composite: missing an image filename `build/s-resize.png' @ error/composite.c/CompositeImageCommand/1607.

```

---

### Post by MountainX on 2011-11-30
any suggestions?

---

