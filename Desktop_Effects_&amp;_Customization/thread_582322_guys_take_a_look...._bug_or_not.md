---
title: "guys take a look.... bug or not?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Myronray on 2007-10-19
if i select in visual effects >> normal my window no bar, no close, no minimized icon in the upper rightside and i cannot drag also, i use gforce 6600-LE vcard plss and i install properly my vcard driver,,help to resolve this problem,

thanks

---

### Post by carlinuxlearner on 2007-10-19
I don't think it's a bug, but there is a way to fix it, don't remember what that is though, I'll look around.

C@RL

---

### Post by Myronray on 2007-10-19
carl need ur help how to fix this hehehe :) i weyt for ur response.. thanks

---

### Post by carlinuxlearner on 2007-10-19
Alright open up a terminal and execute this "sudo gedit /etc/X11/xorg.conf" and then in the "device" section of the file put in this "
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
" 
and at the bottom of the file (if it's not there already) and this "

Section "Extensions"
Option "Composite" "Enable"
EndSection

"
save the file and restart your computer, this should fix it.

C@RL

---

### Post by Myronray on 2007-10-20
weeeeeeeeeeeeeeeeeeeeee!!!!!!!!!!!!!!!!!! thanks carl its workinggggggggggggggg!!!!!!!

thanks, thanks, thanks your the man... IDOLLLLLLL hehehehehe

---

### Post by OldGrey on 2007-10-20
Hi

Tried this fix out, which I eventually got working, but with some odd side effects.

My log in screen is at the wrong resolution - I run 1280 x 1024 and it looks about 800 x 600.

Also the keyboard switches to US English configuration and I use UK English and it rests to US every time I log on.

What went wrong?

Sorted out the keyboard - chaned the keyboard in the xorg.conf file. Still have the resolution issue on the log-in screen

---

### Post by carlinuxlearner on 2007-10-20
@ OldGrey
Open up a terminal window and execute this "sudo dpkg-reconfigure xserver-xorg" answer questions accordingly, then restart your computer (or just restart X) this might fix it.

C@RL

---

### Post by OldGrey on 2007-10-20
Thanks, It'll have to wait till tomorrow now, but I'll give it a go when I have more time.

---

### Post by mishaco on 2007-10-21
ive taken all the advice here and it has helped , to an extent . 

"sudo dpkg-reconfigure xserver-xorg" was the most help . it brought my nvidia dual dvi 6600 gt close to its spec . and resolution , though both of my dell 1907fp monitors report in screens and graphics differently . 

so , for now , im getting this : [_**[COLOR="Red"]Screenshot.png[/COLOR]**_]("http://www.mishaco.com/ubuntu/Screenshot.png") kind of thing .

---

### Post by OldGrey on 2007-10-21
> **carlinuxlearner said:**
> @ OldGrey
Open up a terminal window and execute this "sudo dpkg-reconfigure xserver-xorg" answer questions accordingly, then restart your computer (or just restart X) this might fix it.

C@RL

I have done this which worked in the sense in that I am back to square 1- ie everything works fine except the visual effects

OldGrey

Since discovered that download xserver-xgl using synaptic does the trick

---

### Post by carlinuxlearner on 2007-10-21
try running this,  click ALT + F2 then type in this "compiz --replace" see what happens, if the visual effects are enabled then you are good to go; if not then edit your "/etc/X11/xorg.conf" in the device section make sure the "driver" is "nvidia" if it is not the change it so it is. Then restart your computer. Post any errors or whatever here.

C@RL

---

