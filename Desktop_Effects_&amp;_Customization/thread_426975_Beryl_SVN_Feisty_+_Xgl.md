---
title: "Beryl SVN Feisty + Xgl?"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by Mr Greencastle on 2007-04-29
Is that possible?

I tried it and had to rollback to 0.2, I may be doing something wrong...

---

### Post by kbzona on 2007-04-29
:lolflag:  thnx for the wobbly thing! now i will give u back the favor :) 

for Beryl SVN + Feisty .. Treviño's repos should work fine...

add this to the /etc/apt/sources.list

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 


finally the key:

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

and ... install beryl... :guitar:

---

### Post by Mr Greencastle on 2007-04-29
Thanks, it half worked.

I fixed it by removing: deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

from the /etc/apt/sources.list

I love the features in the SVN release, and am happy to have them again in Feisty. +1 for the Ubuntu community!
Many thanks!

---

### Post by Mr Greencastle on 2007-04-29
One more quick question, it seems that when unminimizing windows, they pop up instantly, then the effect happens afterward...

It also happens when creating new windows/starting other programs, any fix?

Edit: fixed by deselecting then reselecting water... odd bug perhaps?

---

### Post by kbzona on 2007-04-29
i also a a similar problem but just with one effect...i think that the window draws too fast and the effect just looses the timing...:lolflag:

---

### Post by Mr Greencastle on 2007-04-29
Try going to the "Extras" tab and deselect something that you don't really need, like benchmark or whatever.

It worked for me.

---

### Post by kbzona on 2007-04-29
:(  ive already tried that but didnt solve the problem..

well i played around with the open create close timings and that solved it :) :)

---

### Post by Mr Greencastle on 2007-04-29
Thats lame, oh well, I guess there are some sacrifices for Beryl...

Also a weird thing, does your skydome turn white when using water effects?

---

### Post by kbzona on 2007-04-29
yes i have the same problem... :confused:

---

### Post by Mr Greencastle on 2007-04-29
Its weird, oh well, I don't really use water anyway....and now I can't get snow to work :(

---

### Post by kbzona on 2007-04-29
for the snow plugin to work u must ensure that u have installed:

beryl-plugins-unsupported

---

### Post by Mr Greencastle on 2007-04-29
Yeah I installed it but when I do a Super F3, nothing happens, I've tried changing the shortcut too and no luck...

---

### Post by kbzona on 2007-04-29
Oh.. thats weird... mine works fine :confused: 

this may sound dumb but. make sure that you have activated the snow plugin and the snow in the screensaver plguin

---

### Post by Mr Greencastle on 2007-04-29
lol yep it was the screensaver thing that wasn't activated...
I feel dumb

---

