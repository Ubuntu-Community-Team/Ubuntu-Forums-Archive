---
title: "S-Video"
date: 2009-05-10
forum: General Help
---

### Post by gmoney671 on 2009-05-10
I have a Toshiba A215-S5849 and I'm trying to connect my computer to my TV so I can watch movies and ect. I haven't been able to get my S-video to work can someone pls. help?!?

---

### Post by BslBryan on 2009-05-10
Hello, gmoney671. :-)

Firstly, what kind of S-Video cable?  And is it S-Vid to S-Vid, or something else?

Also, what version of Ubuntu are you currently using, and what graphics card do you have?

Sorry for all of the questions, but I'd like to help as much as possible. :-)

---

### Post by confusedstingray on 2009-05-10
check you resolution start at 640 x 480 this should allow you to see the boot up on the tv.

---

### Post by gmoney671 on 2009-05-10
The connection is S-vid on the computer to the S-vid on the TV. I have a ATI Radeon Graphic card (I don't know how to find out which kind), AMD Truion 64x2

---

### Post by gmoney671 on 2009-05-10
And Ubuntu 9.04

---

### Post by BslBryan on 2009-05-10
Do you happen to have an Hp Pavilion DV series laptop?

---

### Post by gmoney671 on 2009-05-10
Found it ATI Radeon X1200 graphics

---

### Post by gshankar on 2009-05-10
Sorry to jump in but I too have a S-video problem.

My hardware: Intel Desktop Board D945GCLF2 with onboard video(mini-ITX form factor) w/2Gig RAM and 20GB harddrive.

Ubuntu 8.1 

The VGA looks good but the S-video appears that there is no vertical sync at all and the picture rolls rapidly.

I checked intel website but they don't seem to have any support for Linux video driver

Help please.


Thanks,
G Shankar

---

### Post by aaboelela on 2009-05-13
Hi,

check this:

[http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42](http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42)

To enable S-Video Out:
> xrandr --output S-video --set load_detection 1 
xrandr --output S-video --auto 
xrandr --output LVDS --off

Now to go back to normal:
> xrandr --output LVDS --auto 
xrandr --output S-video --off 

---

### Post by aaboelela on 2009-05-13
Also you can create that in script files (e.g. **tvon** and **tvoff**) to make it easy, as following:

1. create **tvon** script file:
> cd /usr/bin
sudo vim tvonThen insert (type **i** to goto insert mode):
> xrandr --output S-video --set load_detection 1 
 xrandr --output S-video --auto 
 xrandr --output LVDS --offThen type **Esc** to go back to command mode, then save and exit using : x or :w then :q

2. Create **tvoff** script file:
> cd /usr/bin
sudo vim tvoffThen insert (type **i** to goto insert mode):
> xrandr --output LVDS --auto 
 xrandr --output S-video --off Then type **Esc** to go back to command mode, then save and exit using : x or :w then :q

3. Make the script files exectable:

> sudo chmod 777 tv*Now connect the S-Video to your TV, then type **tvon** to enable tv/s-video output, then later type in the command line **tvoff** to go back to normal.

---

### Post by C1ph3r13 on 2010-01-02
Just want to let everyone who is reading this that i was having the exact same problem and this fixed it for me. Thanks so much I was having a heck of a time.  :)

---

### Post by C1ph3r13 on 2010-01-02
Hey, its me again. Just wondering if there is a way to make this more permanent. I tried to put the tvon script in the /etc/init.d file and ran the update-rc.d tvon defaults command in order to have the script run at boot but seems to be a no go. Ive tried the scripts so i know they work, it just wont work during boot. If anyone has any suggestions they would be much appreciated.

---

### Post by yasir.elsharif on 2010-01-10
I got this output:
yasir@yasir-laptop:~$ xrandr --output S-video --set load_detection 1 
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26

does that mean I can't have s-video at all?
I am using dell inspiron1420 with Intel video card

---

### Post by GrizzLyCRO on 2010-02-19
I get

```
grizzly@ubuntu:~$ xrandr --output S-video --set load_detection 1 
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```

---

### Post by GROwen on 2010-05-25
I've just started experience exactly the same thing as the last two posters. Any updates to these?

---

### Post by GROwen on 2010-05-30
Turns out I needed to regenerate the xorg.conf file, don't know how it was messed up but found a reference (can't remember where now) to delete the file and then reboot X. Which worked a treat.

---

### Post by spleffy on 2010-06-05
I have the same problem. Has anybody found a solution yet?

Cheers

---

### Post by spleffy on 2010-06-05
I have a radeon X800 and tried to set up the s-video out but didnt manage to do so. If I type in xrandr -q I get s-video disconnected. How do I force xrandr to detect the s-video out?

Cheers,

---

