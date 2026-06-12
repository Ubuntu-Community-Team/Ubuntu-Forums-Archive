---
title: "MPlayer Background"
date: 2006-02-14
forum: Desktop Environments
---

### Post by DonQuixote on 2006-02-14
On many films when playing at full screen there is this annoying blue background at the top and bottom of the screen.  In other players it is black and allows me to focus on the movie.

Is there a way of changing that background color? Yes? \\:D/ 

Thanks!

---

### Post by DonQuixote on 2006-02-14
Do themes for MPlayer affect the background I'm talking about?

---

### Post by DonQuixote on 2006-02-14
Well, for anyone else who is having trouble with this, here is what I found (I read the manual, once I found it!)

In the "/usr/share/mplayer/Skin/default/" directory (this was where Synaptic placed it) there is a file named "skin".

You will need to open it as root using "sudo".
- Open a terminal window and type: "sudo kate /usr/share/mplayer/Skin/default/skin" (Kate may not be your editor, use the editor of your choice)
- Enter your password

In the file look for this section:
```

 window = sub

  ;base=bitmap,x,y,sx,sy
  ; x:            | y:
  ;  -  0: left   |  -  0: top
  ;  - -1: center |  - -1: center
  ;  - -2: right  |  - -2: bottom
  base = subblue, -1,-1, 640, 480
  ; background=r,g,b
  ; window background color, default is black
  ; only subwindow, and decimal numbers
  background = 128,128,255

 end

```

At the end where you see "background = 128,128.255" replace those numbers with values between 0 and 255, using the RGB (Red, Green, Blue) format.

For Black, I entered 0,0,0.  For White you would enter 255,255,255.

Pick the color you want, and enjoy.

---

