---
title: "Need higher screen resolution."
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by UnsteadyBeat on 2008-01-22
I need a higher screen resolution, but mine only goes to 1280 by 800. I've read some other thread about this same problem, but I couldn't figure out what I'm supposed to do. Can anyone help? Thanks. 


](*,) ](*,) ](*,)

---

### Post by DaveFP on 2008-01-22
What is the maximum resolution that your monitor supports? It might be the case that it can't go any higher than you have it. If it will support a higher resolution, you should check to make sure that Ubuntu is correctly identifying the make/model of your monitor.

---

### Post by UnsteadyBeat on 2008-01-22
Well, I recently reinstalled Windows XP on my laptop and before I had a very high screen resolution, higher than what's on it now, but now I don't have it. Also, I'm not on my laptop, I'm on a different computer.

---

### Post by Cybergod on 2008-01-22
Are you referring to the resolution on the other computer and not your laptop?

---

### Post by UnsteadyBeat on 2008-01-22
I need a higher resolution for my laptop. That's where I reinstalled Windows XP and now I don't have the high resolution.

---

### Post by Cybergod on 2008-01-22
If you are using Windows XP, you need to go to the manufacturers website and download the latest video driver for your specific laptop.

---

### Post by UnsteadyBeat on 2008-01-22
Well, I have downloaded a video driver, but it didn't give me the resolution that I had before.

---

### Post by Cybergod on 2008-01-22
What is the make and model of your laptop?  And what is its screen size?

---

### Post by UnsteadyBeat on 2008-01-22
I have a Dell Inspiron 6000 and I don't know what my screen size is. All I know is that it's resolution is 1280x800 and I need a higher one.....

---

### Post by Cybergod on 2008-01-22
WXGA (1280 x 800 pixels), WSXGA+ (1680 x 1050 pixels) or WUXGA (1920 x 1200 pixels)

Which does your laptop have?  Did you go into display properties to see if you can change your resolution?  What video card does it have?

---

### Post by UnsteadyBeat on 2008-01-22
WXGA (1280 x 800 pixels) I'm guessing. 

Yes, I have tried. 1280x 800 is the highest it goes.

I have ATI MOBILITY RADEON x300

---

### Post by fatherdaly on 2008-01-22
thats ironic my laptop's maximum resolution is 1080x800

but I can't change it to 1080x800 in ubuntu :(

---

### Post by Cybergod on 2008-01-22
> **UnsteadyBeat said:**
> WXGA (1280 x 800 pixels) I'm guessing. 

Yes, I have tried. 1280x 800 is the highest it goes.

I have ATI MOBILITY RADEON x300

What is the specific model number of your laptop?

---

### Post by Cybergod on 2008-01-22
> **fatherdaly said:**
> thats ironic my laptop's maximum resolution is 1080x800

but I can't change it to 1080x800 in ubuntu :(

Did you add that resolution to your xorg.conf file?

---

### Post by fatherdaly on 2008-01-22
Sounds like a good idea, could you explain how to do that?

I'm still getting used to using linux

---

### Post by Cybergod on 2008-01-22
> **fatherdaly said:**
> Sounds like a good idea, could you explain how to do that?

I'm still getting used to using linux

You will want to open a terminal:  Applications > Accessories > Terminal

In the terminal type:  
```
sudo cp /etc/X11/xorg.conf xorg.conf.bak
```
* This will make a backup copy of your xorg.conf file

Now type:
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down the file until you see   **Section "Screen"**

You will then see **SubSection** then **Modes**

You will see something like **800X600**, you can add a resolution here.

This may not always work, it depends on whether or not your video card supports the resolution.

---

### Post by Cybergod on 2008-01-22
I forgot to add that once you do this,  you will have to restart Xserver by doing key combination "<CTRL><ALT><BACKSPACE>".  Log back in and then go to "System" > "Preferences" > "Screen Resolution".  Select your new Resolution :)

---

### Post by fatherdaly on 2008-01-22
Thanks.

Yea I'm sure that my graphics card supports 1080x800 because thats what I used in windows.


```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

```

What exactly do I do here, and how can I use the resolution once I have edited this?

---

### Post by Cybergod on 2008-01-22
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800" "1280x960" "1152x864" "1024x768" "832x624" "800x600"
	EndSubSection
EndSection

```

I've never seen a resolution of 1080x800.  Once you've added what you want then save the file and restart X as I stated in my previous post.

---

### Post by fatherdaly on 2008-01-22
My bad I meant 1280x800.

Thanks for all the help man. :D

---

### Post by Cybergod on 2008-01-22
> **fatherdaly said:**
> My bad I meant 1280x800.

Thanks for all the help man. :D

That's okay, we all have a brain fart every now and then :)

Let me know if this worked for you.

---

### Post by amdalex on 2008-01-22
I don't think your laptop supports a higher resolution.

---

