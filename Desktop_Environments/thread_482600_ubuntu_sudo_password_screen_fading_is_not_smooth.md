---
title: "ubuntu sudo password screen fading is not smooth"
date: 2007-06-23
forum: Desktop Environments
---

### Post by ajpug on 2007-06-23
Hi all,

I have just switched from Windows Vista to Ubuntu Feisty and I have to say that I really love it.
Everything worked fine and even installing Beryl was very easy.
I have however some odd problems. When I do some action that requires me to insert my password (sudo), the background screen fades to black but not smoothly, rather it is blocky and in discrete steps.
Similarly, when the popup blocker in Firefox appears and disappears (the notification bar on top), it does so not smoothly but in steps.
Any idea what this might be related to?

I am using an ATI radeon X700 pro with whatever drivers were installed by default. Screen resolution is 1280x1024 @ 60Hz with 24 bit color depth.

Any help is very much appreciated.

Thank you,
ajpug

---

### Post by raul_ on 2007-06-23
Maybe you have to tweak some settings in xorg.conf

let's go extreme here, but first, let's backup what you have:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

now since we both have ATI cards, I'll give you the options I added and you add them too:

```
sudo gedit /etc/X11/xorg.conf
```

now in section "Device" add these lines before "SectionEnd"

 Option "RenderAccel" "true"
	Option	"AddARGBGLXVisuals" "True"

in section "Screen" before "EndSection"

	Option "AddARGBGLXVisuals" "True"

Obviously, one of them is repeated, but I don't know which one so let's keep it that way :)

try changing your default depth to 16, it did no harm here.

Now restart X with ctrl+alt+backspace

worst case scenario you'll end up in a terminal , where you can do 

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

and then 

startx

and you keep your original settings

---

### Post by klato on 2007-06-23
I've had this behavior since Dapper...and back then I was using an ATI Mobility Radeon 7500.  Was the same on Edgy with the same card.  However, now I'm on Feisty with an nVidia Geforce Go 7300 and I STILL get that behavior...

---

### Post by raul_ on 2007-06-23
Yeah but ATI sucks!! I can't even play Secret Mario Chronicles :(

---

### Post by airtonix on 2007-06-23
klato: So considering the drivers are the issue, when do you see a resolution occuring for better drivers? aka : blame ati/amd

---

### Post by klato on 2007-06-24
Hehe, I'm not sure where the problem is...but I've had the problem with both ati and nvidia, so who knows if it's anyone's driver at all

---

### Post by ajpug on 2007-06-27
I am trying the suggested method but it does not seem to solve the problem.
One thing I have noticed is that in xorg.conf my video card was detected as PCIE instead of AGP. Can this cause problems?

Also, I have noticed that under the Add/Remove programs, there is an ATI driver which , according to the description, should enable 3D acceleration. Has anyone experience with this driver?

Thanks a lot,
ajpug

P.S. One more thing. Don't you think it is odd that I have the problem mentioned in this thread but then Beryl etc. works just fine?

---

### Post by ajpug on 2007-06-29
I think I found the problem. It seems that I experience such problem only wen using Beryl. If I do not use Beryl everything works fine. I guess it has to do with some odd setting/effect in Beryl that gets picked up.

ajpug

---

