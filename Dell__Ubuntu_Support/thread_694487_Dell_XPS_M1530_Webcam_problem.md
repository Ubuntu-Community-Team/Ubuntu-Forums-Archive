---
title: "Dell XPS M1530 Webcam problem"
date: 2008-02-12
forum: Dell  Ubuntu Support
---

### Post by sgtbug on 2008-02-12
I have searched the forum for 2 days, and have not found any working solution for my webcam problem in Gutsy.

Here is the story:

I installed Gutsy 32-bit yesterday, and removed ekiga. My webcam was not working after i tried it with cheese.

Then I installed 64-bit but the display driver was giving problems. I did not remove anything and the webcam was working, but I chose to install 32-bit realizing that my webcam would work in that too.

Then I installed 32 bit yet again. Then tried the webcam through cheese and yippee! It was working! I was so happy that I shut my system down and went to sleep.

Next morning I fired up the system to chat with my girlfriend (who is very upset with me now!), and the webcam wouldnt work again! I tried everything. All people tell me is that it should work out of the box, but it isnt working!

attaching my lsusb, modprobe -l output..

---

### Post by hyperair on 2008-02-12
Could you try posting the output of "lsmod"? On a side note I was actually thinking of getting a Dell XPS M1530. How's the performance of that laptop with Ubuntu? I've tried searching but there are hardly any resources on it.

---

### Post by sgtbug on 2008-02-12
here is my lsmod output..

the performance is fine.. the touchpad is a little funny when u close the lid n open again..

---

### Post by hyperair on 2008-02-12
Alright. What you need to do is try: 
```
sudo modprobe gspca
```

Then try doing your stuff with Cheese again. If it works, then you must edit your /etc/modules file. Add (on a new line) "gspca". 
```
sudo gedit /etc/modules
```

p.s. What do you mean by "a little funny"? And also.. is there anything that doesn't work by default on the laptop and what did you have to do to get it to work? =\

---

### Post by sgtbug on 2008-02-12
thanks a lot for replying.. but it did not work.. 

btw.. i am not getting the resolution i should be getting, which is 1680x1050.. i still have to run it on 1280x800.. fixing that..

the touchpad starts working on its own like a freakin ghost when u close n open the lid.. that was in 32 bit.. 64 bit has resolution issues.. everything should work out of the box.. its not like my frnd's acer 4520, which reqd a whole lot of stuff to be done..

---

### Post by sgtbug on 2008-02-12
ok.. now again webcam is working..

but there is a new issue.. check out the screenshot..

---

### Post by hyperair on 2008-02-13
Try running "gnome-settings-daemon&exit" in a terminal, or just "gnome-settings-daemon" in a run dialog.

---

### Post by sgtbug on 2008-02-13
nothings working.. i tried all that.. gnome-appearance-manager does not open.. settings-daemon wont open..

i finally give up.. installing ubuntu 32 bit atm.. no resolution issues.. webcam issue is there but that is just it.. in 64 bit, everything was causing problems.. the nvidia driver was conflicting with something..

things were fine on "nv" but as soon  i installed nvidia-glx-new or installed the driver manually, i started getting problems..

also, i was getting only 1280x800 resolution, instead of 1680x1050..

shutdown was not happening.. it got stuck at ALSA.. sound was screwed.. blah blah!

32 bit everything is smooth.. m gonna use 32 bit till hardy comes out..

btw.. another funny thing happened.. when i run the modprobe command for my webcam module, and reboot it works.. and works in vista too (i knw it sucks but i need an os which constantly runs).. and when it stops working in ubuntu, it stops there too.. then i gotta come back to ubuntu, load the module and reboot.. webcam works..

things are getting very screwed up here!!

---

### Post by hyperair on 2008-02-13
That sounds... insane. Looks like Ubuntu's gspca driver somehow shuts off the webcam, hardware-wise Oo

---

### Post by sgtbug on 2008-02-13
i really dont understand why this is happening.. btw.. if u do buy this model.. be sure to never install 64 bit.. dunno why but i think my inspiron 6400 was much more stable!!

i will post the report on 32 bit.. installing updates now.. :)

---

### Post by sgtbug on 2008-02-13
k.. all stable.. running 32 bit.. tried rebooting several times.. webcam still works.. added gspca to /etc/modules.. all perfect..

but wish 64 bit could be as smooth.. ^^

---

### Post by hyperair on 2008-02-13
Sounds great. ^^

---

### Post by sgtbug on 2008-02-13
yup ^_^..

getting 2mp pics using GUVCView..

---

### Post by Aybara on 2008-02-17
I'm having problems with the webcam on this laptop as well. I'm on gutsy. I tried downloading the latest gspca driver and installed it. When I try camorama I get a message saying something like "Could not open video device (/dev/video0). Please check the connection".

lsmod | grep gspca
gspca                 608336  0 
videodev               29312  2 gspca,uvcvideo
usbcore               138632  7 spca,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd

---

### Post by hyperair on 2008-02-17
How about ```
ls -l /dev/video*
```

---

### Post by Aybara on 2008-02-17
crw-rw---- 1 root video 81, 0 2008-02-17 09:02 /dev/video0

Tried running "sudo camorama" as well, but it didn't do the trick.

---

### Post by mgc8 on 2008-05-05
I think the correct driver for the webcam is "uvcvideo" not "gspca". I just tried to get this to work using gspca, and it doesn't recognize any webcam. Loading uvcvideo however immediately blips the blue led and the camera is recognized and works using cheese for example. Since the cam supports UVC, I think the uvcvideo way is the best in any case. To make sure it's loaded on boot, add "uvcvideo" to /etc/modules...

Regards,
Mihnea

---

