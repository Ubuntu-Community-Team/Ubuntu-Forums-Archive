---
title: "Where did KeyjnoteGUI go? (Or how to add 3D effects to presentations)"
date: 2010-05-10
forum: Education &amp; Science
---

### Post by PC_load_letter on 2010-05-10
So, Keyjnote (aka impress!ve) is still in the repos but it's a CLI tool, which I think would be very hard to use given the objective here. There used to be a KDE GUI for it but it's only available for versions <= Hardy. 

I didn't hear about it before now, and I think it'as a pretty neat idea to pimp a beamer presentation w/ 3D effects and what have you. 

So, are there anything similar to this which is still in active development? I know about OOo Impress w/ ogltrans extension but it's not working for me on Karmic 64 bit, besides I'd rather use beamer (way easier) for my presentations.

Thanks in advance.

---

### Post by PC_load_letter on 2010-05-10
Ok, so I have a partial (albeit tedious!) workaround:
- First I just write my Math. presentation w/ beamer, ouput as either pdf or ps.
- Using the convert command from the ImageMagick package I convert the beamer pdf (or ps) presentation into individual jpg slides as follows:
```
convert -quality 100 -density 600x600 beamer_presentation.pdf single%d.jpg
```

- Here is the tedious part: Start OOo Impress, create an empty presentation, then insert each single jpg file in a slide. The average 50mins presentation could take up to 50~60 slides in my case, so is there a way one could do this from the command line?

- Voila! You can now use whichever transitional effect between slides....BUT....of course no control over any individual slide. Using the **openoffice.org-ogltrans** package (which is finally working for me) really makes the presentation come to life.

Any better ideas to achieve similar results?

---

### Post by ugm6hr on 2010-05-12
Impressive is actually very easy to use from CLI:
[http://impressive.sourceforge.net/manual.php](http://impressive.sourceforge.net/manual.php)

If you use XFCE / thunar, you can easily create a custom action to launch any PDF in it with a right-click.

There is generally little need to mess with any of the options... Or if you do, you will tend to use the same options each time.

---

