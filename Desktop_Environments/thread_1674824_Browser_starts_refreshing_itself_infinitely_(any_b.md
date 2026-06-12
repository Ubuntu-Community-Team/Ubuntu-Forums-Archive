---
title: "Browser starts refreshing itself infinitely (any browser that is installed) &amp; home fo"
date: 2011-01-24
forum: Desktop Environments
---

### Post by leon7302 on 2011-01-24
[LEFT]Browser starts refreshing itself infinitely (any browser that is installed) & home folder automatically opens and keeps opening itself infinitely? I am using ubuntu 10.10 and run it along side with Win 7 I don’t have any deep knowledge about Linux and would like help in resolving this issues. It is very annoying and won’t stop once started. My PC is running on core 2duo E8004 processor, two HD (one 250GB & other 500GB), has 2GB ram, 512 MB ATI 4850 graphic card.:o[/LEFT]

---

### Post by leon7302 on 2011-01-25
> **leon7302 said:**
> [LEFT]Browser starts refreshing itself infinitely (any browser that is installed) & home folder automatically opens and keeps opening itself infinitely? I am using ubuntu 10.10 and run it along side with Win 7 I don’t have any deep knowledge about Linux and would like help in resolving this issues. It is very annoying and won’t stop once started. My PC is running on core 2duo E8004 processor, two HD (one 250GB & other 500GB), has 2GB ram, 512 MB ATI 4850 graphic card.:o[/LEFT]


 
I noticed that while the browser is refreshing infinitely if I press
any key on the key board it stops refreshing for some time but again it starts
also if no application (including Firefox or any other browser) is open on the
desktop then this issues causes home folder to open and keep opening in new
windows infinitely.
 
would be helpfull if any one can suggest some solution for this

---

### Post by matt_symes on 2011-01-25
Hi

> Browser starts refreshing itself infinitely (any browser that is installed) & home folder automatically opens and keeps opening itself infinitely? 

I don't think i can help with this one (i have no idea what could be causing it) but maybe a better description will help someone else diagnose the problem. Can you explain a little more in depth and provide more information ?

Your browser issue.

How often does it refresh ? Right away ? Once every second, minute ? What is your network set up ?

Your home folder issue.

Are you opening it in Nautilus. Do you have to open a your home folder  for nautilus to keep opening your home folder ? When does it happen ? As soon as you log on ? Are there any other applications running at the same time ?

Kind regards

---

### Post by leon7302 on 2011-01-27
> **matt_symes said:**
> 
  Can you explain a little more in depth and provide more information ?




How often does it refresh ? Every time I work in ubuntu

 I ran the firefox in safe mode but the issue is still happing in safe mode.
Xev output shows the below event while the browser refresh, also if any key on
the key board is pressed while the issue is happing it stops refreshing for some time but again it starts


( KeyPress event, serial 33, synthetic NO, window 0x4600001,
    root 0x10b, subw 0x0, time 441845, (240,542), root:(248,639),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0x10b, subw 0x0, time 441879, (240,542), root:(248,639),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x4600001,
    root 0x10b, subw 0x0, time 441879, (240,542), root:(248,639),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0x10b, subw 0x0, time 441913, (240,542), root:(248,639),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False  ...... it goes on for some time )

Are you opening it in Nautilus? yes
Do you have to open a your home folderfor nautilus to keep opening your home folder ? some time it opens automaticly out of blue and keeps opening this normally happens when no application is active on the desktop, other wise while the browser is refreshing and I activate the home folder or any other folder by opening it.  
 When does it happen ? As soon as you log on ? Some times yes and some times it starts after some time same  goes for the browser.
Are there any other applications running at the same time ? yes

---

### Post by Krytarik on 2011-01-27
Hi leon7302,

the output of xev was very helpful! I could reproduce the described behaviour exactly by passing the mentioned keycode "180" to the command "xsendkeycode". At my keyboard it is the special key "Home". Look if you also have that key. Maybe those very key is defect.

---

### Post by leon7302 on 2011-01-27
> **Krytarik said:**
> 
  At my keyboard it is the special key "Home". .
Yes, I too have the home key on my keyboard but I don't see any damage to the key as it works or causes any issues in windows. I also tried pressing the home but it did not went to the home page as it happens when the browser refreshes but pressing Alt+Home produces the same action as produced by the output of xev does that is open the home page in the browser.

---

### Post by Krytarik on 2011-01-27
Then check the "Keyboard model" in "System -> Preferences -> Keyboard -> Layouts".

Note: Those combination/special key also opens your home directory in nautilus, if you are not in the web browser.

---

### Post by |{urse on 2011-01-27
By browser do you mean the file browser or an internet browser

Does using a different keyboard make the refreshing stop? I had this happen once with a keyboard that had the f5 key stuck a bit.

---

### Post by leon7302 on 2011-01-29
how is that a particular combination gets stuck :D as I told the keyboard does not show any sing of defect in my windows 7. Can it be any kind of virus :confused:

---

### Post by Krytarik on 2011-01-29
> **leon7302 said:**
> how is that a particular combination gets stuck :D as I told the keyboard does not show any sing of defect in my windows 7. Can it be any kind of virus :confused:
In Linux, that is *really* unlikely! I assume it is connected via USB, try another port.

---

### Post by leon7302 on 2011-02-03
I selected a keyboard model in the System > Preferences > Keyboard > Layout as OS was unable to recognise mine and was showing Unknown in that field and it resolved the issues. It has never occurred from my last update till this one  expect for once but that was just a minor one it only opened Home folder automatic but did not kept opening infinitely. Thanks guys for all your help will let know if it again starts. Also I unchecked the option in Repeat Keys that says "Key Presses repeat when Key is held down" \\:D/

---

