---
title: "using S-video for TV hookup produces odd graphics"
date: 2010-04-02
forum: Desktop Environments
---

### Post by Jordanwb on 2010-04-02
I have a computer that I want to use as a Multimedia machine. It has a ATI radeon X1600 Pro AGP video card. It has a VGA, DVI and S-video output ports. I have the computer hooked up to my TV via a S-Video cable. When the computer starts Ubuntu 9.10 off of the LiveCD the menu (the one that says "Try without installing", "Run a memory test"...) displays perfectly. No issue. When usplash (the one that shows the pulsing Ubuntu logo) there are no issues. When Xorg finally starts the graphics are weird:

[IMG]http://img641.imageshack.us/img641/1637/img0192ma.jpg[/IMG]

It seems like my TV is trying to decide if it's PAL or PAL-N. If I drop to VTY1, the text is white on a green background. When I issue "sudo halt", the VTY changes to a black background.

How do I get xorg to work properly so I can get to Gnome?

If anyone wants I can record a video displaying what happens. I find it especially odd since I live in Canada and not in Europe.

[Edit]

I never saw this before but there's a jumper on the video card controlling video format. I'll try changing that.

[Edit #2]

No change.

---

