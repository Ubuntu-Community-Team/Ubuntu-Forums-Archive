---
title: "Some Games Will Not Load"
date: 2009-02-07
forum: Gaming &amp; Leisure
---

### Post by monkeychick on 2009-02-07
Hi,
I have just finished playing Supertux one without any problems at all, so I installed supertux2 from the repo. When I click on it to play nothing happens. This also happens with a few other games such as supertuxcart.

Im using Ubuntu 8.04 and this is the output from  the terminal for supertux 2

michelle@michelle-desktop:~$ supertux2
[/home/michelle/.supertux2] is in the search path
[/usr/share/games/supertux2] is in the search path
Invalid button '0' in buttonmap
Invalid button '1' in buttonmap
Invalid axis '-2' in axismap
Invalid axis '-1' in axismap
Invalid axis '1' in axismap
Invalid axis '2' in axismap
Fatal: Unexpected exception: Couldn't set video mode (800x600-0bpp): Couldn't find matching GLX visual
michelle@michelle-desktop:~$ 

And here is the output for supertuxkart

michelle@michelle-desktop:~$ supertuxkart
freeglut (supertuxkart): OpenGL GLX extension not supported by display ':0.0'
michelle@michelle-desktop:~$ 

I have no idea what any of that means but would I be right in assuming it's something to do with graphics? When I click to see hardware drivers I get a message saying nothing is in use on the system. I am still quite new to Ubuntu and any help is greatly appreciated.

Thanks In Advance.

---

### Post by hikaricore on 2009-02-07
Definitely a video hardware/driver issue.

Please give some more info on your hardware and someone may be able to assist you.

---

