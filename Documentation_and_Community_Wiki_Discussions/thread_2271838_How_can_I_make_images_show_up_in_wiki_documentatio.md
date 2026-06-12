---
title: "How can I make images show up in wiki documentation?"
date: 2015-04-02
forum: Documentation and Community Wiki Discussions
---

### Post by Clopper Almon on 2015-04-02
I recently downloaded the gThumb program ffor editing and searching the EXIF data of .jpg files. Once you learn by trial and error how to use the program, it is just about ideal for its purposes. But the eight-year-old official documentation and what you get from the Help of the program itself are both out of date, and neither matches how the program works. 

For my own use and that of associates, I wrote a three-page guide to using it. The guide contains five screen shots. I easily updated the text of the Community documentation and easily uploaded the fiive  .png files of the screenshots. But I have been unable to make the screenshots show up when the wiki is viewed. The directions that I could find say that, where the image should appear, I should put either   attachment:filename.png or [[attachment:filename.png]]  Neither works. Does anyone know how to make those pictures show up?

---

### Post by sudodus on 2015-04-02
If it is an Ubuntu wiki page or help page, you can tell me the address to the page I can try to fix it, and then you can see in the raw text, how I did it :-)

---

### Post by sudodus on 2015-04-02
I found the wiki page, and you can wrap it in double curly braces, like

{{attachment:filename.png}} 

I did it with one picture. I suggest you do it for the other pictures.

Thanks for sharing your knowledge about gThumb :KS

---

### Post by Clopper Almon on 2015-04-02
It is a community documentation page with the URL: 
[https://help.ubuntu.com/community/gThumb](https://help.ubuntu.com/community/gThumb)

When I looked back at it today, someone had already fixed the first image, and I then fixed the others. 

All of the Ubuntu documentation that I could find said to do either
[[attachment:filename.png]]
or just
attachment:filename.png

In fact what works is 
{{attachment:filename.png}}

In other words, one should use curly braces not square brackets. 

If you know any way to make the text wrap around the image, please apply it to one of the images, and I will then fix the others.

Thank you.

---

### Post by slickymaster on 2015-04-02
*Moved to the ***Documentation and Community Wiki Discussions*** sub-forum*

---

### Post by sudodus on 2015-04-02
It is possible by enclosing the pictures in table cells. But you must also arrange the text in a way, that it will fill the space to the right of the pictures.

||<tablestyle="float:left; margin: 0 0 1em 1em;" style="padding:0.5em;"> {{attachment:gThumbOne.png}} ||

I'm not sure that the result is better. If you think so, use it! But most Ubuntu wiki pages and help pages do not use this feature.

-o-

Did you find this link for general editing help: [https://help.ubuntu.com/community/HelpOnMoinWikiSyntax?action=show&redirect=MoinMoin%2FTextFormatting](https://help.ubuntu.com/community/HelpOnMoinWikiSyntax?action=show&redirect=MoinMoin%2FTextFormatting)

---

