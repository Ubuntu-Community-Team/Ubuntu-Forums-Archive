---
title: "Button text color with dark gtk theme"
date: 2007-03-17
forum: Forum Feedback &amp; Help
---

### Post by tomchuk on 2007-03-17
I'm using a GTK theme with a dark background color and a light grey foreground (text) color. The button class in the forums' stylesheet styles the background of buttons but not the foreground. With the theme I'm using the result is that the button text and background are the same color.

Looking at the css in firebug, it seems that the color attribute for the buttons should be inherited from the panelsurround class, but running an up-to-date Firefox in Feisty, this is not being applied.

Could someone please add a "color: #444444;" to the button class so that buttons are readable regardless of the GTK foreground color.

What the submit/preview buttons look like now:
[img]http://tomchuk.com/drop/ubuntu_forums_buttons_pre.png[/img]

What they look like with "color: #444444" added to the button class:
[img]http://tomchuk.com/drop/ubuntu_forums_buttons_post.png[/img]

---

### Post by bonzodog on 2007-03-20
Yes, you will also see that with dark themes that the text boxes also use white text with a white background by default, so you cannot see what you are typing! The CSS should be setup so that it inherits the gtk theme, with a dark background in the text boxes, and dark text in the buttons.

---

