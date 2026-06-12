---
title: "Transparent window movement and resizing How?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by lisux on 2005-10-26
Hi all.
How i can enable the transparent window resizing and moving.
I don't want to use the opaque default model because it delay the window redraws every time a move a window.
Almost all window managers support transparent window moving and resizung, how i can enable it in ubuntu 5.10 for metacity?

Thanks

---

### Post by jrib on 2005-10-26
I wanted to do the same thing.  The only solution I have found (which i don't like) is to  enable "reduced resources".

> If true, metacity will give the user less feedback and less sense of "direct manipulation", by using wireframes, avoiding animations, or other means. This is a significant reduction in usability for many users, but may allow legacy applications and terminal servers to function when they would otherwise be impractical. However, the wireframe feature is disabled when accessibility is on to avoid weird desktop breakages. 

If you want to use it, start up gconf-editor and change /apps/metacity/general/reduced_resources to true

---

### Post by lisux on 2005-10-26
Thanks jason, is a solution.
But i think that i prefer a more configurable window manager that metacity.

---

