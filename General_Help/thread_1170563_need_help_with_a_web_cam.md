---
title: "need help with a web cam"
date: 2009-05-26
forum: General Help
---

### Post by jdmdelsol97 on 2009-05-26
ok so i gave my dad my dell with ubuntu on it, since its easier for him to use. I went ahead and bought him a logitech quick cam connect as a gift. the problem is skype doesnt recognize it. ok, so its time for some drivers. i went through the forums and came to this...[http://mxhaard.free.fr/download.html....but](http://mxhaard.free.fr/download.html....but) how do install it? i just extracts and keeps extracting and i have no idea what to do. any help as to how to install the drivers? im running ubuntu 8.10

---

### Post by kestrel1 on 2009-05-26
I am using the same cam, but have no problems using it under skype.
To check that it is working install cheese```
sudo apt-get install cheese
```
Once cheese is installed you can run it from the Applications -> Graphics -> Cheese Webcam booth.
You should then get the green light working on the cam & see a your picture.
If it is working you need to configure it with Skype.

---

### Post by kestrel1 on 2009-05-26
Quick update on this. I had used Skype under Ubuntu 8.04 & it worked fine. I have recently re-installed my system & only have 9.04 at present. Just installed skype again & I am getting nothing either. Are you using Ubuntu 9.04?
I am looking in to this at present & will post back with further info.

---

### Post by jdmdelsol97 on 2009-05-26
i'll try cheese but yea when i go to skype and go to video options it only gives me the test option but cant view anything.

---

### Post by kestrel1 on 2009-05-26
Yep same here. I suspect cheese will work for you, so it will prove that the webcam is fine.
I think it may be down to the fact that the guys at skype haven't updated the Linux programs for a very long time. I will see if I can find a way around it.

---

### Post by jdmdelsol97 on 2009-05-26
ok thanks

---

### Post by kestrel1 on 2009-05-26
Try this command & see if it works for you. You need to shutdown Skype first if it is running:```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
If it is the same as mine it won't make any odds.
To see if your Cam will work with libv4l1 type this in a terminal & try it out:```
gstreamer-properties
```
If you select libv4l2 you should see your cam working. With libv4l1 it will probably be green & full of interference.
I have yet to find a solution, but if you could post back with the results of the above it will prove that your problem is identical to mine. I continue to search for a solution.

---

### Post by jdmdelsol97 on 2009-05-27
hey thanks for everything turns out that the camera was broken after i got a replacement it works. thanks

---

### Post by kestrel1 on 2009-05-27
Glad you are sorted & working. I have just re-installed my system & gone back to Ubuntu 8.04. I was having a few other problems with Ubuntu 9.04 apart from the webcam. Hardy always played nice. Just got to reconfigure everything. I will probably use Jaunty as a virtual machine for the time being. Works well on my laptop, but doesn't like a few things on the desktop machine.

---

