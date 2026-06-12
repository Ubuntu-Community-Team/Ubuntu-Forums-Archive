---
title: "Annoying window border corners with Compiz"
date: 2009-12-24
forum: Desktop Environments
---

### Post by Ubom on 2009-12-24
Hi, 
With Compiz turned on, the bottom corners of my windows do not to be a smooth curve like it is when Compiz is turned off. It is a bit difficult to describe exactly what I mean so I have attached a couple of small images to highlight what is going on. Look at the bottom right corner of the window in both the following images.

With Compiz:
[IMG]http://imgur.com/ZPJK3.png[/IMG]

Without Compiz:
[IMG]http://imgur.com/L1Cfh.png[/IMG]

Other Info:

[LIST]
[*]I am using Ubuntu 9.10.
[*]I have changed all my fonts to size 8 using the appearance tool in preferences.
[*]I am using the default Human theme.
[/LIST]

If anyone knows how I can make the corners look like they do without Compiz while running Compiz your help would be much appreciated.

Thanks.

---

### Post by mocoloco on 2009-12-24
At first I didn't see what you mean but I do now.  I compared my own window corners and I see the same thing, right where the corners turn up there's a jaggie spot that pokes out.  Only there when compiz is on.  It's a small thing but it's noticeable once pointed out.  Maybe this should be a bug or a "paper cut"?

---

### Post by Ubom on 2009-12-24
Hi, I managed to find a quick solution to fix the problem, but it does involve sacrificing 2 pixels of height for every window. Basically, you edit you the metacity-theme-1.xml file. I just changed:
```
<frame_geometry name="normal" rounded_top_left="true" rounded_top_right="true" rounded_bottom_left="true" rounded_bottom_right="true">
  <distance name="left_width" value="3"/>
  <distance name="right_width" value="3"/>
  <distance name="bottom_height" value="3"/>
  <distance name="left_titlebar_edge" value="3"/>
  <distance name="right_titlebar_edge" value="3"/>
  <aspect_ratio name="button" value="0.9"/>
  <distance name="title_vertical_pad" value="3"/>
  <border name="title_border" left="2" right="2" top="1" bottom="2"/>
  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>
```

with
```
<frame_geometry name="normal" rounded_top_left="true" rounded_top_right="true" rounded_bottom_left="true" rounded_bottom_right="true">
  <distance name="left_width" value="3"/>
  <distance name="right_width" value="3"/>
  <distance name="bottom_height" value="[COLOR=Purple]**5**[/COLOR]"/>
  <distance name="left_titlebar_edge" value="3"/>
  <distance name="right_titlebar_edge" value="3"/>
  <aspect_ratio name="button" value="0.9"/>
  <distance name="title_vertical_pad" value="3"/>
  <border name="title_border" left="2" right="2" top="1" bottom="2"/>
  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>
```

and the problem seems gone. If anybody has a better solution please tell me.

---

