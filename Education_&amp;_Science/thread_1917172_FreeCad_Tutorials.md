---
title: "FreeCad Tutorials"
date: 2012-01-29
forum: Education &amp; Science
---

### Post by TFroehlich3 on 2012-01-29
Hello Everyone,
I am looking for a tutorial to learn how to design a house with FreeCad. I have installed the software <sudo apt-get install freecad> and now just looking to find a tutorial to learn how to design a house. Does anyone know of any good ones? I can't seem to find any.. Or perhaps is there a better CAD program for this application?

---

### Post by Gemnoc on 2012-02-09
Hello,

First of all the FreeCAD version in Ubuntu 11.10's repositories is rather old. The v0.11.4446 package is almost one year old, and FreeCAD benefits from fast development: v0.12 was released in mid-December and brings a lot of new features.

There is no v0.12 package available (only a source tarball), but the FreeCAD project has two PPA repositories based on the development branch which is now at v0.13. One updates daily, the other whenever I think of updating it, about every 4-6 weeks. (I'm not a developer but I help maintain the PPA)

For more info on how to add the PPA and update your version of FreeCAD, you can check out the FreeCAD wiki:

[https://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Download#Ubuntu_PPA_packages](https://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Download#Ubuntu_PPA_packages)

There is currently an Arch module in development, to allow building of architectural components, but I'm not sure it's entirely usable yet. There is no detailed tutorial on how to build such complex models as houses. You have to keep in mind small open source projects don't have a lot of manpower. FreeCAD does not benefit from as large a user base as Blender. But I recommend you register on the [FreeCAD forums]("https://sourceforge.net/apps/phpbb/free-cad/index.php") and ask questions, we're not many but people are helpful and even the developers answer questions.

FreeCAD may currently not be the best choice to model a house, but to be honest there are not many choices on Linux. It can do it though, but if you have no 3D CAD experience you're looking at a steep learning curve. At least the GUI is pretty easy to figure out. I once tried a demo of Cycas, it's a commercial architectural software, but I couldn't make sense of its odd GUI.

But what is your intended use? Do you want to do it just for fun? Or does the model need to be realistic in every detail? Do you need to get 2D views on paper?

For a simple program, free but not open source, you could have a look at Google SketchUp. There is no Linux version, but the Windows version installs and works fine with Wine, with only minor glitches.

---

