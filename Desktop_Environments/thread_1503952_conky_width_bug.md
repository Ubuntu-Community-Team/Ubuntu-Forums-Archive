---
title: "conky width bug?"
date: 2010-06-07
forum: Desktop Environments
---

### Post by Kodpoet on 2010-06-07
I'm fiddling around with conky and as I turn on "draw_border" I notice there's a bunch of extra space next to my conky. I try to change the "minimum_size" / "maximum width" to something more slim but what happens is that the extra space is unaffected but the text however is.

How come this is happening and is there a remedy?

conkyrc code of potential interest:

```
own_window yes
own_window_transparent yes
own_window_type desktop
background no
```The left screenshot is with:

```
minimum_size 400 5
maximum_width 400
```and the right is with:

```
minimum_size 300 5
maximum_width 300
```[IMG]http://i49.tinypic.com/24fzfhg.png[/IMG]

---

### Post by Kodpoet on 2010-06-07
My bad,

since I copied this conkyrc from somewhere I didn't notice the "${offset 240}" infront of all text :P bummer.

I'm not sure why anyone would want to have all that space infront of the text though?

---

