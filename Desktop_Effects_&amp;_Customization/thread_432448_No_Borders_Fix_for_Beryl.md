---
title: "No Borders Fix for Beryl"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by slambrick on 2007-05-04
I have Feisty installed witht the latest Nvidia drivers installed. After installing Beryl I could not get the Window borders to display at all. I read a lot of Forum info but no fixs. Here is Mine.
Under the Beryl Icon choose **Advanced Beryl Options** and then **Rendering Path**. Change from **Automatic** to **Copy** and Voila my window Borders have returned. I can now see all the theme treatments I was expecting from the start.
Hope this helps.
:popcorn:

---

### Post by Pox on 2007-05-04
Could be that your video card has trouble with the new Texture-From-Pixmap rendering path - to people who use Copy, beware that it is storing textures in RAM and is significantly slower than TFP rendering.

---

### Post by willg on 2007-05-12
This was posted in another forum and worked for me:

sudo nvidia-xconfig --add-argb-glx-visuals

Then restart X and you should have borders.

---

