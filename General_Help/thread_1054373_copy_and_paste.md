---
title: "copy and paste"
date: 2009-01-29
forum: General Help
---

### Post by andyubu on 2009-01-29
I recently witch to Ubuntu (intrepid) 
I use Eclipse (Europa), PHP 5.2.6 
I have this "copy & paste" nightmare in Ubuntu "the block you copy and paste can randomly appear any where in any open file in your editor". This happens not only inside Eclipse, but also in gtext (the default text editor 
coming with Ubuntu). The best expert I know tells me that he experienced this problem long time ago. Then he switched to vi/vim and didn't bother anymore about that. He advised me to do the same thing. I wish I could! As a long time user of Windows , I think I need a bit more time to completely give up the windows way of doing thing. 
Any suggestion to get around this issue! 
Thank you very much

---

### Post by khedron on 2009-01-29
Do you mean that when you paste something it may appear anywhere in the file, or that a copy of the clipboard appears in weird places in the text file you happen to be editing?

If the second case is true, remember that middle-click on the mouse (clicking the scroll wheel) does a paste of the clipboard. It may be that in scrolling through your text file you may inadvertently have pressed too hard on the scroll wheel and pasted the clipboard in as you were scrolling by.

---

### Post by khedron on 2009-01-29
If you want to disable this behaviour of pasting on middle-click, then this post seems to have the answer:
[http://ubuntuforums.org/showthread.php?p=3030645#post3030645](http://ubuntuforums.org/showthread.php?p=3030645#post3030645)

---

### Post by andyubu on 2009-02-01
The thread ([http://ubuntuforums.org/showthread.p...45#post3030645](http://ubuntuforums.org/showthread.p...45#post3030645)) suggests a change in the xorg.conf, section Input Device 
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 3" 

But in the xorg.conf, I see this 
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
It seems that the mouse configuration must be done somewhere else? 
 
Thank you very much

---

### Post by andyubu on 2009-02-01
Further resarch show a way to mess up with hal through the file 
/etc/hal/policy/preferences.fdi 
with something like this (inside the section <deviceinfo> 

   <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" string="Macintosh mouse button emulation">
        <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
        <merge key="input.x11_options.ButtonMapping" type="string">1 3</merge>   
      </match>
   </match>
  </device>

but it does not do the trick for me (even after reboot). 
What am I still missing? 

Furthermore, I don't want to disable the middle button, I still want to use it to scroll, just don't want to paste with it.

---

### Post by grantbuntu on 2009-05-20
This blog article did the trick for me:

[http://robwilkerson.org/2008/08/20/linux-make-your-scroll-wheel-double-click/]("http://robwilkerson.org/2008/08/20/linux-make-your-scroll-wheel-double-click/")

---

