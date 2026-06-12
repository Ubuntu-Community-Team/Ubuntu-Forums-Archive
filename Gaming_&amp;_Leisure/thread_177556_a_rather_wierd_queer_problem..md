---
title: "a rather wierd queer problem."
date: 2006-05-16
forum: Gaming &amp; Leisure
---

### Post by RajivNair on 2006-05-16
im having ubuntu 5.10 installed on intel motherboard 845g with on onboard graphics of 64mb.i play CS in wine,and it works like a charm,very smooth.as i was browsing thru the threads i came to know that to have 3d acceleration glxgears should be showing above 1000fps but mine gives me:-
"
rajiv@Rajiv-Nair:~$ glxgears -printfps
2407 frames in 5.0 seconds = 481.146 FPS
2382 frames in 5.0 seconds = 476.242 FPS
2381 frames in 5.0 seconds = 476.048 FPS
2387 frames in 5.0 seconds = 477.198 FPS
2336 frames in 5.0 seconds = 467.133 FPS
"
but on the other hand the "glxinfo" command shows that direct rendering is enabled.so i am in a fix now,i dont know whether i have 3d acceleration or not.can anyone explain whats happening.

---

### Post by Lord Illidan on 2006-05-16
Glx gears is rather inaccurate. If you are getting nice animations and good fps in CS, don't bother.

Try getting a couple of other games, just to test...

```
sudo apt-get install gl-117
```

---

### Post by DJ Scribblinni on 2006-05-16
I think this is the command to find out if 3D acceleration is working,,,not sure though: ```
glxinfo | grep rendering
```

---

### Post by RajivNair on 2006-05-16
yes DJ,thats a correct command and the result is:-
"
rajiv@Rajiv-Nair:~$ glxinfo | grep rendering
direct rendering: Yes
"
but as i have seen in the forums,people have difficulty just to setup their resolutions above 640*480 with intel onboard graphics and what im intrigued about is that i havent installed any drivers or nything regarding graphics.and also the glxgears result,whats amazing is,when i minimize thw gear windows,i get fps upto 2500,but when its displayed it falls back to 500.

---

### Post by RajivNair on 2006-05-16
hey lord illidan,i tried gl-117 and it give me fps frm 20-30 and also message comes up saying my "fps is low turn down the graphics settings".i have kept every option on and playing at 1024 resolution.when i turned every option off, i got 50-55 fps at 800 resolution.but the graphic still sucked.

---

