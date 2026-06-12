---
title: "Dell XPS 15 L501X Webcam NOT working in Ubuntu 11.04 Natty Narwhal 64-bit"
date: 2011-06-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maverick280857 on 2011-06-02
I am starting a new thread for this as it evoked no responses on the Dell XPS 15 L501x thread. 

I just noticed that my webcam isn't working on my Dell XPS 15 L501x (running Ubuntu 11.04 64-bit and GNOME3). When I start Cheese, Camorama (or Skype video test), the webcam's power light turns on, but I see no video feed. Any ideas what could be wrong? It used to work a few weeks ago..

```
 cat /proc/bus/input/devices |grep Name
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Lid Switch"
N: Name="Power Button"
N: Name="AT Translated Set 2 keyboard"
N: Name=" USB OPTICAL MOUSE"
N: Name="Video Bus"
**N: Name="Laptop_Integrated_Webcam_2HDM"**
N: Name="Dell WMI hotkeys"
N: Name="HDA Intel Mic"
N: Name="HDA Intel Headphone"
N: Name="SynPS/2 Synaptics TouchPad"

```

---

### Post by maverick280857 on 2011-06-03
Any ideas, anyone?

---

### Post by maverick280857 on 2011-06-10
Reinstalling Dell Webcam Central on the Windows 7 64-bit partition seems to have fixed the issue. I am going to wait for a few days before marking the thread as solved.

---

### Post by sahyagiri on 2011-06-17
sudo apt-get install cheese

all de best

---

### Post by cmspider on 2011-06-27
I have seen this problem intermittently. It seems that the camera sometimes just won't start. The white LED comes on, but nothing comes from the camera. The problem sometimes clears itself up if I power off the computer for a while. Sometimes booting into windows and starting the camera up in windows helps.  

I've had other problems too though - when your camera works in linux, do you ever see corrupted frames - especially at high resolution?

---

### Post by maverick280857 on 2011-07-01
No, I have not seen corrupted frames.

I reinstalled Natty, and I am still facing this problem. In one session, the camera works just fine, and in another it doesn't (until a reboot). Dell asked me if I want to get the webcam replaced.

Are you facing this problem in Windows 7 as well? I am.

EDIT: This is still **unsolved**.

---

### Post by phguisset on 2011-07-05
i have got the same problem both on natty  and win 7, must e something linked to the bios, what do you think ?
i updated the bios recently ,maybe this update of the bios was wrongm but definitely something is worng with a software update somewhere.
as it neither works on ubuntu and win 7 I would rather think of a bios problem.

i am happy to get your solution if any, and  I will share mine. I would say changing the camera is not a solution.

---

### Post by maverick280857 on 2011-07-06
Dell wants to replace my webcam now. They say the webcam and/or its interface cable may be faulty, leading to an erroneous IRQ allocation.

For the time being, I am researching solutions just like you. Will post anything useful that I come across.

---

### Post by cmspider on 2011-07-08
That sounds odd - the camera is a USB device so the IRQ allocation side of that sounds fishy to me, but there is a thread in Dell's forums 
where a number of people seem to be having similar problems.  
It does sound like there might be some common issue with the cable to the camera.

The thread is here:
[http://en.community.dell.com/support-forums/laptop/f/3518/p/19373194/19864532.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/p/19373194/19864532.aspx)

Do they want to ship you a new camera to have you change it? Or sent the computer back to them? or onsite service?

Getting to the camera actually looks fairly involved...

My problem with the camera not starting is very intermittent.  Sometimes just closing the lid (to suspend) and reopening "fixes" it for a while...

---

### Post by maverick280857 on 2011-07-10
My problem has been solved for now, after Dell decided to replace the webcam and its interface cable.

The culprit in all likelihood was the interface cable. Sometimes, the camera started to work after I closed and re-opened the lid. If the camera were bad, it wouldn't work at all. 

By the way, the interface cable is VERY flimsy. Makes me wonder how much of the 'build quality' we end up paying for these days :-P.

If your webcam works permanently in Windows and not in Linux, it is most likely a driver issue in Linux. If it works intermittently in Windows, then check the lid (close the lid, and restart Dell Webcam Central). Dell only offers support for Windows, so ask Dell to replace your webcam AND the interface cable.

---

### Post by maverick280857 on 2011-07-10
> **cmspider said:**
> 
Do they want to ship you a new camera to have you change it? Or sent the computer back to them? or onsite service?


Dell has on-site warranty. They sent an engineer, who took apart the laptop, replaced the webcam and the interface cable (which is a flimsy looking ribbon cable).

---

### Post by cmspider on 2011-07-11
Has replacing the camera solved all your issues?

There's a new post here:
[http://en.community.dell.com/support-forums/laptop/f/3518/p/19373194/19854383.aspx?PageIndex=2](http://en.community.dell.com/support-forums/laptop/f/3518/p/19373194/19854383.aspx?PageIndex=2)

where yarosps points out that if the camera doesn't start up, all you need to do is point it at some light. Sure enough, if I try to start capturing from the camera in the dark, it fails to start every time, but then just turning on some light will cause the camera to start. Does this happen with your new camera? Is the new camera the same model as the old camera?

---

### Post by Bogart on 2012-11-19
I have the same problem with the same laptop. I'm not sure if it happens on Windows, since I hardly use it, but in Linux it happens randomly.

Now finally I understood why. When it's too dark the camera won't start. But if I light something in front of the camera (like my phone's screen) then it comes up.

Thanks for that tip :)

---

### Post by wildmanne39 on 2012-11-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

