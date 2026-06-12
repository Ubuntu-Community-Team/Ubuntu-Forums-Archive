---
title: "Graphics/Monitor Help!"
date: 2006-02-27
forum: Desktop Environments
---

### Post by mattyboi88 on 2006-02-27
Hey.

I have just installed Ubuntu 5.10 on a PC I aqquired from when my dad's company upgraded there network. It's a DELL poweredge 2200 with Twin processors, both pentium II's, running at 333Mhz. It has 256MB ram and I'm not entirely sure what kind of video card it has in it, but it is embedded into the motherboard and Ubuntu say's it is an ATI Mach 64 1MB or soemthing.

The issue is: Ubuntu load's perfect up until the log-in screen, in which, I am seeing double of my screen, i.e; two cursers, two of everything, etc. The problem stays from then on untill I restart, and thus, the process begins again. It wont let me change the Screen resolution or colour depth, and I can't navigate properly because of the double of everything...

Please Help!!!!

---

### Post by xmastree on 2006-02-27
The first thing I'd do is ctrl alt + (on the nuerical k/b, right side) to try and switch video modes. If that helps, and you end up with a resolution you can use, then you need to edit xorg.conf to remove the higher resolution it's trying to use.

Failing that, change the video driver to vesa and restart x.

---

### Post by mattyboi88 on 2006-02-27
Cool, Thank's Mate! Umm, how do I edit the 'xorg' file... Can someone give me directions and what I have to edit.... Thank's in advance guy's, your help is much appreciated.

Matt.

---

### Post by xmastree on 2006-02-27
So, presumably it worked.

Open a terminal, and type this command:
```
sudo cp /etc/X11/xorg.conf /etcX11/xorgbackup.conf
```That backs up the original one, then```
sudo gedit /etc/X11/xorg.conf
```to open it in an editor.
Look for sections like this:
```
SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
```and remove any references to resolutions you don't need. I would suggest making it just "1024x768" "800x600" "640x480"
Save the file and exit, then restart X with ctrl-alt-backspace.

You should be god to go.

---

### Post by mattyboi88 on 2006-02-28
Mate, that didn't work, It's still the same.

How do I change to Vesa> Thnx.

---

### Post by xmastree on 2006-02-28
[QUOTE=mattyboi88]How do I change to Vesa[/QUOTE]Edit the same file as before, but look further up for a section something like this:```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
```Yours will be slightly different.

See where mine says "nvidia", change whatever yours says to "vesa" then save it and restart X again.

---

### Post by mattyboi88 on 2006-02-28
This is really annoying me!

My XORG.Conf file is coming up blank, completly blank in terminal...... Can someone dumb it all down for me and make it easier for to, i.e. steps, I really appreciate your help xmastree but linux is really confusing me because i cant see what I am doing with my screen, because it is blurry and all doubled etc.

And, the backup command is not working either, saying something about no file been there... please help

---

### Post by xmastree on 2006-02-28
Sounds like you're in the wrong place.
Try this: Ctrl-Alt-F1
that will put you at a comand prompt. Login as usual, then type
**sudo nano /etc/X11/xorg.conf**
to get into an editor. The capitalisation of the letters is important, so in your post above, XORG.Conf is different from xorg.conf

Edit: forgot to mention, Ctrl-Alt-F7 to get back to your graphical interface.

---

### Post by mattyboi88 on 2006-03-01
Thank's mate! I owe you one! I can finally see what I am doing... YaY!!! lol

Umm, I've got a few small issues now... hopefully you can help me out... you're probally sick of me, sorry.

1. My cd-rom drive isnt mounting .... :S
2. I have two hard disks, both seagate 8GB SSCI, it only recognises one..
3. I can't change my resolution, it's on 640x400 - it's a pain because everything is big and gets cut off.
4. Network card - how do I install that?

Thanks... Matt

---

### Post by xmastree on 2006-03-01
[QUOTE=mattyboi88]Umm, I've got a few small issues now... hopefully you can help me out... you're probally sick of me, sorry.[/quote]Not at all. Glad to help where i can.

> 1. My cd-rom drive isnt mounting .... :S
2. I have two hard disks, both seagate 8GB SSCI, it only recognises one..
Hmm... :-k no idea
My CD always worked, so I don't know what's likely to be wrong there.
It's unlikely, but there could be something wrong with your /etc/fstab

Here's the relevant line from mine:
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

> 3. I can't change my resolution, it's on 640x400 - it's a pain because everything is big and gets cut off.
That's likely to be xorg.conf again. a very common problem is that the monitor refresh rates are missing from the file.

Here's mine:
```
Section "Monitor"
	Identifier	"NEC CI CT700"
	Option		"DPMS"
	HorizSync	31.5 - 80
	VertRefresh	60 - 75
EndSection

```
Those two lines, Horizsync and vertRefresh, if they're missing it can cause that problem. You need to find out what the values should be for your monitor.

> 4. Network card - how do I install that?Again, mine work right out of the box, no installation requred.

If yours isn't recognised, I suggest you search the forums for that particular model. Chances are, the answer is here somewhere.

---

