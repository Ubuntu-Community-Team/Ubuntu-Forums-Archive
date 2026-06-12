---
title: "Windows Stop Updating After Too Many Are Open"
date: 2008-06-03
forum: Desktop Environments
---

### Post by ephro on 2008-06-03
I'm using Hardy, compiz turned on with a nVidia Quadro NVS 290, dual 1920x1200 in TwinView with 6 virtual desktops. Everything runs smoothly until I have approximately 20 to 30 windows open. At that point any new window that I open stops updating. For instance I can open gEdit and start typing and nothing appears, but then if I resize the window it will show the text, continuing to type shows nothing until I resize the window again.

I have myself half convinced it's related the onboard memory of the video card, where it just can't store any more windows. If this is the case is there a way to allocate system memory for compiz to use, or is there any other solution that anyone has?

I should note that the titlebar of new windows still updates and displays correctly, it's only the contents of the window that is the problem.


ephro

---

### Post by ephro on 2008-06-04
So I have narrowed this down to happening when there are 24 windows open. Attached is a screenshot of the problem occurring.

Nobody else has this problem?

---

### Post by Ric123 on 2009-04-29
I have this exact problem too! 
I'm using Ubuntu 9.04 with Compiz from the repositories. It only happens when you have too many windows open. I can still interact with windows (press buttons, type text) and the titlebar does update, the content inside the window just doesn't update, making it look static. I think it has to do with the fact that the screen resolution is large. I have a 1920x1200 monitor. If I turn off Compiz and use Metacity, the problem goes away. Also, if I resize the misbehaving window smaller (maybe down to around 800x600) the problem goes away. And the more windows I have open, the smaller it seems I need to resize them for them to start working again. The system can hang if I make a window fullscreen, but maximizing will not crash anything. All the Compiz effects and the window manager itself still work (ex. I can rotate my desktop cube and the window animations still work). It definitely seems like a redraw problem because of how the windows will be "imprinted" with whatever they are restored onto. 

I did find a link to several suggested solutions to this problem, but so far none have been effective for me, but it does say that some work for certain people: 
[http://blog.xupeng.me/2009/04/07/window-doesnt-redraw-correctly-when-using-compiz/](http://blog.xupeng.me/2009/04/07/window-doesnt-redraw-correctly-when-using-compiz/)

I have a Dell Inspiron 1720, 2 GB RAM, 128 MB NVIDIA GeForce 8400 using the latest Restricted Hardware Driver (version 180)

I hope this gets fixed soon, it's definitely a big blot for an operating system...:(
Please ask me if you need more info!

---

### Post by lisati on 2009-04-29
I don't mean to sound rude or ignorant but...... *(immediate opportunity for appearing that way)....* do you really **need** that many windows open? The "KISS" principle ("Keep it simple, Silly!") suggest to me that having less windows open might be of some value here.

---

### Post by Ric123 on 2009-04-30
I understand and too a certain degree I agree with you, but it's probably not in the best interest of the user. (And somewhat laughable) In my experience, I tend to have many background application windows on another workspace which causes windows on the current workspace to stop working.

I ran a quick test and found that I can only open 9 OpenOffice Writer windows before this bugs comes up! And I can open 9 Word docs in Windows Vista no problem!

Here's a real world example:
Workspace 1: 2 Firefox windows, 1 OpenOffice Writer window, 1 File Browser window, 1 Terminal
Workspace 2: 2 Pidgin(IM), 1 Miro (Downloading), 1 Amarok(Music)

And now I can't maximize any window or make anything "too big"

Like ephro I've convinced myself that it's probably because I don't have that much graphics memory. If that's the case, then Compiz should probably try to clean up after itself like releasing window memory when a window is minimized or on another workspace, although this is not my field of expertise. I'm interested on how Windows Vista handles this. (Maybe using RAM?)

24 windows is probably not going to happen that often, but 9 isn't good.
I'll try pinning the problem down more precisely to see what exactly is causing it, maybe I just have a bad combo: not enough video memory for my screen size

---

### Post by toughy1983 on 2009-09-16
Hi there, 

i got the same Problem here and I'm a web developer and i really need a solution for that, cause i'm loving using ubuntu for my developing work, but as soon as my work gets a lil too complex (gimp, netbeans, virtualbox, firefox, several documentation PDFs etc.) the windows doesn't get refreshed anymore like it was already described by the previous speakers. 

I would really appreciate some (constructive) replies!

THX!

---

### Post by bigboy_pdb on 2009-09-16
I tried opening a lot of windows (more than 30) and my typing got slightly slower.

As you open more and more windows, it makes sense that your system might slow down because there'd be less resources available (especially if you're performing tasks that are resource intensive).

There's a number of reasons that might happen. Your video card might not be well supported or you might not have enough RAM (or there could be other hardware incompatibilities).

You could try disabling compiz. To do this open the "Appearance Preferences" window (System -> Preferences -> Appearance). Select the "Visual Effects" tab and select "None".

If you have another video card, you can try swapping them, or if you have additional RAM then you can try adding it (but it would be a good idea to check that they're compliant with your motherboard design before you try putting them in).

---

### Post by toughy1983 on 2009-09-16
Unfortunately it is not about getting a slow response or similar. The windows' content just doesn't get updated, if I exceed a specific window size. And that starts when I have several windows open. I got an Core 2 Duo 2.4 GHz and about 6GB Ram. My Video Card is a Nvidia Quadro NVS 285 128MB x16 and i have 2 monitors (1600x1200) connected. I'm running them in TwinView mode.

I think the reason could be, as my previous speakers pointed out, the low video memory. Tomorow I'll try allocating shared memory to the PCI Express Bus via the BIOS, maybe that will help.

Thx for the fast reply anyway!

---

### Post by toughy1983 on 2009-09-18
Hmmm,

i looked into the BIOS configuration, but i couldn't find an option to allocate more memory for the PCI Express Bus from the normal RAM, "Shared memory" like.

Could there be an option in Ubuntu, where you can do that by Software configuration? Maybe in the Nvidia driver configuration... i didn't find one, yet.

Greetz

---

### Post by toughy1983 on 2009-11-25
Has someone another idea? 

I still have this Problem... It's about the less memory of my video card, but that shouldn't prevent Ubuntu to update the windows, if there are many open. 

It only happens with compiz on...

Thanks!

---

### Post by lifesizejesus on 2009-12-09
I've had a problem very similar to this one for a long time, at least since hardy (8.04). I'm currently at Karmic. My video card is nvidia geforce 7950GT with 512Mb memory. I have seen the problem with many different nvidia driver versions, currently "version 190" according to hardware drivers manager.

For me the problem seems to get worse over time. After clean boot I can open A LOT of full screen windows without problems, but the longer I have been using the computer the less windows are needed to trigger the problem.

Even before windows stop updating completely, any new windows using OpenGL become VERY slow. I have to close other windows to get 3D modeller (Ac3d) or 3D games running again.

This could be caused by running out of video memory. If that is the case, then it is likely that something (compiz?) is leaking video memory. Then again, if that is the cause then this should be a lot more common problem..

---

### Post by akashiraffee on 2009-12-09
> **toughy1983 said:**
> 

It only happens with compiz on...



Well, sadly, then, it is probably compiz  -- not surprising, since compiz is the "window manager".

I don't have to time to come up with 24 windows to open right now (I run 6 workspaces with only a few windows in each), but I'll be sure to test this later.

I have a friend who works like you.  His taskbar looks like someone just dropped a deck of cards.  

Keep in mind more windows will slow the system down (any system), even if they all still "work".  It seems strange to me you would want 9 seperate open office windows open...doesn't open office support tabs?  

Tabs use fewer resources than windows.  I get the feeling you and my friend are just using the taskbar like a normal person would tabs, which is not very efficient.  

Also, you must be leaving some (significant) number of those windows open, untouched, for a long time.   Like, how many of the 24 windows do you see in 15 minutes?  That's the real number of windows you should have open.  

In other words, you are kind of "getting what you deserve".  It is unlikely developers would prioritize supporting irresponsible silliness ;)  Maybe if you had a nicer wallpaper image, this would be less of a temptation...

---

