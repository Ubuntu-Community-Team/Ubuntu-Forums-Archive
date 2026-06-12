---
title: "Gnome panel shows colored block on left and right side"
date: 2009-12-23
forum: Desktop Environments
---

### Post by michaelgilch on 2009-12-23
I have about a 12px block on both ends of my panel with the following settings:

uncheck Expand
uncheck Show Hide Buttons
Background = 100% Transparent

It seems to be a placeholder of sorts for the Hide Buttons, and gives you the ability to drag the panel around. I am looking for a way to make those 12px blocks transparent along with the rest of the panel. I have searched extensively through gconf-editor with no luck. Any suggestions?

Attached is a screenshot of the blocks in question.

Thank you

---

### Post by michaelgilch on 2009-12-24
I solved it! 

A little more info: I am using the Dust theme. I discovered that the block color would change when I changed the Dust Theme Controls.

Solution:  In /usr/share/themes/ there is a folder for each theme you have installed.  I searched for 'panel' in /usr/share/themes/Dust/gtk-2.0/gtkrc and the first entry that came up was:
```
style "panel" = "dark" {
  bg[NORMAL] = "#2C2B29"
  engine "murrine" {
  }
}
```
I checked the "#2C2B29" value in Gimp. It happened to be the exact color of the block in question.  So, I changed that value to "#000000" to match my black background. No more blocks!

---

### Post by w1d3 on 2011-07-23
> **michaelgilch said:**
> I solved it! 

A little more info: I am using the Dust theme. I discovered that the block color would change when I changed the Dust Theme Controls.

Solution:  In /usr/share/themes/ there is a folder for each theme you have installed.  I searched for 'panel' in /usr/share/themes/Dust/gtk-2.0/gtkrc and the first entry that came up was:
```
style "panel" = "dark" {
  bg[NORMAL] = "#2C2B29"
  engine "murrine" {
  }
}
```I checked the "#2C2B29" value in Gimp. It happened to be the exact color of the block in question.  So, I changed that value to "#000000" to match my black background. No more blocks!
is there a way to make the color transparent

---

