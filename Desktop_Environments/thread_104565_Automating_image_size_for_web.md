---
title: "Automating image size for web"
date: 2005-12-16
forum: Desktop Environments
---

### Post by hal pacino on 2005-12-16
Hi all,
I'm a recovering Gentoo user (lol). So I'm new to this forum. I'm creating a webpage and I'm wondering if there's a way to automate shrinking of hi-res images to a smaller size jpg or png. I've already created a template to create webpages, but I just don't want to make dial-up users unduly suffer.

Sorry, if this is posted in the wrong forum.

Thanks for all help.

---

### Post by soulestream on 2005-12-16
use the image tags to modify the size

<p>
An image:
<img src="constr4.gif"
width="144" height="50">
</p>

<p>
A moving image:
<img src="hackanm.gif"
width="48" height="48">
</p>

[http://www.w3schools.com/html/html_images.asp](http://www.w3schools.com/html/html_images.asp)


soule

---

### Post by lcg on 2005-12-16
[QUOTE=hal pacino]I'm creating a webpage and I'm wondering if there's a way to automate shrinking of hi-res images to a smaller size jpg or png.[/QUOTE]
ImageMagick can do that.

[QUOTE=soulestream]use the image tags to modify the size[/QUOTE]
But that does not reduce the amount of data, only the displayed size of an image in the browser. Hal Pacino wanted to be nice to people with slower lines.

HTH,
Lars

---

