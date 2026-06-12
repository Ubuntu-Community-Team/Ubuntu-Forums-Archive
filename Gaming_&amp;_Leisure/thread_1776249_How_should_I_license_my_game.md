---
title: "How should I license my game?"
date: 2011-06-05
forum: Gaming &amp; Leisure
---

### Post by twopointfour on 2011-06-05
I want to port an iOS game I wrote to linux and release it for purchase in the Ubuntu Software Center and I have some licensing questions. I'm going to be using [cocos2d]("http://www.cocos2d.org/"), a python game development framework, for my port, so my game will be written in python.

I'm happy to share the source code (I'm not sure I have a choice if it's written in python), but I also want people to purchase it still. I think I've heard of things like open sourcing your game code but not your game assets? Is this possible, and how do you do it? Include a LICENSE file that explains the assets are not to be redistributed but everything else is GPL (or whatever license I choose), and include the GPL at the top of all the source files? If I do this, how do I distribute the code? A tarball that just doesn't include any images?

I could keep it proprietary as well. But again, I believe I have to release the code since it's going to be written in python. Has anyone else dealt with semi-open sourced video game licensing?

---

### Post by mastablasta on 2011-06-06
> **twopointfour said:**
> I could keep it proprietary as well. But again, I believe I have to release the code since it's going to be written in python. Has anyone else dealt with semi-open sourced video game licensing?
 
i don't think that is how it works. you should really look more thoroughly into these licences. There are plenty out there. GPL, Apache or you can even make one yourself.
 
Just because you used the opensource tools doens't mean that the product needs to  be open source and free as well. 
 
for example you can use opencart for free as it's opensource but you can create your theme and then sell the theme (or any other add on).
 
same you can create an image in GIMP and then sell it. 
 
so unless Python restricts this specifically then it is allowed to "close" your license.and in fact it is specific license called Python Software Foundation license: 
[http://en.wikipedia.org/wiki/Python_Software_Foundation_License](http://en.wikipedia.org/wiki/Python_Software_Foundation_License)
 
> allows modifications to the source code, as well as the construction of derivative works, without making the code open-source.

---

### Post by danbishop on 2011-06-06
I think the OP meant that as python is an interpreted language people can just look at the code anyway... so although he doesn't necessarily have to release it under a free licence like the GPL, the project will always be open source, just not necessarily free and open source (big difference!).

I think you've made the best decision already. License the code as GPL and your game assets such as artwork, music etc. as proprietary. 

I believe even Richard Stallman himself once said something about that being the perfect way to license such a game. You will need to look into the GPL if you're not familiar with it of course, to be absolutely certain that it works for you. I see no reason why it should not though.

This way you you might even find that people are willing to port your game to other platforms (windows, android, etc.) for free as the code is GPL, but you will make money from these ports as people will still have to pay for your non-free artwork.

---

