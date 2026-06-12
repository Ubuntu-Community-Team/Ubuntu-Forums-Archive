---
title: "Making Ubuntu Faster"
date: 2006-09-10
forum: Desktop Environments
---

### Post by roland_mai on 2006-09-10
Hi,

I would like to disable a bunch of Ubuntu's window transitioning. You know, the little black rectangles that appear when one minimizes a window and little details like that. 

Window transitioning is kinda slow too. It takes 0.5-1 second to transition between firefox tabs, and about 0.2-0.4 seconds when transitioning between other windows (I am ballparking here).

I am running a the latest updates on a Dell D600 Centrino 1.3 Ghz, 768 RAM, with a Radeon 9000. Do you think that using the fglrx drivers would improve the performance?

Thanks,

Rolnad

---

### Post by Ramses de Norre on 2006-09-10
Fglrx would definitely help, and for the window transitions:
Set this key in gconf: /apps/metacity/general/reduced_resources
And unset this one: /apps/panel/global/enable_animations

---

### Post by flipkick on 2006-09-10
> **Ramses de Norre said:**
> Fglrx would definitely help

Don't start hasseling with that. just disable the window animation and active the reduced_resources. That's fairly all you "can" do. The so called 3D accelleration is for users with high end systems. It's not speeding up, but blowing the system with "facy" bubblewubble.

that's my opinion.

---

### Post by Ramses de Norre on 2006-09-10
I don't know about his video card in particular but my experience is that fglrx did speed up my desktop responsiveness. You can always try, it's not that hard to download xorg-driver-fglrx and change the driver in xorg.conf.

---

### Post by roland_mai on 2006-09-10
Thank you guys. You have been really helpful. 

Is there anyway of getting rid of the grid that appears when one moves the windows or resizes them.

---

