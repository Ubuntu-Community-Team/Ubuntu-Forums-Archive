---
title: "keyboard stops working in specific apps...why?"
date: 2007-04-17
forum: Desktop Environments
---

### Post by fishexe on 2007-04-17
Frequently I will be using a gnome app and it will just stop responding to the keyboard.  This has happened in nautilus, abiword, gedit and probably several others.  The only way to fix it is to quit the app and open it again...this is especially troubling with Nautilus as it forces me to quit my session and return.  Is there some keyboard setting I need to fix for this?  Should I file a bug report?  Has anyone else had similar problems?  Any help is much appreciated.  I am using edgy on amd x64.

---

### Post by jon.reeve on 2007-10-20
I'm getting this same problem.

---

### Post by compwiz18 on 2007-10-20
Same problem here in Gusty x64, very irritating.  I've noticed that although no text shows up in the box, the little animated keyboard in Pidgin's status box continues to type when I type, and stop when I stop.

oh and I've never noticed this problem before in any previous Ubuntu versions, or in Arch Linux.

---

### Post by dchenbecker on 2007-10-22
I don't know if it's the same problem but I opened a bug in Launchpad: 

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/154912](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/154912)

For me it most often happens in Thunderbird and Eclipse, and only since I upgraded to Gutsy. The weirdest part is that sometimes if I switch away and switch back to a window it gets some of the keystrokes. It seems like the even queue in X is getting jammed on a per-app basis.

Derek

---

### Post by whoosh on 2007-10-22
Yeah this is pretty frustrating.  I get this problem in Pidgin sometimes.  Funny thing is, I'll try to type and nothing will show up, but it will respond to other keyboard strokes.  I'll press ctrl+w to close the IM in pidgin and it'll close.  I have to restart it to type again.

I don't know what the actual problem is, I can never really replicate it...

---

### Post by dchenbecker on 2007-10-22
Well, it just gets more and more fun. I did some X debugging with xmon and found that the key events are being sent to the client (Thunderbird in this case). Now I have to dig into Xlib or possibly GTK to figure out where the events are getting tossed.

---

### Post by compwiz18 on 2007-10-22
Someone on the Ubuntu IRC channel helped me out and we found a solution.

edit the file ~/.scim/config

change the line /FrontEnd/X11/Dynamic = False to /FrontEnd/X11/Dynamic = True

then reboot, and you should be good to go.

---

### Post by firefeather on 2007-10-27
I'm having a similar problem but the keyboard stops working for all apps. Could it be related? (I can still do anything else)

---

### Post by dchenbecker on 2007-10-28
At least on my machine it turned out that it was SCIM. If you need SCIM for multi-language input then I think you might be screwed. If you don't need it, you can do

```
im-switch -s none
```

to disable SCIM and then logout and back in. I'm going to try to debug next week if I get time.

Derek

---

### Post by dandellion on 2007-11-04
I don't know if this is the same problem, but my keyboard is behaving badly in Blender and in Second Life (so far). 
In Blender, it responds only on numerics and insert/delete/home... part of the keyboard, and TAB key.
In second ife it doesn't get any ctrl- combination. 

I am using keyboard switcher. Default one is not U.S english.

---

### Post by fishexe on 2008-05-22
I had the problem under feisty 7.04 and 7.10 but upon upgrade it appears to be fixed.  The problem turned out to be SCIM.  I was able to fix it by exiting SCIM each time it happened and running scim -d whenever I needed Chinese input again.  It seemed not to be a problem until I pressed the Backspace key, but after that any application with more than one window would send input to the wrong place.  Like I said, it appears (so far as I can tell) to be fixed in the version of SCIM included in Hardy Heron.

---

