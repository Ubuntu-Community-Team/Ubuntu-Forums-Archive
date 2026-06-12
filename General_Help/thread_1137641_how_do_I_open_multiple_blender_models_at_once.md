---
title: "how do I open multiple blender models at once?"
date: 2009-04-25
forum: General Help
---

### Post by Dustin2128 on 2009-04-25
I'm working on a computer animated movie, based around star trek. I found an excellent site for downloading models, they had everything I could ask for and more. So I unzip these models, and test them, they all worked flawlessly. Well, on just about every scene, there are going to be multiple objects. Several I am designing my self, simple things like planets and the badlands. Others, such as ships, have complex models that I just don't have the time to do myself. I opened them all, and they are excellent. How would I, say, open a ship, then open another in the same project. This is very important to me, because there are several battle scenes.

---

### Post by lovinglinux on 2009-04-25
Depends on the model file format, but usually by importing the mesh into the scene.

What is the file extension of the models you are downloading?

Check these links:

[http://www.blender.org/education-help/tutorials/](http://www.blender.org/education-help/tutorials/)
[http://www.blender.org/education-help/video-tutorials/](http://www.blender.org/education-help/video-tutorials/)

---

### Post by Dustin2128 on 2009-04-26
these are .blend files

---

### Post by lovinglinux on 2009-04-26
> **Dustin2128 said:**
> these are .blend files

Then you should use the "Append" feature ("File >>> Append" or "Shift+F1").

---

### Post by Dustin2128 on 2009-04-27
> **lovinglinux said:**
> Then you should use the "Append" feature ("File >>> Append" or "Shift+F1").

Dosen't work, I just get into these menus with mesh, object, scene, and some other stuff when I click on my model.

---

### Post by lovinglinux on 2009-04-27
> **Dustin2128 said:**
> Dosen't work, I just get into these menus with mesh, object, scene, and some other stuff when I click on my model.

It works. That is the correct method, because it won't append everything by default. In your case, you just want to append a mesh, but hard-core developers use this feature to import just what they need form huge blend files with lots of stuff in it. This way they can share objects between blend files without importing entire scenes into the new ones.

---

