---
title: "LaTeX font installation trouble: pdfTeX error (\pdfmapfile)"
date: 2008-12-14
forum: General Help
---

### Post by floydian_slip on 2008-12-14
Hello everyone,

I'm trying to install the Garamond font for use with LaTex from [this]("http://gael-varoquaux.info/computers/garamond/index.html") site. I extracted all files from the package and placed them into their proper folders by their extensions (creating new folders when necessary), according to the readme and some other sites. So everything should be in its place.

When I try to run the tex command on a file containing garamond, I get the following error:

```
! pdfTeX error (\pdfmapfile): not allowed in DVI mode (\pdfoutput <= 0).
l.7 \pdfmapfile
               {=ugm.map}

```

I'm not sure how to solve this. Is there a problem with the .map file? By the way, I ran texhash and updated the map with:

```
updmap --enable Map=ugm.map
```

with no problems.

Any ideas? Thanks in advance. :)

---

### Post by floydian_slip on 2008-12-23
Anyone? Ideas?

---

### Post by hugmenot on 2008-12-23
Did you try pdfTeX instead of dvi-based latex?

---

### Post by TeXtonyx on 2008-12-23
> **floydian_slip said:**
> Anyone? Ideas?

This post was about installing Japanes fonts.

"Just unpack it to your texmf (or, safer, localtexmf), and refresh your LaTeX filename data base (e.g. under Unix by running texhash, or with MixTeX by starting MikTeX options and clicking on the "refresh file name database" button)." 

Did you update the data base after installing the font package?
You didn't mention doing this step, I'm not current with LaTeX.

---

