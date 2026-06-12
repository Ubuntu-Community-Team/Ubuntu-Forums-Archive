---
title: "Dell XPS M1530 acting weird"
date: 2009-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pappfer on 2009-08-27
I'm facing an interesting problem.
I have a Dell XPS M1530 with 64-bit Ubuntu Jaunty on it.

After the notebook is on for a couple of hours it get's acting weird. I mean it clicks the mouse button or the mouse gets moving or it pastes the text from clipboard, closes the open tabs in Firefox or opens a bookmark folder and such other weird things.

The area next to the touchpad is pretty hot after the notebook is on for a couple hours. That area has metal housing and some of my friends said that maybe this is the way Dell tries to take the heat away from the notebook. I don't know if it's a "bug or a feature" but it's just hot. I'm using sensors in my Ubuntu to check the temperature but it always shows good values.

My old Acer notebook did weird things too in the past but not as many times and not as frustrating things that I experience now. I could turn off the touchpad in that notebook with a keyboard combination and that solved the problem. In my XPS I can't turn it off so I downloaded gsynaptics and turned the touchpad off when the notebook was acting weird. That seemed to solve the problem. But the thing is still very frustrating, it comes up almost every day.

What can I do about it? Is it normal that the area next to touchpad is hot? My notebook is on for a couple of hours now and the sensors show the following values:
CPU temperature: 53 C
HDD: 51 C
Video card: 67 C

---

### Post by Gausian on 2009-08-27
Your temps look fine.  Where exactly is it getting hot?  Under the touchpad, to the left or right?

For your info, if you havent taken your laptop apart, under your touchpad is your netowrk card.  to the left is the HDD.

---

### Post by pappfer on 2009-08-27
> **Gausian said:**
> Your temps look fine.  Where exactly is it getting hot?  Under the touchpad, to the left or right?

For your info, if you havent taken your laptop apart, under your touchpad is your netowrk card.  to the left is the HDD.
It's getting hot everywhere below the keyboard. It's a bit warmer to the left of the touchpad where the HDD is.

---

### Post by Gausian on 2009-08-28
well i cant see those temps making your computer bug out, so im not sure of the cause of your acting up problems.

as for your heat worries, the only advice that i can give you is to keep your fans clean and have your laptop on hard surfaces.  on pillows or beds etc the vents dont get enough air flow.  laptops get warm no matter what when on so you may just have to get used to it.

---

### Post by nwadams on 2009-08-28
the hdd is a bit hot according to your sensors. And your video card might be a tad warm too. May I ask what video chip you have. But your cpu is well within reasonable range. I have a dell xps m1330 so under the hood they are very similar. (except for the obvious size difference)

---

### Post by pappfer on 2009-08-30
> **Gausian said:**
> as for your heat worries, the only advice that i can give you is to keep your fans clean and have your laptop on hard surfaces.  on pillows or beds etc the vents dont get enough air flow.  laptops get warm no matter what when on so you may just have to get used to it.
How to keep my fans clean? I need to disassemble it, don't I?
I always keep my notebook on hard surfaces.
I know that laptops get warm but honestly it's getting hot. Really hot! I could get used to it but when you see your laptop doing things by itself then you think it's just not normal..

> **nwadams said:**
> the hdd is a bit hot according to your sensors. And your video card might be a tad warm too. May I ask what video chip you have. But your cpu is well within reasonable range. I have a dell xps m1330 so under the hood they are very similar. (except for the obvious size difference)
I have an nVidia GeForce 8600M GT video card with 256MB dedicated RAM.

---

### Post by spongypants23 on 2009-08-31
> **pappfer said:**
> How to keep my fans clean?

No. Just blow into the fan every once in a while.

---

### Post by pappfer on 2009-09-25
Would replacing my HDD be the only solution?
Would it solve it anyway, what do you think?

---

### Post by wavesailor on 2009-10-07
I seem to have a similar problem. Mine is a Dell PC  - Dimension 2400. Mine mouse normally starts to act crazy after a day or so of the PC running continuously. I thought it was the mouse at first and swapped it for another but the problem still persists. The favourite thing it likes to do is open the trash folder like twenty times and highlight areas on the desktop.

I'm not sure how to even start looking for the problem??

---

### Post by sonofzerg on 2010-02-03
I also have a problem with my Dell XPS M1530. When running Ubuntu 9.10 my laptop is burning at 80 degree C for the CPU and 74 degree C for the GPU. I've checked my fan. It works fine. Actually, it's running at full speed all the time but my temperatures don't drop. I didn't have this problem with previous version of Ubuntu. Does anyone have any ideas or have the same problem with me? Please help. Thanks.

---

### Post by omarly on 2010-02-07
> **pappfer said:**
> I'm facing an interesting problem.
I have a Dell XPS M1530 with 64-bit Ubuntu Jaunty on it.

After the notebook is on for a couple of hours it get's acting weird. I mean it clicks the mouse button or the mouse gets moving or it pastes the text from clipboard, closes the open tabs in Firefox or opens a bookmark folder and such other weird things.

The area next to the touchpad is pretty hot after the notebook is on for a couple hours. That area has metal housing and some of my friends said that maybe this is the way Dell tries to take the heat away from the notebook. I don't know if it's a "bug or a feature" but it's just hot. I'm using sensors in my Ubuntu to check the temperature but it always shows good values.

My old Acer notebook did weird things too in the past but not as many times and not as frustrating things that I experience now. I could turn off the touchpad in that notebook with a keyboard combination and that solved the problem. In my XPS I can't turn it off so I downloaded gsynaptics and turned the touchpad off when the notebook was acting weird. That seemed to solve the problem. But the thing is still very frustrating, it comes up almost every day.

What can I do about it? Is it normal that the area next to touchpad is hot? My notebook is on for a couple of hours now and the sensors show the following values:
CPU temperature: 53 C
HDD: 51 C
Video card: 67 C
I had a problem with my gpu and cpu, getting hot, read a lot of forums. then i dismanteled the fan and the colling from the cpu and gpu, and played it like "harmonica" - out came a lot of dust and ****, and now my temps are 20C below what it was. it was impossible to see the **** and the heating was triggered from secondlife, and when i complained, i was sure i had no buggy fan or anything, but i was wrong.

I have had my lap since 2 years ago and i think i have treated it nice, but the fan is like a vacuum-cleaner, and its been on most of the time :) and worked/s like a charm now.

check it out, if you are a bit handy and soft on your hand. i think you only need a small phillips screw-driver. and check out on the dell-manual in advance. not that big a deal, 8 scews or something. i didn't even have the pasta, which is recomended, but it was late at night and week-end, so i didn't have the time/patience.

it worked for me :) hope it works for u too

---

### Post by omarly on 2010-02-07
> **sonofzerg said:**
> I also have a problem with my Dell XPS M1530. When running Ubuntu 9.10 my laptop is burning at 80 degree C for the CPU and 74 degree C for the GPU. I've checked my fan. It works fine. Actually, it's running at full speed all the time but my temperatures don't drop. I didn't have this problem with previous version of Ubuntu. Does anyone have any ideas or have the same problem with me? Please help. Thanks.
as my other post says: i had exactly the same thought as you. the shift from 8.10 to 9.04 made me think of the software, but the symptom with high fan speed is exactly what happened to me. i even had a auto shut-down, and thank to the lap-god, the whole thing didn't burn

as we speak i have dual screen, cpu 49C and gpu62. this thing made me install sensors, at the panel, which is highly recomended ;)

---

### Post by omarly on 2010-02-07
[http://support.dell.com/support/edocs/systems/xpsM1530/en/SM/cpucool.htm#wp1084976](http://support.dell.com/support/edocs/systems/xpsM1530/en/SM/cpucool.htm#wp1084976)

link to dells service-manual and cooling. the m1330 has a cooling-prob, but IS NOT, related to the m1530, i found out after hours of study.

---

### Post by OldTimeTech on 2010-02-08
I also have a XPS M1530 and it gets hot (very hot on left hand side). When in facebook will quit letting me type and then highlights everything, will not close down browser without doing a hard reboot.  If you say it is facebook, I will also tell you that it will do this in my email pages and when I work on travel plans.  I too at first thought it was 9.10, then I thought it was Firefox upgrade, have downloaded software to delete Flash cookies thinking that had something to do with it.

My fan is working and I've cleaned it out frequently but the strangeness continues, I'm hoping someone figures out the problem.

---

### Post by omarly on 2010-02-09
> **OldTimeTech said:**
> I also have a XPS M1530 and it gets hot (very hot on left hand side). When in facebook will quit letting me type and then highlights everything, will not close down browser without doing a hard reboot.  If you say it is facebook, I will also tell you that it will do this in my email pages and when I work on travel plans.  I too at first thought it was 9.10, then I thought it was Firefox upgrade, have downloaded software to delete Flash cookies thinking that had something to do with it.

My fan is working and I've cleaned it out frequently but the strangeness continues, I'm hoping someone figures out the problem.
it was not my fan which was filthy, it was the grid, whichs is at the left corner of the laptop when you type. no prob with the fan, but my air did not get out! then you can try as much in as you want from the fan. i played the whole thing like a "harmonica", grill in mouth

---

