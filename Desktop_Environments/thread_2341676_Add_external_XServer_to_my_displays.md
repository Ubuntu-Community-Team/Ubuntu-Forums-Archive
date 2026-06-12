---
title: "Add external XServer to my displays"
date: 2016-10-30
forum: Desktop Environments
---

### Post by SimonHGR on 2016-10-30
Hi all,

I'm using Ubuntu 16.04 "out of the box" with whatever display manager, configuration, etc. that offers.

I have an xserver running on a tablet device, and I want to add that to the screens that I can use. I'd like to be able to position the display relative to the other displays using the xrandr --output DISP --right-of DISP mechanism, but I cannot work out how to configure the infrastructure such that xrandr (and whatever else needs to know) knows about it. xrandr does not allow me to use "192.168.2.8:0" as a display name, for example.

I have a feeling I should be using xorg.conf to tell the infrastructure about this device, but a) I've utterly failed to discover any documentation that seems to address this particular issue, and b) I want to do this from a command line rather than a config file if possible, since this will be an occasional/transient configuration, not a permanent one (though perhaps that doesn't matter, if the device is offline?)

[[edit, having poked around a bit further, it seems that there no xorg.conf file in my entire system, so I guess there's some other infrastructure configuring the display[s] on Ubuntu. Perhaps someone can tell me what that is, as that might be an avenue that I can / should explore too?

OK, belay that, I discovered that the config seems to be individual files in a directory called xorg.conf.d, and I had done a find for an exact match on xorg.conf. So, I guess it does in fact use xorg...]]

Anyway, if anyone can suggest how I should do this, or even, as a starting point, how I might go about configuring the xorg infrastructure to believe that an external xserver might be available for use, I'd be most grateful.

TIA
Cheers
Simon

---

### Post by TheFu on 2016-10-31
The X/Server has to request the X/Clients to send data. That means you need to connect to the Ubuntu machine using a non-X method from the tablet to start x-clients ... **ssh -X** is normally used. It will automatically setup a tunnel and set the correct DISPLAY variable.

X/Windows has a fairly bad security model, so you can allow X/clients to "send" data to an X/Server, but the X/Server has to allow this insecure access.  Anyone on the X/Client machine can abuse this and see all traffic, however. The link below should explain more about this method and why it shouldn't be used.

Oh - and the desktops will not be integrated. Integration only works if the same video card is used and that isn't what will happen with your setup.  No copy/paste and you won't be able to drag-n-drop windows between them either.  The GPU on the tablet is used to show the desktop there.  Plus, since most tablets only have wifi access, the performance will suck relatively, when compared to a wired ethernet connection.

There is a tool called **synergy** (think that is the name) that allows different computers to integrate. Mostly it was about keyboard and mouse events. I've never used it.

And I don't think eye-candy-desktops which require 3D GPU support will work.  Keep the X/Clients simple - start by opening an xterm. If that works, then you know X on the tablet is working.  Don't expect video playback or audio or anything other than nominal "productivity" apps to work.

More background: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) which may or may not be helpful.

Anyway, hope this is helpful in some way.

---

### Post by SimonHGR on 2016-11-01
Thanks for the input. I guess I can fire up apps on that screen in the un-integrated way. I was hoping to make it part of the layouts that xrandr manages, (and use the "primary" keyboard and mouse etc...)

Pity, this feels like it should be simple enough, and would help make up for the (seeming) fact that Linux doesn't like the USB displays (I really just want to have a second display that I can carry around with me, but the USB types don't seem to refresh properly, so are useless). Regular monitors are too big, and have stands etc. so they don't fit easily in the bags you can get in an aeroplane carry-on.

Anyway, thanks, I'll keep tinkering with what you've suggested and see if I can get anywhere that way.

---

### Post by TheFu on 2016-11-01
xrandr communicates with the X/Server. Every graphics card had a separate x-server.
It isn't that Linux doesn't like USB displays. It is that the vendors who make those devices haven't made Linux drivers like they do for some other OSes.

You can have a 2nd display that you carry around with you, using normal, 40 yr old X/Windows techniques.  Plus, X/Windows doesn't work well over WAN connections. For that, you want a remote desktop that can highly, highly, compress the data being transferred.  

I use x2go - actually, I'm using x2go (it uses the NX protocol) right now from a chromebook typing into my normal desktop (private cloud-based) running a browser on it.  x2go has clients for the main 3 OSes running x86 CPUs. Don't think they support ARM or tablet OSes.  For those, you'd need to use some network security layer and a VNC-type client.  VNC is 2-3x slower than NX, but still 20x faster than X/Windows from remote locations.  VNC isn't secure, to a VPN/ssh-tunnel is really needed to make it work.

I tried traveling with just a tablet once for 3 weeks and ran into all sorts of issues. It just wasn't quite enough OS for my needs.  Switched to a Linux-running netbook and now use chromebooks with stock Linux.  8+ hrs of battery, about 2 lbs, 1080p screen, keyboard. I miss a few things - delete and F11-F12 keys, larger HDD, great keyboards, but besides that, the chromebooks with chromeOS removed, running, my Linux, have been very nice.  I don't plan to ever buy a normal laptop again - at least not an expensive one.

BTW, I have a 10inch tablet too - use it for reading. There's a nice read-it-later app for web pages and my calibre library can be loaded up onto the tablet pretty easily. My tablet is old now and doesn't hold charges as long as it used to. Next one will be 8 inch (7 is a little too small for me).  I can read stuff on the tablet in more places and much faster than on a computer.

Anyway, you have options.

---

### Post by SimonHGR on 2016-11-01
I'm rather aware that I might be missing the point of what you're trying to tell me.

For contextual clarity, I know what X/Windows is and what it has historically done. I was teaching folks to write programs using X for the GUI, and teaching them general Unix and X/Windows administration 30 years ago. So, it's possible that that experience is sufficiently out of date that it's causing me to be blinkered and fail to see what would be obvious if I didn't have preconceptions.

I'm not currently interested in a powerful remote computer with local IO, though I totally get how wonderful this can be, because I often work in situations where there is absolutely zero connectivity (nasty airlines, and sometimes just places that don't offer wifi, and won't let me connect to their local networks. Those folks usually escort me to the bathroom...) I have to carry my own compute power to these locations with me (annoying though that can surely be!).

Also, I don't really want to have two keyboards and mice if I can help it, so the traditional "DISPLAY=192.168.1.33:0 clientprogram" is, while kinda functional ish, really not what I'm wanting either. I just want a lightweight external monitor that I can slide my mouse pointer across to, and I can drag applications to (having started them in normal ways, be that command-line or menu), and that I can type into from my regular keyboard.

So, my uncertainty is that it sounds like you're suggesting ways that I can get "traditional X" to run fast, which while certainly useful and well worth pointing out on this thread (both because I might have been interested, and because other folks finding this thread later might be), it's not going to be what I'm looking for. But, it might be that you're describing something else, and I'm missing the point completely.

Did I manage to explain my doubts? I guess that's a question--are you describing tools that can do what I'm looking for, or simply alternatives that might be coerced into something similar? Can I use one X server for output of a program that takes input (key and mouse events) from a different X server? If that's what you're describing, then we're on to something.

Anyway, sorry that's a bit rambly, but I really am unclear if we're talking at cross-purposes, or I'm just missing the essence of what you're describing because of my preconceptions.

Thanks again for all your input!
Cheers,
Simon
(Oh, and I totally get that it's not Linux's fault those USB things don't have drivers :)

---

### Post by TheFu on 2016-11-01
Completely understand the confusion - on both sides.

Check out [http://symless.com/synergy/](http://symless.com/synergy/) - that's all I got. Might look on alternativeTo for other options to that if your platform isn't supported.

When you said "take it on an airplane" ... I switched from "local display" to "remote GUI display" that could also be used locally.  Figured you weren't going to bring the computer, just the tablet on a trip.  Also "tablet" is a little vague.  The OS running on it matters for any solution. 

BTW, I was writing Xt, Xm and Xlib programs about 25 yrs ago myself.  Knowing that you know that would have changed the conversation COMPLETELY.
xhost + ....

---

### Post by SimonHGR on 2016-11-02
Ah, OK, so indeed. Well, many thanks for such an energetic effort to assist. The synergy thing looks interesting in its own right, and who knows, maybe soon the internet will be so utterly pervasive, fast, reliable, and free in all locations, that I can go with the pure remote display approach. That would be very nice ;) In the meantime, I guess I'll just hope that a majority of my clients can offer me the use of a simple display that I can add to my machine (which does have spare video outputs).

Thanks again!
Cheers,
Simon

---

### Post by TheFu on 2016-11-03
Just saw this:  [http://www.ubergizmo.com/2016/11/spud-24-inch-collapsible-display/](http://www.ubergizmo.com/2016/11/spud-24-inch-collapsible-display/)
HDMI out. That should work. Kickstarter only for now.

---

