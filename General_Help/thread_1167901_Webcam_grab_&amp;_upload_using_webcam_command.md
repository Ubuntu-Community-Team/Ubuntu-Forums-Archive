---
title: "Webcam grab &amp; upload using webcam command"
date: 2009-05-23
forum: General Help
---

### Post by Gina on 2009-05-23
I'm trying to upload my webcam images to my website.  The built-in ***webcam*** command is supposed to do it (run from terminal) but I can't get it to work.  It read the **grab** section of the info file then nothing.> gina@AMD64-Jaunty:~$ webcam ~/weather/webcam.conf
reading config file: /home/gina/weather/webcam.conf
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320

I'm wondering if it isn't finding my webcam - in fact, I don't really know exactly what to put in the configuration file.

My message log shows > May 23 16:29:39 AMD64-Jaunty kernel: [29205.202410] uvcvideo: Found UVC 1.00 device Sweex Webcam USB (0ac8:3343)
May 23 16:29:39 AMD64-Jaunty kernel: [29205.205396] input: Sweex Webcam USB as /devices/pci0000:00/0000:00:02.1/usb1/1-10/1-10:1.0/input/input15

Can anyone help please?

EDIT...  I should add - the webcam works fine in **xawtv** It refers to it as Camera 1

---

### Post by Gina on 2009-05-23
With more testing I have found one problem.  Although the webcam command output shows it as having read the config file, in fact it hasn't.  When I tried changing the settings, they didn't change in the terminal display.  I then tried using the default config filename and location without the option in the command line and now the result is different.> gina@AMD64-Jaunty:~$ webcam
reading config file: /home/gina/.webcamrc
v4l2: open /dev/video1: No such file or directory
v4l2: open /dev/video1: No such file or directory
v4l: open /dev/video1: No such file or directory
no grabber device available
gina@AMD64-Jaunty:~$ 

Changing input device back to **[B]device = /dev/video0**[/B] and **Input = Camera 1** gets a bit further.> gina@AMD64-Jaunty:~$ webcam
reading config file: /home/gina/.webcamrc
invalid norm: pal
gina@AMD64-Jaunty:~$
So it seems norm = pal is wrong and yet that is in the example given in **man webcam** and the webcam is the UK version which I assume uses the PAL standard.

---

### Post by Gina on 2009-05-23
Sorted... Commented out norm = pal and it's grabbing images and uploading them to my website :)

---

### Post by Gina on 2009-05-23
Not quite solved after all :(

Got the web page done and updating regularly and the ***webcam*** applet uploaded regularly BUT it's not grabbing a new webcam image for each upload although it's updating the title/date/time watermark.  It's just not grabbing a new webcam image :(

---

### Post by Gina on 2009-05-27
Working alright now - using webcam to add a "weathercam" to my weather station website :)

---

### Post by Robt6 on 2009-07-21
Trying to do the same- upload webcam pic to my webpage server.
How exactly did you get it to work? Not very linux savy. Have been searching for an app since I installed 8.10, Feb 09, No previous linux experience. DOS, whey back when? Wish it had a GUI!

---

### Post by ixnull on 2010-12-10
I'm trying to configure a webcam server using the same webcam-program as Gina, but instead of uploading the images to a server, I want to save them locally. The webcam works fine with cheese, but something is wrong with the webcam program. No image is produced to the /var/www folder. I pasted below what happens when I run the program as well as the conf file. Any ideas?

> 
test@test:~$ webcam /etc/webcam.conf &
reading config file: /etc/webcam.conf
video4linux webcam v1.5 - (c) 1998-2002 gerd knorr
grabber config:
  Size 352x288 [none]
  input spca561, norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=288, right=352
write config [ftp]:
  Local transfer /var/www/uploading.jpeg => /var/www/webcam.jpeg
libv4l2: Error reading: Invalid argument
v4l2: Read: Invalid argument
capturing image failed


> 
[grab]
device = /dev/video1
text = "webcam %Y-%m-%d %H:%M:%S"
#infofile = infofile
fg_red = 255 
fg_green = 255
fg_blue = 255  
width = 352       
height = 288         
delay = 5  
wait = 0    
input = spca561
#norm = pal
rotate = 0
top = 0
left = 0
bottom = -1
right = -1
quality = 75
trigger = 0
once = 0

[ftp]
host = localhost       
user = webcam
pass = xxxxxx 
dir  = /var/www
file = webcam.jpeg
tmp  = uploading.jpeg
passive = 1
debug = 0   
auto = 0       
local = 1  
ssh = 0 


---

