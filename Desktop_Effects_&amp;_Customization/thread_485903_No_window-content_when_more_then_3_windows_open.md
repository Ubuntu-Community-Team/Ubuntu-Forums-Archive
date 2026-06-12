---
title: "No window-content when more then 3 windows open"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by Plaaa on 2007-06-27
Hello,
i have a problem with the Compiz Fusion manager 
When I open more than 3 windows, the content of the window does not update. 

After boot I (re-)start compiz with parameters:
compiz --sm-disable --replace --indirect-rendering

Without that options the screen stay black. 
With the options i can see the content, but it does not refresh..

I have a geforceGo 6200.

I hope someone can help me to solve it :)

br

---

### Post by martynp on 2007-06-27
Hey,

Firstly........... thanks.............this is the closest I have got to getting rid of the dreaded black windows!

However, I am getting the same problem as you. Have tried with and without emerald but still no refresh after 3  windows open.

I hope someone reads this and has a brainwave!!

---

### Post by hyperair on 2007-06-27
Why don't you try just using "compiz --replace --sm-disable"? I use that command, and I certainly don't have a black window problem (it definitely takes more than 3 windows to cause it anyway) 

Also, how much video memory does your graphic card have? Mine has 64MB. You could try disabling the Blur plugin. It definitely helps.

---

### Post by Plaaa on 2007-06-27
sorry i have a geforce 6400 , 128 mb ram

hyperair when i do it your way,  performance is decreased dramaticly. I almost disable all of the plugins, just to try it, but it don't get better... i will post a bug-report at bugzilla for that and come back to this thread...
thanks anyway :)

---

### Post by hyperair on 2007-06-27
Strange... try checking if you have direct rendering enabled? 
```
glxinfo | grep direct
```

Anyway from what I'd heard before, direct rendering supposedly had better performance compared to indirect rendering.

Also, which version of the nvidia drivers do you have installed?

---

### Post by martynp on 2007-06-27
Hey Guys,

Been having a little play tonight and found that the following gave me the best performance yet.

sudo nvidia-xconfig --composite --add-argb-glx-visuals -d 24 (run in terminal)

compiz --sm-disable --replace --indirect-rendering (run via Alt-F2)

I have managed to get a lot of the plugins running from the settings manager and can have Firefox, a video, Nautilus and a couple of terminals open before things start to slow down.

This is the best I have had compix fusion running so far as I suffered badly with the 'black windows'

I am pretty new to Ubuntu and have already forgotten the command to show my Nvidia card detail and RAM. Can someone remind me how to do that via the terminal?

Thanks

---

### Post by hyperair on 2007-06-28
[quote=martynp]Hey Guys,

Been having a little play tonight and found that the following gave me the best performance yet.

sudo nvidia-xconfig --composite --add-argb-glx-visuals -d 24 (run in terminal)

compiz --sm-disable --replace --indirect-rendering (run via Alt-F2)

I have managed to get a lot of the plugins running from the settings manager and can have Firefox, a video, Nautilus and a couple of terminals open before things start to slow down.

This is the best I have had compix fusion running so far as I suffered badly with the 'black windows'

I am pretty new to Ubuntu and have already forgotten the command to show my Nvidia card detail and RAM. Can someone remind me how to do that via the terminal?

Thanks
[/quote]

Firstly, you shouldn't attempt to hijack someone else's thread like that with something completely off-topic. The topic is "No window-content when more than 3 windows open", obviously referring to the black window bug, and here you are asking about showing nVidia card details and RAM. 

Secondly, I don't know, but if you post your own thread, someone who knows is likely to find your post and reply you.

---

### Post by martynp on 2007-06-28
Hyperair,

I was trying to help. The thread of this topic is related to the black windows bug. The poster of the original thread has helped me get rid of the black windows bug but we still have the issue of the lack of refresh when opening 2 many windows. Have a look around at the requests for help with Nvidia cards and the black/white/frozen window bug and I think you will agree that my response is totally relevant.

As for the request for help. I notice people posting their graphic card details in posts to aid people reading. I believe mine is a GeForce 6600 but I do not know the RAM size. I didn't want to NOT post the info and look dumb so I tagged onto my post a request for help.

May I burn in hellfire.

---

### Post by hyperair on 2007-06-28
Ah I'm sorry, martynp. I must have misunderstood. My deepest apologies. I didn't read your post properly, only the last part where you were asking the questions.

---

### Post by martynp on 2007-06-28
Hyperair,

No problem..... the red mist has gone now

:D:D:D:D

---

