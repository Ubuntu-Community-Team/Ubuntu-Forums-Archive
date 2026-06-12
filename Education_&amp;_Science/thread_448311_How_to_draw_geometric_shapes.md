---
title: "How to draw geometric shapes?"
date: 2007-05-19
forum: Education &amp; Science
---

### Post by Zdravko on 2007-05-19
Hi there!
I search for an application for plotting geometric shapes. Example: I want to draw a circle with center 0,0, radius = 20cm etc. The graph must be exportable into png, jpg, ps, pdf etc.
Thanks!

---

### Post by tweedledee on 2007-05-19
> **Zdravko said:**
> Hi there!
I search for an application for plotting geometric shapes. Example: I want to draw a circle with center 0,0, radius = 20cm etc. The graph must be exportable into png, jpg, ps, pdf etc.
Thanks!

Inkscape can do the drawing part - it's transform features allow for precise control over position and size (among other things) of shapes.  Depending on the precise shapes you have in mind, you may have to build some from lines and create the shape yourself, but that's pretty straightforward as well.  However, it can only save in svg and export to png, though you could print to pdf by setting up a pdf printer.

---

### Post by anoir on 2007-05-19
I use OO.o Draw for little graphs and charts, but if you want to print those figures, then Inkscape seems to be fit for your needs better.

---

### Post by Zdravko on 2007-05-19
Why no one recommended me KIG? It is a fantastic KDE application! I am amazed by its enormous functionality! :)

---

### Post by ricrac on 2007-05-19
drgeo 
Qcad 
Cenon

Or do 2d in 3d app
blender
varkon
geomview

Or with a download java 3d app that does 2d, 
art of illusion - [http://www.artofillusion.org/](http://www.artofillusion.org/)

Or with a download 3d app that does 2d, 
xara extreme - [http://www.xaraxtreme.org/](http://www.xaraxtreme.org/)

Don't forget google Sketchup 3d 
[http://sketchup.google.com/download.html](http://sketchup.google.com/download.html)
Runs in wine, but better using vmware or xen and windows
Post models to google maps and google earth.
Obtain models from the [http://sketchup.google.com/3dwarehouse/](http://sketchup.google.com/3dwarehouse/)
Set lat/long and compass alignment, time of day, and calculate where shadows will fall on your garden from the new addition to your house you want to build.


Many other including code/math oriented but I think these are the better interactive available.

---

### Post by Zdravko on 2007-05-20
Okay, thanks for the suggestions. I will currently stick to Kiq. Then, if I want a professional scientific article-like graphics, I will ask again in this topic :)

---

### Post by Zdravko on 2008-02-23
Now I use Fedora, but with YumEx I can't find Kig! Help! I need this great application! It is fantastic! But I can't find it in Fedora!
What to do?

---

### Post by Zdravko on 2008-02-23
I found a kdeedu package that contains kig. Unfortunately I will have to download several hundreds useless stuff with it... :(

---

### Post by PeterP24 on 2008-03-09
You could try matlab or similar. For the circle you could use the following code :

> t = linspace(0,2*pi,100);
r = 20;                                       % the ray
x = r*cos(t);                              % the parametric approach with t as parameter
y = r*sin(t);
axis square;
hold on
plot (x,y);

The resulting figure can be formated to contain grid, etc. and it can be exported in a bmp or jpeg file to be embedded in a nice looking homework. With some basic knowledge of mathematics one can plot complex geometric figures either 2D or 3D.

Best regards

Peter

---

### Post by Zdravko on 2008-12-24
I just found out that there is no Windows version of Kiq! What to do? Can you recommend me a suitable replacement? Help!

---

### Post by waspbr on 2008-12-24
if you are still looking in ubuntu, there is this program called scilab, which is a matematical environment much like matlab. 

additionally there's QCAD, that is very much a CAD software. Also there's gmsh ... you can get all these by searching in synaptic

---

### Post by Zdravko on 2008-12-24
I don't have Ubuntu now. I use Windows.

---

### Post by Zdravko on 2008-12-24
I just found what I was looking for - GeoGebra. This tool is very similar to Kig, but has a Windows version instead!

---

### Post by hrod beraht on 2008-12-24
[[COLOR="Blue"]Inkscape[/COLOR]]("http://www.inkscape.org/")

---

