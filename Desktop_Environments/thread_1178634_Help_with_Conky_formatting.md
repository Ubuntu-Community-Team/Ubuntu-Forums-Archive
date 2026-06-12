---
title: "Help with Conky formatting"
date: 2009-06-04
forum: Desktop Environments
---

### Post by lsutiger on 2009-06-04
I am asking someone out here to help me out with the formatting of my conky settings. I have it very minimal, and that is the way I want to keep it. But I am having a problem with formatting. I have alignc as one of the tags, but it is not formatting the line as centered. I am attaching the conkyrc file and a screenshot. 

I am not sure why it is acting this way, but I can not get it to center.

Thanx in advance!

---

### Post by m_duck on 2009-06-04
Assuming your monitor resolution is 1680x1050 from your screenshot, I would try changing and adding the following:

[LIST=1]
[*]Change [COLOR=SeaGreen]**minimum_size 100 5**[/COLOR] to [COLOR=SeaGreen]**minimum_size 1660 5**[/COLOR] (1660 due to the gap_x property).
[*]Add a line under it reading: [COLOR=SeaGreen]**maximum_width 1660**[/COLOR] (this will make sure your conky is always 1660px wide).
[/LIST]
I think that's all I thought of... I think the problem is that as you only have a minimum size declared which is smaller than the lines of text you have, conky has taken the longest of the lines as its width, and then centered everything according to that. Those two changes should make conky stretch to a full width and center everything within that.

HTH

---

### Post by lsutiger on 2009-06-08
Thanx!

---

