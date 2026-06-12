---
title: "Inject the output of a PHP script through the socket Firefox is using"
date: 2009-02-11
forum: General Help
---

### Post by Acuity on 2009-02-11
Yup, this about covers it.

Here is what I am trying to do more elaborately:

On Facebook there's an App called Grafiti; essentially, it's a whiteboard that you get to draw pictures on or whatever.  With a little bit of skill, people have written programs to be able import images to Grafiti.

What I am trying to do is something similar to that of Grafiti, only it's in a little game and the Grafiti-like app is only one aspect of the game.  Oh, and the vast selection of colors isn't available (however you can inject them).

For a while now I have used a homebrewed PHP script to "upload," my pictures to the game pixel by pixel.  However, people have started being assclowns and using WPE Pro to erase other peoples' boards, deface them and whatnot.  So now there are security measures in place so you can't deface other boards.  Unfortunately this locks me out of being able to upload my images.

I'm thinking that the key to success now is to upload these images by virtue of the same open socket Firefox is using.  Unfortunately, on Windows, WPE Pro isn't sophisticated enough to string packets together and in order to upload using a PHP script, I would need to learn a whole bunch of programming knowledge that I don't want to learn due to the way Windows handles sockets.

I know that Linux doesn't protect their sockets like Windows does so perhaps there's a way for me to accomplish this task on Ubuntu.  

So are there any tools which can do what the title asks?  

Thanks for any assistance you can provide. ;)

---

### Post by mb_webguy on 2009-02-12
The Programming board might be a better place to ask about this.

---

