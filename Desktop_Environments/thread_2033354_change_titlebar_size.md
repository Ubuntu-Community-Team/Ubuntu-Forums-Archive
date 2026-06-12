---
title: "change titlebar size"
date: 2012-07-26
forum: Desktop Environments
---

### Post by beboylips on 2012-07-26
Hello Community,

I have a question: is it possible to change the title bar size to make it less wide? 
I find that the default title bar size is too large and takes too much space on my laptop screen.

By title bar I mean this:
[IMG]http://imgur.com/40RJT[/IMG][IMG]http://i.imgur.com/40RJT.jpg[/IMG]

I'm using Unity with Mac OS Lion theme. I'm running Ubuntu 12.04 64-bit.

Thank you in advance,
Beboy

---

### Post by beboylips on 2012-07-26
Found it!!

You have to edit the .xml config file for metacity in the theme folder.

For any theme, navigate into /usr/share/themes/<name of theme>/metacity-1

or, if the theme is installed only for your user to ~/.themes/<name>/matacity-1

and edit the file metacity-theme-1.xml at the following location:

```

<!-- general window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
  <distance name="left_width" value="1"/>
  <distance name="right_width" value="1"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="10"/>
  <distance name="right_titlebar_edge" value="10"/>
  <distance name="button_width" value="18"/>
  <distance name="button_height" value="20"/>
**  <distance name="title_vertical_pad" value="5"/>**
  <border name="title_border" left="2" right="2" top="0" bottom="0"/>
  <border name="button_border" left="0" right="0" top="1" bottom="0"/>
</frame_geometry>

```

Change the value of the variable in bold to change the title bar size, smaller value will make the title bar smaller, larger will make it larger.

In order to keep a concistant appearance, you may also want to change the size of the title bar when maximized:

```

<frame_geometry name="geometry_maximized" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="10"/>
  <distance name="right_titlebar_edge" value="10"/>
  <distance name="button_width" value="18"/>
  <distance name="button_height" value="20"/>
**  <distance name="title_vertical_pad" value="6"/>**
  <border name="title_border" left="2" right="2" top="0" bottom="0"/>
  <border name="button_border" left="0" right="0" top="1" bottom="0"/>
</frame_geometry>

```

Cheers!
-Beboy

---

